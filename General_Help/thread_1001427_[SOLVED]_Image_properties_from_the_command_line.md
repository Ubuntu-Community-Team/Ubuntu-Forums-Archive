---
title: "[SOLVED] Image properties from the command line"
date: 2008-12-03
forum: General Help
---

### Post by Davorian on 2008-12-03
Hi all,

I use vim and the command line fairly heavily when writing HTML and associated CSS/scripts.  I've found that it would be really handy sometimes to be able to quickly find out the the size of an image from the command line, i.e. without having to use an image program or right-click->properties from a file manager.  Is there a utility in the Ubuntu package space (or anywhere, for that matter) that can provide a quick-and-easy readout like this?

---

### Post by kaibob on 2008-12-03
The identify utility from the Imagemagick suite will do what you want. For example:

```
identify rose.jpg
rose.jpg JPEG 640x480 DirectClass 87kb 0.050u 0:01
```

For more information:

[http://www.imagemagick.org/script/identify.php](http://www.imagemagick.org/script/identify.php)

---

### Post by Davorian on 2008-12-03
> **kaibob said:**
> [http://www.imagemagick.org/script/identify.php](http://www.imagemagick.org/script/identify.php)

This works like a charm, thanks!

---

### Post by iaculallad on 2008-12-04
Or you could use the file command:

```
file picture_filename.jpg
```

This applies to any file you want to view it's properties.

---

### Post by Davorian on 2008-12-04
> **iaculallad said:**
> Or you could use the file command:

```
file picture_filename.jpg
```

This applies to any file you want to view it's properties.

Ahh, also good, and doesn't require the installation of another library.  Thanks.

---

