---
title: "compiz cube not working"
date: 2009-02-18
forum: General Help
---

### Post by ahsun on 2009-02-18
Hi

I can't get the cube to work.. I did have cube and rotation checked. it only showed be 2 desktops.. then i restarted.. and now i can't get it launch from system tools.. i select it and nothing happens.. when i try to launch it from terminal i get this:

Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

I'm begining to think maybe Ubuntu is not for me
Any help will be greatly appreciated

---

### Post by CRIMPS on 2009-02-18
I think you probably have upgraded to 8.10?  One of the updates breaks the Nvidia drivers that were working.  Now, you will need to start looking into how to upgrade to the latest Nvidia drivers.  This isn't always simple.  

Many people running Intrepid ran into this issue.  For some, the fix was quite easy. For others, like me :( , it wasn't.  You should try doing a search on 8.10, nvidia drivers, etc.

There are others on this site that can help you as well.  But you may want to move this thread to another Forum.

If this is not the case and I am way off, then please provide us with some more information so we can help you further.

---

### Post by CRIMPS on 2009-02-18
Let me just add something else to this because you should understand what reasonable expectations should be when running the newest version of Linux, Compiz, and other cool eye candy (because I went through this a couple of years ago when I switched to Linux.)

I generally enjoy running cutting edge software! :)  Its exciting!  However, there are times... when running on the edge, that you get cut.  If you are new to Linux and you want to just get through the break-in period of leaning a new OS, you may want to stick to an LTS version of Ubuntu.

Good Luck!

---

### Post by ahsun on 2009-02-18
HI, 
Thanks for your reply, and thanks for your second advice.
I will mention this before i go any further I'm using ATI RADEON x1200.. would nividea drivers have any impact as mentioned in your previous post.

thanks

---

### Post by CRIMPS on 2009-02-18
ha!  I think I just scanned through the return that you attached and I saw "Nvidia: Not present".  

So I think you probably are just having some issues with Compiz more likely.  

Take a look at this link.  It looks like there is a resolution in here.

[http://ubuntuforums.org/showthread.php?t=571645&page=3]("http://ubuntuforums.org/showthread.php?t=571645&page=3")

---

### Post by ahsun on 2009-02-18
Thanks alot my friend. That did that trick.. Thanks for your time

---

