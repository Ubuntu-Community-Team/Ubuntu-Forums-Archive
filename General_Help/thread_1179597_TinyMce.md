---
title: "TinyMce"
date: 2009-06-05
forum: General Help
---

### Post by Szise on 2009-06-05
Is the first time i use Ubuntu, i'm trying to use TinyMce, i installed the software with Synaptic but can't find its location to start it, how to start it ?

---

### Post by piine on 2011-10-03
To use tinymce/tinymce2, I did this:
```

apt-get install tinymce tinymce2

```

I already had several javascript library installed, which reside in /usr/share/javascript, so I made a link to that directory (because tinymce is /usr/share/tinymce and tinymce2 is /usr/share/tinymce2)

```

sudo ln -sf /usr/share/tinymce /usr/share/javascript
sudo ln -sf /usr/share/tinymce2 /usr/share/javascript

```

once you make the links to the directories, you can access in your html code by using:
tinymce:
```

<script type="text/javascript" src="/javascript/tinymce/.../tiny_mce.js"></script>

```

tinymce2:
```

<script type="text/javascript" src="/javascript/tinymce2/.../tiny_mce.js"></script>

```

---

