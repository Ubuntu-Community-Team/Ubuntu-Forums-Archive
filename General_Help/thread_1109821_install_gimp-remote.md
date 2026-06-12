---
title: "install gimp-remote"
date: 2009-03-29
forum: General Help
---

### Post by GabrielWolff on 2009-03-29
I am looking for a way to install gimp-remote. Is there a .deb file, is it part of a package? Do I just have to enable something in gimp?

---

### Post by todak on 2009-03-29
This page [http://www.gimp.org/man/gimp-remote.html](http://www.gimp.org/man/gimp-remote.html) shows (tells, actually) how to implement the gimp-remote command. ;)

Apparently, the command has been deprecated. In GIMP go to **File> Open Location...** to enter a URL to a remote image.

---

### Post by GabrielWolff on 2009-03-29
> **todak said:**
> This page [http://www.gimp.org/man/gimp-remote.html](http://www.gimp.org/man/gimp-remote.html) shows (tells, actually) how to implement the gimp-remote command. ;)

Apparently, the command has been deprecated. In GIMP go to **File> Open Location...** to enter a URL to a remote image.

Depracted? Darn. 

What I am looking for is actually just a waste product of gimp-remote. I edit images in two separate programs:
gthumb and gimp
I would like to find a way to open in gimp an image I am looking at in gthumb with just one keyboard shortcut.

Any suggestions?

---

### Post by todak on 2009-03-29
You can always drag the image from gThumb straight into GIMP.

---

### Post by GabrielWolff on 2009-03-29
> **todak said:**
> You can always drag the image from gThumb straight into GIMP.

Ah... no, I can't. Should I be able to do that?
Is there a way of programming such a shortcut?
Why was gimp-remote discontinued. Can I find an old version?

---

### Post by todak on 2009-03-29
Hmmmm... Yes, you should be able to drag any image you see, whether in gThumb, a web browser or a folder into a running instance of GIMP's main editing window. I tried all three methods and it worked for me. I don't know why gimp-remote was removed other than the possibility that it might duplicate context menu functions such as right-clicking an image in gThumb and clicking **Open With...** and selecting **GIMP Image Editor**. The gimp-remote command is coded into the earlier versions and as such you would have to downgrade to the version that contained the script (I am not sure which one that would be!). See [here]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=517921") for more information. Read the #20 message. It says that since version 2.4 the **gimp** command acts the same as **gimp-remote**, if that is of help to you..

---

