---
layout: posts
title: Excerpt Di Jekyll
---

Sebenarnya ada banyak cara membuat excerpt pada blog yg di buat dengan menggunakan jekyll, tapi entah kenapa akhirnya malah memilih menggunakan jQuery untuk membuat excerpt tersebut, entah di lihat dari sisi mana, ini bagus atau tidak, pastinya tidak sempurna tapi it gets the job done.

Jadi pertama-tama menggunakan tag html + liquid untuk menampilkan daftar postingan-postingan, sebagai berikut:

<pre><code class="html"> 
&lt;ul class=&quot;posts&quot;&gt;
{{ "{% for post in site.posts "" }}%}
  &lt;li&gt;
    &lt;article&gt;
    &lt;h1 class=&quot;post-title&quot;&gt;
      &lt;a href=&quot;{{ "{{ post.url " }}}}&quot;&gt;{{ "{{ post.title " }}}}&lt;/a&gt;
    &lt;/h1&gt;
    &lt;span class=&quot;post-date&quot;&gt;
      {{ "{{ post.date | date_to_string " }}}} &amp;laquo; 
      &lt;a href=&quot;{{ "{{ post.url " }}}}#disqus_thread&quot;&gt;&lt;/a&gt;
    &lt;/span&gt;
    &lt;div class=&quot;post-content&quot;&gt;
      {{ "{{ post.content " }}}}
    &lt;/div&gt;
    &lt;p class=&quot;post-meta&quot;&gt;
      &lt;a href=&quot;{{ "{{ post.url " }}}}&quot;&gt;Read More &amp;raquo; &lt;/a&gt;
    &lt;/p&gt;
    &lt;/article&gt;
    &lt;hr/&gt;
  &lt;/li&gt;  
{{ "{% endfor "" }}%}
&lt;/ul&gt;
</code></pre>


Kemudian di bagian `<head>` di isikan kode jquery berikut ini:

<pre><code class="javascript">
$(document).ready(function(){
  $('.post-content').each(function(){
    $(this).children().slice(1).css('display', 'none');
  })
});
</code></pre>

Yang intinya, melakukan looping pada elemen dengan class `.post-content` dan jika ketemu elemen tersebut, elemen anaknya yg bukan elemen urutan pertama/persis di bawahnya akan di beri atribut css `display: none;`. 

Sederhananya, script di atas hanya akan menampilkan paragraf pertama dari setiap post yg di buat, dengan kekurangan bahwa setiap kali membuat post, harus di mulai dengan sebuah paragraf, karena nanti itulah yg akan di jadikan sebagai excerpt. 

Terima Kasih, sudah berkunjung.
Have a great day!