# Highlight.js for rails 4.0

NB: Apologies to those who downloaded versions < 7.4.0.3; third times
a charm as they say. This version now DOES work. 99% sure but...

## README FIRST
This is my first gem and I am learning as I go along. I am reasonably
certain this version works, however you may want to wait a day or so
since my next job is to add some tests.

## WHAT IS THIS?

Highlight.js is an EXCELLENT javascript library by Ivan Sagalaev which
uses javascript to detect and syntax highlight ```<code></code>``` blocks in
a webpage.  Find out more over at http://highlightjs.org/.

Highlight_js-rails4 is a simple wrapper around the library to allow
you to add highlight.js support to rails4 via a gem.

## WHY?
This is a ~~minor~~ slightly more extensive update than I first
realised to chloerei/highlight_js-rails which I have forked because :

1. I've nevered forked a repository before.
2. it hadn't been updated in a year and was 3 versions behind
highlight.js.
3. I've yet to create a gem. Its about time I learned.
4. It doesn't mention compatability with rails 4.0.

## DESCRIPTION

Rails pipeline wraper for highlight.js http://highlightjs.org/

## INSTALL

In your Gemfile

```ruby
gem 'highlight_js-rails4'

# or

gem 'highlight_js-rails4', :git => 'git://github.com/os6sense/highlight_js-rails4.git'
```

Then `bundle install`

## USAGE

### 1. Edit the applications javascript file
If you want to only select a few languages you can include just
highlight and the languages you want/need.  Edit your applications
js file (or appropriate layouts .js file if you are using layouts)
e.g.  "app/assets/javascrpt/application.js" and include something
like the following but specifying the languages you want to be
highlighted:

```javascript
//= require highlight_js/highlight
//= require highlight_js/languages/ruby
//= require highlight_js/languages/python
//= require highlight_js/languages/xml

hljs.initHighlightingOnLoad();
```

#### ALTERNATIVELY:
The source for highlight.js itself also comes with a pack which enables
autodetection. I have included 2 packs from highlight.js:

  **highlight.pack.js** - this is the download pack as supplied at
                       http://highlightjs.org/download/ and includes:
                       Bash, C#, C++, CSS, Diff, HTML, XML, HTTP, Ini,
                       JSON, Java, JavaScript, PHP, Perl, Python, Ruby, SQL

  **highlight.pack.all.js** - this is the complete shebang built with the
Python build script included in the highlight.js source. It is rather
large at 111K and includes some languages which I hadn't even heard of!
See classref.txt for the complete list.

The great thing about these is that they autodetect and hence don't
require you to specify which language to include. To use either of them,
all you will need to add to the application.js file is:

```javascript
//= require highlight_js/highlight.pack
hljs.initHighlightingOnLoad();
```
OR, in the event that you want all languages:

```javascript
//= require highlight_js/highlight.pack.all
hljs.initHighlightingOnLoad();
```
### 2. Edit applications stylesheet file
highlight.js comes with several different styles which can be applied to
the highlighted code block. There is a very useful test where you can
see the effects of these at: http://highlightjs.org/static/test.html

The complete list of styles included is:

arta, ascetic, brown_paper, dark, default, docco, far, foundation, github
googlecode, idea, ir_black, magula, mono-blue, monokai, monokai_sublime
obsidian, pojoaque, railscasts, rainbow, school_book, solarized_dark
solarized_light, sunburst, tomorrow, tomorrow-night-blue, tomorrow-night-bright
tomorrow-night, tomorrow-night-eighties, vs, xcode, zenburn

In order to add a given style edit the application stylesheet file:
    app/assets/stylesheets/application.css

If you are using a different layout the name of this file will
correspond with that layout.  Add the name of css file in the style that
you want. e.g.

```css
*= require highlight_js/github
```

This will add the github style of highlighting.

## Notes on marking up
I've only briefly used highlight.js myself! With the "pack" type files
auto detection works "as advertised" and any ```<code></code>``` block should be auto
detected and syntax highlighting applied. In the event than a language
isn't autodetected, the language can be specified by providing the
language name within the class.

## LICENSE
Please see the LICENSE. highlight_js-rails4 is little more than a repack of
highlight.js hence it uses the same license.
