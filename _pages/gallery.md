---
layout: page
title: gallery
permalink: /gallery/
description: Here are some things we've done.
nav: true
nav_order: 3
display_categories: [big events, pop-ups]
horizontal: false
---

<!-- pages/gallery.md -->
<div class="gallery">
{% if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized gallery -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_gallery = site.gallery | where: "category", category %}
  {% assign sorted_gallery = categorized_gallery | sort: "importance" %}
  <!-- Generate cards for each project -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_gallery %}
      {% include gallery_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_gallery %}
      {% include gallery.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display gallery without categories -->

{% assign sorted_gallery = site.gallery | sort: "importance" %}

  <!-- Generate cards for each project -->

{% if page.horizontal %}

  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_gallery %}
      {% include gallery_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_gallery %}
      {% include gallery.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>
