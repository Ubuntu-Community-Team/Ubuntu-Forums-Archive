---
title: "wget help"
date: 2009-05-30
forum: General Help
---

### Post by theboytony on 2009-05-30
hi

I am trying to use wget to download a file, but when it downloads it changes the filename and it seems to remove the extension the i can't use tar on the file because it doesn't know what it is, this is the command i am using

wget [http://www.jinzora.com/downloads/jz280.tar.gz](http://www.jinzora.com/downloads/jz280.tar.gz)

how do i get the file to stay as jz280.tar.gz instead of it being renamed to downloads

---

### Post by Volt9000 on 2009-05-30
Well the problem is that you can't access that file directly. Try typing it into your web browser-- you'll see you get automatically redirected to [http://en.jinzora.com/downloads](http://en.jinzora.com/downloads). That's why the file is being renamed as "downloads"-- if you open it up in a text editor you'll see it's just the HTML document to which you get redirected.

This of course means that the URL is invalid and the site is redirecting you.

Here's the direct link:
[http://voxel.dl.sourceforge.net/sourceforge/jinzora/jz280.tar.gz](http://voxel.dl.sourceforge.net/sourceforge/jinzora/jz280.tar.gz)

So now just type

```

wget http://voxel.dl.sourceforge.net/sourceforge/jinzora/jz280.tar.gz

```

---

