# HCA Web Services CSS

The following standards are based off of [Idiomatic CSS](https://github.com/necolas/idiomatic-css)
design principles for CSS development.These guidelines strongly encourage the use of
existing, common, sensible patterns.

## Table of contents

1. [General principles](#general-principles)
2. [Whitespace](#whitespace)
3. [Comments](#comments)
4. [Format](#format)
5. [Practical example](#example)

[Acknowledgements](#acknowledgements)

[License](#license)


<a name="general-principles"></a>
## 1. General principles

> "Part of being a good steward to a successful project is realizing that
> writing code for yourself is a Bad Idea™. If thousands of people are using
> your code, then write your code for maximum clarity, not your personal
> preference of how to get clever within the spec." - Idan Gazit

* Don't try to prematurely optimize your code; keep it readable and
  understandable.
* All code in any code-base should look like a single person typed it, even
  when many people are contributing to it.
* Strictly enforce the agreed-upon style.
* If in doubt when deciding upon a style use existing, common patterns.


<a name="whitespace"></a>
## 2. Whitespace

Only one style should exist across the entire source of your code-base. Always
be consistent in your use of whitespace. Use whitespace to improve
readability.

* _Never_ mix spaces and tabs for indentation.
* Choose between soft indents (spaces) or real tabs. Stick to your choice
  without fail. (Preference: spaces)
* If using spaces, choose the number of characters used per indentation level.
  (Preference: 4 spaces)

Tip: configure your editor to "show invisibles" or to automatically remove
end-of-line whitespace.

Tip: use an [EditorConfig](http://editorconfig.org/) file (or equivalent) to
help maintain the basic whitespace conventions that have been agreed for your
code-base.


<a name="comments"></a>
## 3. Comments

Well commented code is extremely important. Take time to describe components,
how they work, their limitations, and the way they are constructed. Don't leave
others in the team guessing as to the purpose of uncommon or non-obvious
code.

Comment style should be simple and consistent within a single code base.

* Place comments on a new line above their subject.
* Keep line-length to a sensible maximum, e.g., 80 columns.
* Make liberal use of comments to break CSS code into discrete sections.
* Use "sentence case" comments and consistent text indentation.

Example:

```css
/*
 * Name: Name of file at the top
 * Author: HCA Web Services
 * Date Modified: 10-10-2014
 *
 * Description of whatever it is you need to describe. Make sure to
 * keep comments at a sensible lengeth and write like a human.
 *
 */

// Basic comments use LESS ninja comments double slash

// Section comment block
//
```


<a name="format"></a>
## 4. Format

The chosen code format must ensure that code is: easy to read; easy to clearly
comment; minimizes the chance of accidentally introducing errors; and results
in useful diffs and blames.

* Use one discrete selector per line in multi-selector rulesets.
* Include a single space before the opening brace of a ruleset.
* Include one declaration per line in a declaration block.
* Use one level of tab indentation for each declaration.
* Include a single space after the colon of a declaration.
* Use lowercase and shorthand hex values, e.g., `#aaa`.
* Use single or double quotes consistently. Preference is for double quotes,
  e.g., `content: ""`.
* Quote attribute values in selectors, e.g., `input[type="checkbox"]`.
* _Where allowed_, avoid specifying units for zero-values, e.g., `margin: 0`.
* Include a space after each comma in comma-separated property or function
  values.
* Include a semi-colon at the end of the last declaration in a declaration
  block.
* Place the closing brace of a ruleset in the same column as the first
  character of the ruleset.
* Separate each ruleset by a blank line.

```css
.selector-1,
.selector-2,
.selector-3[type="text"] {
	-webkit-box-sizing: border-box;
	-moz-box-sizing: border-box;
	box-sizing: border-box;
	display: block;
	font-family: helvetica, arial, sans-serif;
	color: #333;
	background: #fff;
	background: linear-gradient(#fff, rgba(0, 0, 0, 0.8));
}

.selector-a,
.selector-b {
	padding: 10px;
}

.single-selector { margin: 10px; }
```
### Naming convention of selector
In general, naming a selecter should be *as short as possible but
as long as necessary* to accuratly convey what the selector is doing.

*prefix-where-what*

Example: Let's say we are working on the Home Featured Items widget.

```css

// Home featured items
//
.home-featured-items {
	// Styles for main home featured items widget
}

// Home featurd items title
.home-featured-items-title {
	// Styles for a consisten title style in the home featured items
	// Notice it is not on h3
	// Targeting class names and not elements makes our code more flexible
}
```

#### Declaration order

If declarations are to be consistently ordered, it should be in accordance with
a single, simple principle.

Smaller teams may prefer to cluster related properties (e.g. positioning and
box-model) together.

*Make sure to describe position or purpose of statements where necesarry.*

```css
.selector {
    // Positioning
    position: absolute;
    z-index: 10;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;

    // Display & Box Model
    display: inline-block;
    overflow: hidden;
    box-sizing: border-box;
    width: 100px;
    height: 100px;
    padding: 10px;
    border: 10px solid #333;
    margin: 10px;

    // Other
    background: #000;
    color: #fff;
    font-family: sans-serif;
    font-size: 16px;
    text-align: right;
}
```

Larger teams may prefer the simplicity and ease-of-maintenance that comes with
alphabetical ordering.

#### Exceptions and slight deviations

Large blocks of single declarations can use a slightly different, single-line
format. In this case, a space should be included after the opening brace and
before the closing brace.

```css
.selector-1 { width: 10%; }
.selector-2 { width: 20%; }
.selector-3 { width: 30%; }
```

Long, comma-separated property values - such as collections of gradients or
shadows - can be arranged across multiple lines in an effort to improve
readability and produce more useful diffs. There are various formats that could
be used; one example is shown below.

```css
.selector {
    background-image:
        linear-gradient(#fff, #ccc),
        linear-gradient(#f3c, #4ec);
    box-shadow:
        1px 1px 1px #000,
        2px 2px 1px 1px #ccc inset;
}
```

### Preprocessors: additional format considerations

Different CSS preprocessors have different features, functionality, and syntax.
Your conventions should be extended to accommodate the particularities of any
preprocessor in use. The following guidelines are in reference to Sass.

* Limit nesting to 1 level deep.
* Reassess any nesting more than 2 levels deep.
  This prevents overly-specific CSS selectors.
* Where possible, group `@include` statements at the top of a declaration
  block, after any `@extend` statements.
* Consider prefixing custom functions with `x-` or another namespace. This
  helps to avoid any potential to confuse your function with a native CSS
  function, or to clash with functions from libraries.



Follow [LESS](http://lesscss.org/) syntax and standards.

Make sure to define variables at top of file. If a mixin has the
ability to be reused, consider adding it to the global 'helper.less' file.


```css
// Variables
@color-1
@color-2
@color-3

// Mixins
.mixin(x,x) {}


// List of stuff
//

// List of stuff
ul.list-of-stuff {
	margin: 0;
	padding: 0;
}

// Items in the list of stuff
ul.list of stuff > li {
	list-type: none;
	padding: 10px;

	// Background is the color of the background of item
	background: teal;
}

// Anchor tags inside of list of stuff
ul.list-of-stuff > li > a {
	text-decoration: none;

	// Change link color to color-1
	color: @color-1;
}


// New section
//

// Selector
.selector-1 {
	.clearfix();
	.mixin(x,x);
	// other declarations
}
```


<a name="example"></a>
## 5. Practical example

An example of various conventions.

```css
// Little calendar

@crm-little-calendar-width: 129px;

// Little calendar and multi
.crm-date-calendar,
.crm-date-calendar-multi {
	position: relative;
	max-width: @crm-little-calendar-width;
	text-align: center;
}

// Calendar with multiple sessions
.crm-date-calendar-multi {
	-webkit-box-shadow: 10px 10px 0 0 #eee;
	-moz-box-shadow:    10px 10px 0 0 #eee;
	box-shadow:         10px 10px 0 0 #eee;

	&:after {
		display: block;
		content: '';
		position: absolute;

		top: 0;
		height: 100%;
		width: 100%;
		z-index: 0;

		-webkit-box-shadow: 5px 5px 0px 0px #ccc;
		-moz-box-shadow:    5px 5px 0px 0px #ccc;
		box-shadow:         5px 5px 0px 0px #ccc;
	}
}

// Month
.crm-date-month {
	background: #7A7A7A;
	color: #ffffff;
	font-size: 28px;
	text-transform: uppercase;
	font-weight: 600;
	text-align: center;
	padding: 2px 10px;
}
```
