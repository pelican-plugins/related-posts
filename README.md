Related Posts: A Plugin for Pelican
===================================

[![Build Status](https://img.shields.io/github/workflow/status/pelican-plugins/related-posts/build)](https://github.com/pelican-plugins/related-posts/actions) [![PyPI Version](https://img.shields.io/pypi/v/pelican-related-posts)](https://pypi.org/project/pelican-related-posts/)

Related Posts is a Pelican plugin that adds a list of related posts to an article by adding a `related_posts` variable to the article’s context.


Installation
------------

This plugin can be installed via:

    python -m pip install pelican-related-posts


Usage
-----

By default, up to five related articles are listed. You can customize this value by defining `RELATED_POSTS_MAX` in your settings file:

    RELATED_POSTS_MAX = 10

You can then use the `article.related_posts` variable in your templates. For example:

    {% if article.related_posts %}
        <ul>
        {% for related_post in article.related_posts %}
            <li><a href="{{ SITEURL }}/{{ related_post.url }}">{{ related_post.title }}</a></li>
        {% endfor %}
        </ul>
    {% endif %}

Your related posts should share a common tag. You can also use `related_posts:` in your post’s meta-data. The `related_posts:` meta-data works together with your existing slugs:

    related_posts: slug1, slug2, slug3, ... slugN

`N` represents the `RELATED_POSTS_MAX` value.

Additionally, you can specify the following in your settings file:

    RELATED_POSTS_SKIP_SAME_CATEGORY = True

With this setting, `article.related_posts` will contain only related posts from categories other than the original article's.


Comparable plugins
------------------

Other plugins like `related_posts` exists and more or less cover the same features, most of the time with a twist:

* `similar-posts`: a clone of `related_posts`, but use advanced algebraic model to score post's similarity.


Contributing
------------

Contributions are welcome and much appreciated. Every little bit helps. You can contribute by improving the documentation, adding missing features, and fixing bugs. You can also help out by reviewing and commenting on [existing issues][].

To start contributing to this plugin, review the [Contributing to Pelican][] documentation, beginning with the **Contributing Code** section.

[existing issues]: https://github.com/pelican-plugins/related-posts/issues
[Contributing to Pelican]: https://docs.getpelican.com/en/latest/contribute.html
