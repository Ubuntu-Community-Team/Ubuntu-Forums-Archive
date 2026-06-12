---
title: "Thumbnails are from wrong file!"
date: 2018-09-26
forum: Desktop Environments
---

### Post by bugbear6502 on 2018-09-26
I am using LXDE under Ubuntu 16.04.5 LTS

I have a large directory of low light images (around 500). I have used an ImageMagick script to make preview images of these, cropped to an area of interest, and contrast enhanced. These previews are put in a "proc" subdirectory of the image directory

But when I use pcmanfm, gthumb or gwenview to view the proc directory, the thumbnails are made from the original file, not the processed file. I altered my script to put a "k" prefix on the processed file, so they didn't have the same name as the original to no avail.

I have tried deleting the thumbnail cache, but that makes no difference; the "wrong" thumbnails are diligently recreated.

I used "strace -f -e trace=file -o log gthumb . ". I discovered (and confirmed using Gimp) that the thumbnail file for my preview
file "proc/kIMG_1152.JPG" is ".thumbnails/normal/76bbe5f4905ddf3a8cd78c35b387c00d.png"

Here is the result of egrep "IMG_1152|76bbe5f4905ddf3a8cd78c35b387c00d" in my strace log
```
32600 lstat("/home/bugbear/scratch/pogwatch/d8/IMG_1152.JPG", {st_mode=S_IFREG|0644, st_size=835328, ...}) = 0
32600 access("/home/bugbear/scratch/pogwatch/d8/IMG_1152.JPG", R_OK) = 0
32600 access("/home/bugbear/scratch/pogwatch/d8/IMG_1152.JPG", W_OK) = 0
32600 access("/home/bugbear/scratch/pogwatch/d8/IMG_1152.JPG", X_OK) = -1 EACCES (Permission denied)
32601 lstat("/home/bugbear/scratch/pogwatch/d8/proc/kIMG_1152.JPG", {st_mode=S_IFREG|0664, st_size=89344, ...}) = 0
32601 access("/home/bugbear/scratch/pogwatch/d8/proc/kIMG_1152.JPG", R_OK) = 0
32601 access("/home/bugbear/scratch/pogwatch/d8/proc/kIMG_1152.JPG", W_OK) = 0
32601 access("/home/bugbear/scratch/pogwatch/d8/proc/kIMG_1152.JPG", X_OK) = -1 EACCES (Permission denied)
32600 open("/home/bugbear/scratch/pogwatch/d8/proc/.comments/kIMG_1152.JPG.xml", O_RDONLY) = -1 ENOENT (No such file or directory)
32593 open("/home/bugbear/.thumbnails/fail/gnome-thumbnail-factory/76bbe5f4905ddf3a8cd78c35b387c00d.png", O_RDONLY) = -1 ENOENT (No such file or directory)
32593 open("/home/bugbear/.thumbnails/normal/76bbe5f4905ddf3a8cd78c35b387c00d.png", O_RDONLY) = -1 ENOENT (No such file or directory)
32600 open("/home/bugbear/scratch/pogwatch/d8/proc/kIMG_1152.JPG", O_RDONLY) = 16
32600 lstat("/home/bugbear/scratch/pogwatch/d8/proc/kIMG_1152.JPG", {st_mode=S_IFREG|0664, st_size=89344, ...}) = 0
32600 open("/home/bugbear/scratch/pogwatch/d8/proc/kIMG_1152.JPG", O_RDONLY) = 17
32600 open("/home/bugbear/scratch/pogwatch/d8/proc/kIMG_1152.JPG", O_RDONLY) = 17
32600 open("/home/bugbear/scratch/pogwatch/d8/proc/kIMG_1152.JPG", O_RDONLY) = 17
32593 open("/home/bugbear/.thumbnails/normal/76bbe5f4905ddf3a8cd78c35b387c00d.png.6UISPZ", O_RDWR|O_CREAT|O_EXCL, 0600) = 16
32593 open("/home/bugbear/.thumbnails/normal/76bbe5f4905ddf3a8cd78c35b387c00d.png.6UISPZ", O_WRONLY|O_CREAT|O_TRUNC, 0666) = 16
32593 chmod("/home/bugbear/.thumbnails/normal/76bbe5f4905ddf3a8cd78c35b387c00d.png.6UISPZ", 0600) = 0
32593 rename("/home/bugbear/.thumbnails/normal/76bbe5f4905ddf3a8cd78c35b387c00d.png.6UISPZ", "/home/bugbear/.thumbnails/normal/76bbe5f4905ddf3a8cd78c35b387c00d.png") = 0

```
It looks like it's making the thumbnail from the correct image file, but (somehow) it isn't.

Can anyone help?

   BugBear

---

### Post by bugbear6502 on 2018-09-26
A quick test, changing my derivation script to generate TIF or PNG (instead of JPEG) makes the problem go away.

So it appears the problem is JPEG specific.

  BugBear

---

### Post by bugbear6502 on 2018-09-26
Hah. Looking inside the GThumb source, I found this interesting comment and code:
```

/* ...then use a registered thumbnail generator (the exiv2 extension tries
   * to read the embedded thumbnail) */
  if (pixbuf == NULL)
    pixbuf = gth_hook_invoke_get ("generate-thumbnail", (char *) uri, mime_type, size);
```

Since JPEG can indeed have an embedded thumbnail which is PRESERVED by ImageMagic, adding a simple
[-strip]("https://imagemagick.org/script/command-line-options.php#strip") to my script's image processing made all well again.

 BugBear

---

