---
title: "Celestia 1.3.2"
date: 2005-02-04
forum: Desktop Environments
---

### Post by mirtux on 2005-02-04
Hi,
 i'm trying to install Celestia 1.3.2 on my Ubuntu (Warty) box, compiling it from scratch, but the configure process give me this error during checking:
      ```

     checking for libgnomeui-2.0 gtk+-2.0 gtkglext-1.0... Package libgnomeui-2.0 was not found in the pkg-config search path.
     Perhaps you should add the directory containing `libgnomeui-2.0.pc'
     to the PKG_CONFIG_PATH environment variable
     No package 'libgnomeui-2.0' found
     
     configure: error: Library requirements (libgnomeui-2.0 gtk+-2.0 gtkglext-1.0) 
 not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
     
     
```
   Does anybody of you has some idea on how to solve this? :?:
   
   Thanks in advance,
   MC

---

### Post by axcairns on 2005-02-04
Stupid question - have you installed libgnomeui-2.0?

---

### Post by mirtux on 2005-02-04
.... well, it was the first thing i controlled.... *unfortunately *it is!

---

### Post by kleeman on 2005-02-04
Another stupid question: Do you have the dev packages for libgnomeui installed as well (my box with Warty did not). If you are compiling anything typically you need both the library package (libgnomeui in this case) and the headers package (libgnomeui-dev here). Other things to try is to find the path to libgnomeui.so and add it to the environment variable mentioned in the error message (you need some Unix skills for this btw ;-))

---

### Post by mirtux on 2005-02-04
Ok everybody,
     i've managed to have Celestia running! Thanks. The problem has been resolved installing **lingnomeui-dev** (thanks kleeman for pointing me out this... i didn't saw it at first sight, stupid me) and then **gtkgltext** packages.
  
  Many thanks,
  MC

---

### Post by kleeman on 2005-02-04
Yeah I compiled it myself out of interest and it worked (with those packages) however it now crashes  ](*,)  when launched from the command line. I had to install some nvidia devel packages as well. Maybe the problem is there....

---

### Post by kleeman on 2005-02-04
Also I installed version 1.3.0 instead (Warty standard package) and that works fine. Hmmm

---

### Post by mirtux on 2005-02-04
I'l tell you this weekend how it goes for me ---> i'll install it probalby on Saturday..........
 Regards,
 MC

---

### Post by mirtux on 2005-02-05
[QUOTE=kleeman]Yeah I compiled it myself out of interest and it worked (with those packages) however it now crashes  ](*,)  when launched from the command line. I had to install some nvidia devel packages as well. Maybe the problem is there....[/QUOTE]
Well, i've installed it but i think i have the same problem you have.... installation went fine, but when i try to run *./celestia * it crashes.... i don't know what to do....

Regards,
MC

---

### Post by kleeman on 2005-02-05
My suggestion: Post a bug with the Celestia developers and revert to 1.3.0  :-)

---

### Post by mirtux on 2005-02-06
Thanks kleeman, i'll post something on the Celestia users forums!

MC

---

### Post by mirtux on 2005-02-07
Unfortunately no one seems to have this problem of the celestia forum, since no one has replied to me yet..... :(
 
 MC

---

### Post by mirtux on 2005-02-07
Hi,
     OK, i've got Celestia 1.3.2, using *./configure --with-gtk *instead of *./configure --with-gnome* (looking to the Celestia users forum). But i still have a problem, which i think is related to some GL configuration with my ATI drivers. I can show you what i mean with a screenshot. 
  Whenever i'm using programs that use 3D acceleration i'm experiencing glittering of the screen #-o (very annoying because it's *fast*), with Celestia as well as with tuxracer. No problem however with fgl_glxgears.
  
  Someone has an idea of what's going on?
  
  Regards,
  MC

---

### Post by kleeman on 2005-02-07
OK good one! It works for me with the gtk option as well. No problems like you describe for me (I have a nvidia card) so it must be an ati driver issue (those drivers have issues in my experience- I had a laptop with Radeon 9600M and the ati driver has always had problems particularly with tuxracer for some reason)

---

### Post by mirtux on 2005-02-08
I hate these drivers... [img]http://www.ubuntuforums.org/images/smilies/icon_twisted.gif[/img], and i'm starting hating this video card too..... ---> i'll try with the new drivers but now that i've got a little 3d acceleration i'm thinking not to involve myself in a new driver installation... they could not work....
 
 Regards,
 MC

---

### Post by mirtux on 2005-02-11
See this ----> [http://ubuntuforums.org/showthread.php?p=68016](http://ubuntuforums.org/showthread.php?p=68016)
 
 Regards,
 MC

---

### Post by mirtux on 2005-02-17
Glittering problems resolved with the new 8.10 drivers. See Scottles here [http://ubuntuforums.org/showthread.php?t=13226&page=2&pp=10](http://ubuntuforums.org/showthread.php?t=13226&page=2&pp=10)
 
 Regards,
 MC

---

### Post by mirtux on 2005-02-25
Hi,
  with the new 8.10 drivers i've tested that all the problems encountered with Celestia disappeared! Nice ATI! :razz:

Regards,
MC

---

### Post by ioliver on 2005-06-17
I built Celestia 1.3.2 from source a couple of months back. I just kept googling for the error messages I got until it built!

Everything works except for one little detail. When you start typing the name of an object, tab doesn't cycle you through the options. In fact, it doesn't seem to do anything.

Ideas?

Ian

---

