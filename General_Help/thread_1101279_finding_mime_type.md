---
title: "finding mime type"
date: 2009-03-20
forum: General Help
---

### Post by rex_virtutis on 2009-03-20
I am trying to match files with thier corresponding icons for a python program I am working on.  From my research, I think the eaisest way to do this is by mime types.  however I can't find a shell or python method to give the mime type of a specified file.  Is there a way to do this easily?

---

### Post by mb_webguy on 2009-03-20
You mean something like [this]("https://help.ubuntu.com/community/PythonRecipes/MIMETypes")?

---

### Post by Anthon on 2009-03-20
[http://docs.python.org/library/mimetypes.html](http://docs.python.org/library/mimetypes.html)

One of the included batteries of Python

---

### Post by geirha on 2009-03-20
In the shell you can use file or gnomevfs-info.
```
$ file -bi ~/Examples/kubuntu-leaflet.jpg
image/jpeg

```

---

