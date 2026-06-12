---
title: "Runescape crashes when entering OpenGL"
date: 2010-12-17
forum: Gaming &amp; Leisure
---

### Post by blazemore on 2010-12-17
Hi everyone.
I used to be able to play Runescape fine in OpenGL mode until an update by JaGex (the publisher) broke it!

Now it works fine (but slowly) in Software mode, but when I click OpenGL (Or auto setup), the Java plugin crashes.

I've tried every combination of toggling the following:

[LIST]
[*]Proprietary / Open source ATI driver
[*]Chrome Stable / Firefox 3.6
[*]Sun Java (update 22) / OpenJDK (both from repo)
[/LIST]

Can anyone help?

---

### Post by blazemore on 2010-12-17
Running using the official client from the command line gives this:
```


Mesa 7.9-devel implementation error: bad format in do_row()
Please report at bugzilla.freedesktop.org
... Repeat x a million
...
java: radeon_texture.c:700: radeon_store_teximage: Assertion `dstRowStride' failed.
Aborted

```

---

### Post by blazemore on 2011-01-05
Bump. If you've got this working please post here, don't leave us all in the dark!

---

