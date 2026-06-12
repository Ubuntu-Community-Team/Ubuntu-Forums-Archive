---
title: "Desktop cube top face not updating?"
date: 2009-01-03
forum: General Help
---

### Post by karasuman on 2009-01-03
I'm not sure what's going on here, because I had this working for a while...  I switched my theme to a different color and wanted to change the top/bottom faces of the desktop cube.  At first, they wouldn't change from the image I was using, even when I deleted the image.  I disabled all of the compiz effects and reenabled them.  Now, the first image is gone, but it's replaced with a plain black face, not the new image I tried to use.  (I've tried with different images, and even tried restoring the one that worked; no change.  I also restarted the computer; no dice.)  

I'm getting at this from system -> preferences -> advanced desktop effects settings -> desktop cube -> cube caps.  Is there another place I need to mess with the setting?

---

### Post by SonnHalter on 2009-01-04
try reinstalling. 

you could do it from the repository 

or you could open the terminal and type (oh god i hope this works cause i'm new to terminal codes)

sudo apt-get remove compiz
sudo apt-get install compiz

---

### Post by JECHO on 2009-01-04
> **karasuman said:**
> I'm not sure what's going on here, because I had this working for a while...  I switched my theme to a different color and wanted to change the top/bottom faces of the desktop cube.  At first, they wouldn't change from the image I was using, even when I deleted the image.  I disabled all of the compiz effects and reenabled them.  Now, the first image is gone, but it's replaced with a plain black face, not the new image I tried to use.  (I've tried with different images, and even tried restoring the one that worked; no change.  I also restarted the computer; no dice.)  

I'm getting at this from system -> preferences -> advanced desktop effects settings -> desktop cube -> cube caps.  Is there another place I need to mess with the setting?



I have had the same problem but fixed it, first...are you using ubuntu 8.10?

---

### Post by karasuman on 2009-01-04
Nope, I'm sticking with Hardy until I feel like dealing with whatever breaks with the upgrade.

---

### Post by JECHO on 2009-01-04
> **karasuman said:**
> Nope, I'm sticking with Hardy until I feel like dealing with whatever breaks with the upgrade.


ok, can you post a screen shot of your ccsm settings? in the area where you set the cube caps.

---

### Post by binbash on 2009-01-04
change the top/bottom face in deformation plugin.

---

### Post by karasuman on 2009-01-04
Still not sure why "Desktop Cube" isn't giving me the right images, but I turned on and configured the "Cube Caps" plug-in and got what I wanted.  I don't know how I missed that one when skimming through them before, but it was looking for the deformation plug-in that helped me find it. :)

---

