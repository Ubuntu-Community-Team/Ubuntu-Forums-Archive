---
title: "Problems after upgrading to feisty!"
date: 2007-04-22
forum: Desktop Effects &amp; Customization
---

### Post by thegreenblob on 2007-04-22
Ok, a few days ago I upgraded to feisty and ran into ALOT of problems, but I fixed them all aside from one which I can not figure out...

I just installed beryl for feisty and it worked fine in edgy but in feisty... when I start it all I am getting is a blank white screen.

Really no clue why and wouldn't know how to tell... 

Can someone help?

 Thanks.

---

### Post by staeryatz on 2007-04-23
I get the same problem inberyl on feisty, it worked fine in edgy. I get a completely white desktop and just the mouse pointer. I can rotate the cube, and the cube caps have the pictures on them, but all the desktop faces of the cube are white.

---

### Post by gapplewagen on 2007-04-23
I had this issue with my ATI Radeon 9800Pro and found this over at launchpad and it fixed it for me.  Add these lines to /etc/modprobe.d/blacklist

```

blacklist i82875p_edac
blacklist edac_mc

```

Original link:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78684]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78684")

---

### Post by satchelpig on 2007-04-23
> **gapplewagen said:**
> I had this issue with my ATI Radeon 9800Pro and found this over at launchpad and it fixed it for me.  Add these lines to /etc/modprobe.d/blacklist

```

blacklist i82875p_edac
blacklist edac_mc

```

Original link:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78684]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78684")

I did this and it worked.  Kind of.  But I am still having a problem.  THe white screen is gone, but now my taskbar and menu bar are gone.  I can't access any menus or anything for which tehre is not a desktop icon.  Any ideas???  Help!

---

### Post by gapplewagen on 2007-04-24
> **satchelpig said:**
> I did this and it worked.  Kind of.  But I am still having a problem.  THe white screen is gone, but now my taskbar and menu bar are gone.  I can't access any menus or anything for which tehre is not a desktop icon.  Any ideas???  Help!

From the main login screen click on the session options from the bottom left corner.  Select "Safe Gnome" or just "Gnome".  Upon login click "Just for this session" just to see if it helps you.  

I had a similar issue because I was trying to test out the builtin compiz effects but Beryl seems to have been interfering (best guess).

---

### Post by thegreenblob on 2007-04-24
hmm... It didn't work at all for me. I am still getting the same white screen. Any more help here?

---

### Post by staeryatz on 2007-05-28
Same here. I still get the white screen. :(

---

