---
permalink: /notes/
title: "Personal Notes"
author_profile: true
---

<style>
.notes-intro {
  margin-bottom: 2rem;
  color: #555;
  line-height: 1.8;
}

.notes-grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 1.1rem;
  margin-top: 1.5rem;
}

.note-card {
  padding: 1.25rem 1.4rem;
  border: 1px solid #e6e6e6;
  border-radius: 10px;
  background: #ffffff;
  transition: transform 0.15s ease, box-shadow 0.15s ease;
}

.note-card:hover {
  transform: translateY(-2px);
  box-shadow: 0 5px 16px rgba(0, 0, 0, 0.07);
}

.note-title {
  margin: 0 0 0.4rem 0;
  font-size: 1.16rem;
  line-height: 1.45;
}

.note-title a {
  color: inherit;
  text-decoration: none;
}

.note-title a:hover {
  color: #52adc8;
}

.note-meta {
  margin-bottom: 0.65rem;
  color: #777;
  font-size: 0.86rem;
}

.note-excerpt {
  margin-bottom: 0.75rem;
  color: #555;
  line-height: 1.7;
}

.note-tag {
  display: inline-block;
  margin-right: 0.35rem;
  margin-bottom: 0.3rem;
  padding: 0.14rem 0.52rem;
  border-radius: 12px;
  background: #f1f3f5;
  color: #555;
  font-size: 0.76rem;
}
</style>

<div class="notes-intro">
这里记录我在科研、理论建模、编程、学术写作以及个人思考过程中形成的笔记。部分文章附有 PDF 文档、代码和相关资料链接。所有内容均可能持续修订。
</div>

<div class="notes-grid">
{% assign notes = site.posts | where_exp: "post", "post.categories contains 'notes'" %}
{% for post in notes %}
<div class="note-card">
  <h2 class="note-title">
    <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
  </h2>

  <div class="note-meta">
    {{ post.date | date: "%Y年%m月%d日" }}
    {% if post.last_modified_at %}
      · 更新于 {{ post.last_modified_at | date: "%Y年%m月%d日" }}
    {% endif %}
  </div>

  {% if post.excerpt %}
  <div class="note-excerpt">
    {{ post.excerpt | strip_html | truncate: 150 }}
  </div>
  {% endif %}

  {% if post.tags %}
  <div>
    {% for tag in post.tags %}
    <span class="note-tag">{{ tag }}</span>
    {% endfor %}
  </div>
  {% endif %}
</div>
{% endfor %}
</div>
