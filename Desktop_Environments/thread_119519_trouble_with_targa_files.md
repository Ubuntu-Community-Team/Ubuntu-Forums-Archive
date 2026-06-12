---
title: "trouble with targa files"
date: 2006-01-19
forum: Desktop Environments
---

### Post by LordBug on 2006-01-19
I couldn't find anything in the forums about this, so I hope I didn't miss it.

I'm trying to go through my World of Warcraft screenshots.  These are TGA (targa) files.  Whenever I try to open them through the Gnome file browser, I get this message (the 'xxxxx' is a date/time stamp WoW puts in):
> 
**Cannot open**
**WoWScrnShot_xxxxx.tga**

The filename "WoWScrnShot_xxxxx.tga" indicates that this file is of type "TarGA image".  The contents of the file indicate that the file is of type "Truevision Targa image".  If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source.  To open the file, rename the file to the correct extension for "Truevision Targa image", then open the file normally.  Alternatively, use the Open With menu to choose a specific application for the file."


#1 - Renaming the files is out, and I know they're good files.  So how do I kill this message? 

So, I did try and use the "Open With" menu... and they won't load up in Image Viewer.  I get the "busy" icon, and then it just dies gracefully.  I tried using Gimp, and all of them (that I tested) open perfectly.  So, I loaded eog (Image Viewer) from a prompt and tried to open one.  What I get in the command box is:
```

setting window size: 999/816
Instantiate job with id 1.
Starting thread with id 0.
eog-image_load.c

(eog:10291): GdkPixbuf-CRITICAL **: gdk_pixbuf_loader_close: assertion `error == NULL || *error == NULL' failed

(eog:10291): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
load success: 0
Job 001: disposing ...
Job 001: disposing end

```

I continued testing to see if it was all the TGA files that do this with EOG.  It isn't.  All of the ones I captured in 800x600 load fine with Image Viewer.  Anything with a resolution higher (99.5% of them), don't.  The files all open fine on the Windows PC, so I have no idea what's going on with the Ubuntu box.

#2 - What the heck is causing EOG to bomb on targas over 800x600?

---

### Post by LordBug on 2006-01-20
Spent a bit more time on this last night, and I'm still coming up blank.  Any ideas?

---

