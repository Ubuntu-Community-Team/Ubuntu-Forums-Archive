---
title: "Custom Thumbnails?"
date: 2009-12-16
forum: Desktop Environments
---

### Post by Da_MerV on 2009-12-16
Is there any way to change how image thumbnails are generated? I'm not particularly fond of the default 2 px frame and shadow.

Here is an example of what I am talking about.
By default thumbnails look like this:
[IMG]http://i48.tinypic.com/r9hgfm.jpg[/IMG]
I'd like to do something like this mockup:
[IMG]http://i50.tinypic.com/263fuz5.jpg[/IMG]

Thanks,
Merv

---

### Post by Da_MerV on 2009-12-18
Ideas anyone? Or is there another place I should ask?

---

### Post by jerrrys on 2009-12-18
merv, i cant tell the difference, right down to filename

---

### Post by Da_MerV on 2009-12-21
> **jerrrys said:**
> merv, i cant tell the difference, right down to filename

The difference is in the appearance of the thumbnail. The files have not been changed.

By default they generated with a 1 px white and 1 px black outline, and a shadow cast beneath.

I would like to know if you can change this. I provided an example in which it has a larger shadow and no frame.

---

### Post by Extract_Here on 2009-12-21
You should be able to change it if you right click it and go to properties.

---

### Post by jerrrys on 2009-12-21
> **Extract_Here said:**
> You should be able to change it if you right click it and go to properties.

whats properties got to due with this?

---

### Post by Da_MerV on 2009-12-21
> **Extract_Here said:**
> You should be able to change it if you right click it and go to properties.

I do not want to change a single icon. I wish to change how each thumbnail is generated.

EDIT:
Actually, it looks like I may have found a relevant file. /usr/share/pixmaps/nautilus/thumbnail_frame.png looks like what I'm talking about. I will try modifying and post results.

---

### Post by Da_MerV on 2009-12-21
Ok, so it appears that this file does indeed map the thumbnails. However, there is not much room to work with. Is there perhaps an associated configuration file that governs how it is mapped?

---

### Post by Extract_Here on 2009-12-21
oh i miss read

---

### Post by schmolch on 2009-12-22
I dont even see any thumbnailers for images declared in gconf-editor, does anyone know where they are?

---

### Post by jerrrys on 2009-12-22
user/share/icons ?

---

### Post by schmolch on 2009-12-22
> **jerrrys said:**
> user/share/icons ?

Thats just a folder.
The actual commands that are executed to generate thumbnails are all specified under /desktop/gnome/thumbnails in gconf-editor.
For example it executes "evince-thumbnailer blablabla" to generate pdf-thumbnails.
I dont see the image-thumbnailers anywhere though, i think they should be there. They work though, i dont know what happened here.

---

### Post by hugmenot on 2010-01-08
```
/usr/share/pixmaps/nautilus/thumbnail_frame.png
```

---

### Post by Da_MerV on 2010-01-09
> **hugmenot said:**
> ```
/usr/share/pixmaps/nautilus/thumbnail_frame.png
```

This is what I have found already. What we are still trying to figure out is how (if possible) to configure how this is mapped to a thumbnail. I'm trying to achieve an effect where the shadow is larger, but there isn't much room to work with in thumbnail_frame.png. Also, some pixels seem to be mapped improperly.

---

### Post by Da_MerV on 2010-07-11
Hello All,

I know this is a somewhat old thread, but I have finally found a solution to customizing the thumbnail frame in nautilus.

Now, we have previously concluded that the image that defines the thumbnail frame is```
/usr/share/pixmaps/nautilus/thumbnail_frame.png
```
This allowed somewhat limited customization as there was not much space to work with. To fix this, I recompiled nautilus from source using [this thread]("http://ubuntuforums.org/showthread.php?t=725734") as a guide. To get more room to work with, I modified the margins found in```
libnautilus-private/nautilus-thumbnails.h
```
For example, to get an 8 pixel margin, change the above file to reflect```
#define NAUTILUS_THUMBNAIL_FRAME_LEFT 8
#define NAUTILUS_THUMBNAIL_FRAME_TOP 8
#define NAUTILUS_THUMBNAIL_FRAME_RIGHT 8
#define NAUTILUS_THUMBNAIL_FRAME_BOTTOM 8
```then recompile and install. You can then use a thumbnail_frame.png with 8 pixel borders.

I hope this helps others who stumble across this thread in the future.
-Merv

---

