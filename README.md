# Fold Change Violin Plot


## Installation

**[⬇️ Click here to install in Cauldron](http://localhost:50060/install?repo=https%3A%2F%2Fgithub.com%2Fnoatgnu%2Ffold-change-violin-plugin)** _(requires Cauldron to be running)_

> **Repository**: `https://github.com/noatgnu/fold-change-violin-plugin`

**Manual installation:**

1. Open Cauldron
2. Go to **Plugins** → **Install from Repository**
3. Paste: `https://github.com/noatgnu/fold-change-violin-plugin`
4. Click **Install**

**ID**: `fold-change-violin`  
**Version**: 1.0.0  
**Category**: visualization  
**Author**: CauldronGO Team

## Description

Generate violin plots for fold enrichment analysis across organelles

## Runtime

- **Environments**: `python`

- **Entrypoint**: `fold_change_violin_plot.py`

## Inputs

| Name | Label | Type | Required | Default | Visibility |
|------|-------|------|----------|---------|------------|
| `input_file` | Input Data File | file | Yes | - | Always visible |
| `columns_prefix` | Columns Prefix | text | No | Difference | Always visible |
| `categories` | Organelle Columns | column-selector (multiple) | Yes | - | Always visible |
| `match_value` | Match Value | text | No | + | Always visible |
| `fold_enrichment_col` | Fold Enrichment Column | text | No | Fold enrichment | Always visible |
| `organelle_col` | Organelle Column | text | No | Organelle | Always visible |
| `comparison_col` | Comparison Column | text | No | Comparison | Always visible |
| `colors` | Category Colors | color-map (keys from `categories`) | No | - | Always visible |
| `figsize` | Figure Size | text | No | 6,10 | Always visible |

### Input Details

#### Input Data File (`input_file`)

Data file containing fold enrichment values


#### Columns Prefix (`columns_prefix`)

Prefix of columns to include in analysis


#### Organelle Columns (`categories`)

Select columns representing different organelles/categories

- **Column Source**: `input_file`

#### Match Value (`match_value`)

Symbol or string to match in the data for filtering


#### Fold Enrichment Column (`fold_enrichment_col`)

Name of the column containing fold enrichment values


#### Organelle Column (`organelle_col`)

Name of the column containing organelle labels


#### Comparison Column (`comparison_col`)

Name of the column for comparison groups (optional)


#### Category Colors (`colors`)

Assign colors to each category/organelle

- **Input Type**: Color map for assigning colors to categories
- **Keys From**: `categories` (categories are derived from this input)

#### Figure Size (`figsize`)

Figure size in inches (width,height)


## Outputs

| Name | File | Type | Format | Description |
|------|------|------|--------|-------------|
| `violin_plots_pdf` | `*.pdf` | image | pdf | Violin plots for each comparison group (PDF format) |
| `violin_plots_svg` | `*.svg` | image | svg | Violin plots for each comparison group (SVG format) |

## Visualizations

This plugin generates 1 plot(s):

### Violin Plots (`violin_plots`)

- **Type**: image-grid
- **Data Source**: `violin_plots_svg`
- **Image Pattern**: `*.svg`

## Requirements

- **Python Version**: >=3.11

### Package Dependencies (Inline)

Packages are defined inline in the plugin configuration:

- `pandas>=2.0.0`
- `seaborn>=0.12.0`
- `matplotlib>=3.7.0`

> **Note**: When you create a custom environment for this plugin, these dependencies will be automatically installed.

## Example Data

This plugin includes example data for testing:

```yaml
  match_value: +
  fold_enrichment_col: Fold enrichment
  organelle_col: Organelle
  comparison_col: Comparison
  input_file: examples/fold_change/enrichment.txt
  categories_source: examples/fold_change/enrichment.txt
  categories: [C..Lysosome C..Mitochondria Endosome Golgi ER Ribosome Nuclear]
  columns_prefix: Difference
```

Load example data by clicking the **Load Example** button in the UI.

## Usage

### Via UI

1. Navigate to **visualization** → **Fold Change Violin Plot**
2. Fill in the required inputs
3. Click **Run Analysis**

### Via Plugin System

```typescript
const jobId = await pluginService.executePlugin('fold-change-violin', {
  // Add parameters here
});
```
