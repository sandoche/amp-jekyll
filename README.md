# amp-jekyll (for pages)

Jekyll plugin for creating Accelerated Mobile Page versions of pages. Supports Jekyll version 3.

A fork from: https://github.com/juusaw/amp-jekyll

In this fork the AMP is generated for pages instead of Posts!

### Usage

#### Using the gem
- Add gem `gem 'amp-jekyll', :git => 'https://github.com/sandoche/amp-jekyll-for-pages'` to your `Gemfile` and run `bundle`
- Add the gem to your `_config.yml` like this:

```yml
plugins:
  - amp-jekyll
```

#### Adding the plugin manually
- Place the Ruby files in `lib/jekyll` (`amp_generate.rb` and `amp_filter.rb`) in folder _plugins at the root of the project


#### Then perform the following
- Place the layout file (`amp.html`) to the _layouts folder
- Add `amphtml`-link to post heads (see page linking below)
(Add CSS styles to the html template)
- Generate your site with `jekyll build`

### Skipping Pages

Sometimes there are pages we don't want to be turned into AMP pages, normally this is because they require HTML elements or JavaScript that would make them invalid.

In any post we want to skip simply add;

```yml
skip_amp: true
```

And update your `amphtml` block to look like;

```
{% if page.path contains '_posts' %}
  {% unless page.skip_amp %}
    <link rel="amphtml" href="{{ page.id | prepend: '/YOURDIR' | prepend: site.baseurl | prepend: site.url }}">
  {% endunless %}
{% endif %}
```
