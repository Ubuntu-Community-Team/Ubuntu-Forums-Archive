---
title: "Nestopia installation tutorial please?"
date: 2008-12-27
forum: General Help
---

### Post by Chris220 on 2008-12-27
First off, I'm not sure if this is in the right place, if not, please move it!

Anyway, since I am a complete newbie to Linux, I would really appreciate it if someone could show me, step by step, starting from scratch, how to compile Nestopia into an executable file.

Extra kudos if you can tell me how to put it on the "Applications" menu under "Games".

Thanks in advance!

---

### Post by Chris220 on 2008-12-27
Anyone? Until I find out, I'm stuck using a really slow one :(

---

### Post by Chris220 on 2008-12-27
Please!?

---

### Post by Chris220 on 2008-12-29
-bump-

...

---

### Post by Chris220 on 2008-12-30
Bump

---

### Post by cyclone5uk on 2009-01-11
I'd also like to know how to do this

---

### Post by Chris220 on 2009-01-11
It seems like no one wants to tell us -_-

---

### Post by cyclone5uk on 2009-01-12
Okay, so I was going to have a go at compiling and installing it myself using the source, but I hit a snag at the first hurdle! 

If you go to the NEStopia homepage here: [http://nestopia.sourceforge.net/](http://nestopia.sourceforge.net/) and click on downloads, it lists the various files for different OS. If you click the link for the Linux version, it takes you to a page here: [http://rbelmont.mameworld.info/?page_id=200](http://rbelmont.mameworld.info/?page_id=200) called Arbee’s WIP Emporium.

Unfortunately, if you scroll down and click to download the NEStopia 1.40 source, it links you back to the original page here: [http://nestopia.sourceforge.net/](http://nestopia.sourceforge.net/)

Essentially leaving you in an endless loop, unable to even get the NEStopia source!

Does anyone know where you can download this file?

---

### Post by Chris220 on 2009-01-12
I did get it at one point, but it was from a third party site... like download.com or whatever... I don't remember which website it was though >_<

---

### Post by rauffenburg on 2009-01-21
You have to download the Windows source code, extract it. Then download this linux overlay code, extract it and copy it onto the Windows source.

After this you can compile the source code. Open your terminal, go to the directory and type "make", or "make -j3" for dual core CPUs (will be faster then).

You need to have some development packages though. I had to install the following ones. I do not know if you need any other than these.

libasound2-dev
libgtk2.0-dev
libsdl1.2-dev

After that it did the compiling job. Yet I still had to create a /.nestopia folder in my home directory and copy the nstcontrols file into that directory. I haven't played yet, but the games seem to work at least... they start. OpenGL seems to work, too.

I hope that helps to solve your problem.

Edit: these are the links to the files

For the source: [http://ovh.dl.sourceforge.net/sourceforge/nestopia/Nestopia140src.zip](http://ovh.dl.sourceforge.net/sourceforge/nestopia/Nestopia140src.zip)
For the linux overlay: [http://rbelmont.mameworld.info/nst140_lnx_release_h.zip](http://rbelmont.mameworld.info/nst140_lnx_release_h.zip)

---

### Post by Chris220 on 2009-01-21
Thank you for your instructions! I will try them out when I get back on my Ubuntu machine.

---

### Post by cyclone5uk on 2009-03-01
> **rauffenburg said:**
> You have to download the Windows source code, extract it. Then download this linux overlay code, extract it and copy it onto the Windows source.

After this you can compile the source code. Open your terminal, go to the directory and type "make", or "make -j3" for dual core CPUs (will be faster then).

You need to have some development packages though. I had to install the following ones. I do not know if you need any other than these.

libasound2-dev
libgtk2.0-dev
libsdl1.2-dev

After that it did the compiling job. Yet I still had to create a /.nestopia folder in my home directory and copy the nstcontrols file into that directory. I haven't played yet, but the games seem to work at least... they start. OpenGL seems to work, too.

I hope that helps to solve your problem.

Edit: these are the links to the files

For the source: [http://ovh.dl.sourceforge.net/sourceforge/nestopia/Nestopia140src.zip](http://ovh.dl.sourceforge.net/sourceforge/nestopia/Nestopia140src.zip)
For the linux overlay: [http://rbelmont.mameworld.info/nst140_lnx_release_h.zip](http://rbelmont.mameworld.info/nst140_lnx_release_h.zip)

I followed the instructions but got this error:

```
james@james-desktop:~$ cd /nestopia
james@james-desktop:/nestopia$ sudo make -j3
Creating output directory objs/core
Creating output directory objs/core/api
mkdir: cannot create directory `objs/core'mkdir: cannot create directory `objs/core/api': No such file or directory
: No such file or directory
make: *** [objs/core] Error 1
make: *** Waiting for unfinished jobs....
make: *** [objs/core/api] Error 1
Creating output directory objs
james@james-desktop:/nestopia$ 
```

---

### Post by StarryKnight on 2009-04-11
I was finally able to compile nestopia, but don't know what to do next? 
Can someone please at least tell me this?

---

### Post by Smacks on 2009-06-11
After you've compiled it you need to make a new folder in your user direcory called ".nestopia". Go to this directory and copy the files "nstcontrols" and "nstdatabase.xml" into it. After that click on the file called "nst" and hopefully it will work.

Compiling worked fine for me with sudo and the packages rauffenburg posted installed.

You add Nestopia to the game menu by right clicking the menu and clicking "edit menu" or System>Preferences>Main Menu. Go to the games menu and click the "new item" button. The type should be application, the name can be whatever you want (Nestopia makes sense X) ), the command is just going to be the path to the file called nst(my path was ~/Apps/Nestopia/nst), and the comment can be whatever you want to say about it like "C++ NES Emulator" or something.
If you have an image you want to use as the icon just click big icon in the top left, click browse and go to the folder of the image you want to use, click "OK" , and choose it from the small box. There are some images in "source/win32/resource" of the Nestopia folder. (The program Nestopia uses window.ico)

Hopefully that wasn't too horribly written. Sorry if it was. :(

---

### Post by KamakazieX on 2009-12-23
Can someone compile it for the repo's (.. with the authors permission of course..)

Should be easy with make-kpkg?

---

