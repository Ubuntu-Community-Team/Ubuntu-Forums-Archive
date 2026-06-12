---
title: "Unable to re-enable desktop effects after using VGA out (notebook)"
date: 2009-09-06
forum: Desktop Environments
---

### Post by Daimoneze on 2009-09-06
Lenovo 3000 N100 - Intrepid

I noticed that while the using the VGA out recently Ubuntu seemed to automatically disable the desktop effects. I figured this was just a result of using both video outs simultaneously. However, after unplugging the VGA out and rebooting I am still unable to turn the desktop effects back on via Appearance Preferences. 

I can enable things in CCSM, but nothing changes. In fact, moving windows around now cause them to ghost momentarily. 

In Resolution Settings I see the VGA out is still enabled (but off) and I'm thinking that it might be related. Using the related function key doesn't make it go away.

---

### Post by earthpigg on 2009-09-06
press alt+f2 and run 'compiz --replace'... let us know if that works.

if things go crazy, or if you just want to quickly disable compiz, run 'metacity --replace'.

if compiz --replace works, then we just need to make that run automatically when your computer starts.

---

### Post by Daimoneze on 2009-09-06
No go. Here is the output from the terminal trying to run 'compiz --replace'.

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 

```

I suspect the problem might be related to what we see in the attached image.

---

### Post by earthpigg on 2009-09-06
system -> admin -> hardware drivers

enabled?

and have you tried selecting 'detect displays' in monitor resolution settings?

---

### Post by Daimoneze on 2009-09-06
Hardware drivers reports no restricted drivers available to enable (I'm pretty sure that's actually correct with this system).

After detecting displays the unknown monitor is still there.

---

### Post by twright on 2009-09-06
I suggest you try clicking on the second monitor and seeing if an off option is present - as far as I remember the multiple monitor handling in jaunty is a lot more reliable so that might be your issue.

---

### Post by Daimoneze on 2009-09-06
So I ran ```
dpkg-reconfigure xserver-xorg
``` and pushed through all the defaults. Restarted GDM and now compiz is back and the unknown monitor is gone. I'm marking the thread as solved.

---

