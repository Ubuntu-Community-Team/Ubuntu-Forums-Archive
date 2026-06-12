---
title: "Wallch not loading all wallpapers?"
date: 2012-02-25
forum: Desktop Environments
---

### Post by Hailfax on 2012-02-25
Hey guys,

I have close to 500 wallpapers in my wallpapers folder, and I'm very happy with the Wallch changes wallpapers, but I don't think that Wallch is loading ALL the wallpapers. It seems like it's just going through 25 or so.

Has anyone else experienced this limitation?

Thanks,

Hailfax

---

### Post by hakermania on 2012-03-03
Hello Hailfax, I am one of the developers of Wallch.
Wallch recognizes the images from their extension, and then it checks live (while changing wallpapers) whether an image is a true image or not.
So, if you add wallpapers by choosing a folder to add, then all the images with the following extensions will be added:
```
*.png *.gif *.bmp *jpg *svg *jpeg *.PNG *.GIF *.BMP *.JPG *.JPEG *SVG
```

Be sure that the images you try to add have this extension.

---

