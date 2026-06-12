---
title: "picasa photo viewer"
date: 2009-02-27
forum: General Help
---

### Post by excbuntu on 2009-02-27
i'm trying to install picasa and it's photo viewer that someone ported into linux. it's found [here]("http://rfobic.blogspot.com/2008/11/picasa-photo-viewer-linux-port-updated.html").

i installed the latest linux picasa from google.com, which installed and worked fine. then i downloaded and installed the above link's deb file (Picasa Photo Viewer (Updated to 1.0.2 Requires Picasa 3). when i attempt to open a picture via the photo viewer, nothing happens. otherwise, picasa works fine. please help.

---

### Post by yeats on 2009-02-27
Can you start the photoviewer in the command line interface?  Sometimes that will generate error messages you may not see in the GUI, especially if it's a custom program like this one.

---

### Post by starlex on 2009-03-13
Hi,
I found this post while looking for solutions for the same problem described by chrissharp123.

I tried to launch PicasaPhotoViewer from the terminal, even before I read your advice. The error is the following:

run-detectors: unable to find an interpreter for
/opt/google/picasa/3.0/wine/drive_c/Program
Files/Google/Picasa3/PicasaPhotoViewer.exe

I am not an expert, but it seems that it cannot launch the picasa-flavoured wine instance properly. This is strange, as the script (correctly?) calls the wine wrapper available in the Picasa folder.

starlex.

---

### Post by starlex on 2009-03-13
Update: I was almost ready to hit the bed, when I had a suspect. I installed WineHQ onto my system and tried again with the picasa photo viewer.
Now the program opens fine, so I think that the previous problem was due to some missing dlls in the vanilla-wine provided with Picasa. Nevertheless, now it doesn't seem to recognise the path for my pictures (it always show some sample pictures from the picasa installation folder).

When run from the terminal, the error now is:


"err:ole:apartment_getclassobject DllGetClassObject returned error 0x80040111
err:ole:create_server class {9ba05972-f6a8-11cf-a442-00a0c90a8f39} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {9ba05972-f6a8-11cf-a442-00a0c90a8f39} could be created for context 0x17" ...

---

### Post by caiacoa on 2009-06-19
Hi starlex et al,

no additional wine installation is needed! Please find a debian package of Picasa Photo Viewer at 
[http://www.caiacoa.de/wiki/index.php/Picasa_Photo_Viewer_(Linux_port)_for_Ubuntu](http://www.caiacoa.de/wiki/index.php/Picasa_Photo_Viewer_(Linux_port)_for_Ubuntu)

Cheers

-caiacoa

---

### Post by drhabber on 2010-06-10
> **caiacoa said:**
> [...]Please find a debian package of Picasa Photo Viewer at 
[http://www.caiacoa.de/wiki/index.php/Picasa_Photo_Viewer_(Linux_port)_for_Ubuntu](http://www.caiacoa.de/wiki/index.php/Picasa_Photo_Viewer_(Linux_port)_for_Ubuntu)
Cheers
-caiacoa

Is there any solution to make it start faster? It takes a while to start the viewer after clicking on image.

---

### Post by jiminikiz on 2010-12-10
For the many of us who dual boot (like myself), if Picasa is already installed in windows, you can associate image files in Ubuntu with **PicasaPhotoViewer.exe** and it will run natively (with wine installed).

Prereqs: Install wine

1. Right Click an image file (.png, .jpg, ...)
2. Open With > Other Application
3. > Use Other Command
4. Enter one of the following:

'/media/[nameOfWindowsPartion]/Program Files (x86)/Google/Picasa3/PicasaPhotoViewer.exe' (64bit Windows)
- or -
'/media/[nameOfWindowsPartion]/Program Files/Google/Picasa3/PicasaPhotoViewer.exe' (32bit Windows)

In my case, I run 64-bit windows, my partition is labeled 'Win7'

'/media/Win7/Program Files (x86)/Google/Picasa3/PicasaPhotoViewer.exe'

If you do not mount your windows partition automagically after logging into Linux/Ubuntu, you will have to mount the partition before you can view image files. 

Point in case, this solution is for those who: 
a.) dual boot, 
b.) always mount his/her partition at system start, 
c.) really love picasa-photo-viewer.

Hope this helps! And BTW, thanks @caiacoa for the linux port!

---

