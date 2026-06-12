---
title: "gnubik : &quot;Cannot get suitable visual&quot;"
date: 2009-01-05
forum: General Help
---

### Post by gaf.stephanos on 2009-01-05
Hey guys, i just installed gnubik and it says "Cannot get suitable visual". I checked the source and found that it says that when gdk_gl_config_new fails. Any idea why it may fail ?
I have Ubuntu 8.10 on an Acer Aspire 5310 laptop with Intel GMA 950.
Compiz is running and i tried disabling it.
I also tried xrubik and it gives a segmentation fault which i think is the same error but not handled.
You can look at the failing part here :[[URL="http://gnubik.sourcearchive.com/documentation/2.2-8/glarea-gtk_8c-source.html"] http://gnubik.sourcearchive.com/documentation/2.2-8/glarea-gtk_8c-source.html]("gnubik:glarea-gtk.c")[/URL]
Thanks...

EDIT: I found that i only have 3 Opengl visuals from glxinfo. No wonder it doesn't find a suitable one. How can i fix that ?

EDIT: Ok i found that after adding 'Option "GlxVisuals" "true"' to xorg.conf, i got my 36 visuals for all the glxfbconfigs but my old glxvisuals weren't mentioned in the glxfbconfigs and i lost them now. How do I get everything ? Is it some prob with my driver ?

---

### Post by tbullock on 2009-04-22
I am getting the same deal. gnubik fails to launch after install. I have done some searching and found a link that says they have a patch. What do I do with the patch? Any Ideas??? I notice this was an unanswered post since January. Terminal reads:

travis@travis-laptop:~$ gnubik

** ERROR **: Cannot get a suitable visual
aborting...
Aborted
travis@travis-laptop:~$ 


Here is a copy and paste of said patch:

*** glarea-gtk.c	2009-02-24 18:06:47.000000000 +0400
--- glarea-gtk1.c	2009-02-24 18:05:03.000000000 +0400
***************
*** 152,160 ****
  
  		 GDK_GL_DEPTH_SIZE ,1,
  
! 		 GDK_GL_ACCUM_RED_SIZE, 1,
! 		 GDK_GL_ACCUM_GREEN_SIZE, 1,
! 		 GDK_GL_ACCUM_BLUE_SIZE, 1,
  
  		 GDK_GL_ATTRIB_LIST_NONE 
    };
--- 152,160 ----
  
  		 GDK_GL_DEPTH_SIZE ,1,
  
! 		 //GDK_GL_ACCUM_RED_SIZE, 1,
! 		 //GDK_GL_ACCUM_GREEN_SIZE, 1,
! 		 //GDK_GL_ACCUM_BLUE_SIZE, 1,
  
  		 GDK_GL_ATTRIB_LIST_NONE 
    };


Total Ubuntu Newb here so help me out if you can.

---

### Post by tbullock on 2009-04-22
Bump for solution. :P

---

### Post by gaf.stephanos on 2009-04-22
LOL!! I made that patch but nevermind it.
This problem has been fixed already in the new kernel and the new intel driver. However, if you really need it working fast, 
Download gnubik source from the net,
Open the directory which has glarea-gtk.c,
Open up a terminal inside that directory,
Run "patch < /path-to-patch",
Then wherever the 'makefile' is inside the source directory, run "./configure", then "make install", then you'll find the working gnubik inside that source directory somewhere.

---

### Post by tbullock on 2009-04-23
> **gaf.stephanos said:**
> LOL!! I made that patch but nevermind it.
This problem has been fixed already in the new kernel and the new intel driver. However, if you really need it working fast, 
Download gnubik source from the net,
Open the directory which has glarea-gtk.c,
Open up a terminal inside that directory,
Run "patch < /path-to-patch",
Then wherever the 'makefile' is inside the source directory, run "./configure", then "make install", then you'll find the working gnubik inside that source directory somewhere.

Ok, you missed the newb part from my post apparently.

Here is what I am getting:

Download gnubik source from the net, **Nope**
Open the directory which has glarea-gtk.c,  **Nope**
Open up a terminal **Yep** inside that directory, **Nope**
Run "patch < /path-to-patch", **Nope** but maybe

Sorry about the lack of ability to follow directions. I don't need it in a hurry but would like to try it out.

---

### Post by gaf.stephanos on 2009-04-23
Ok here's gnubik's source : [source]("http://archive.ubuntu.com/ubuntu/pool/universe/g/gnubik/gnubik_2.2.orig.tar.gz")
Then open up a terminal in that directory like if it is on the desktop, type in the terminal "cd ~/Desktop".
Now type "gunzip path-to-source-you-downloaded"
Then "tar -xf path-to-source-you-downloaded" and you'll find that file decompressed and a directory called gnubik something there near it. 
Open up that and search inside for a file named glarea-gtk.c. 
Put the patch inside that directory and then CD your previous terminal in there and "patch < path-to-patch", now get out of that directory by "cd .." where a 'makefile' should be there. Type "./configure" in the terminal and then "make install" after configure finishes and you'll find the fixed gnubik inside a subdirectory of the directory you're in...

---

### Post by gaf.stephanos on 2009-04-24
Well, did you solve it ? Is it working now ?

---

### Post by tbullock on 2009-04-24
It works now in Jaunty but I cannot left click after I open Firefox, Epiphany, and IE. Well IE just locked everything up. I am having to tab everywhere. I don't think the tradoff was very productive.

---

