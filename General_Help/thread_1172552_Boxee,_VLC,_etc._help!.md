---
title: "Boxee, VLC, etc. help!"
date: 2009-05-28
forum: General Help
---

### Post by vinay427 on 2009-05-28
Hey,
I'm really new here, so sorry if it's in the wrong place.  Mods: feel free to move it.  Anyway, I installed Boxee and VLC in 8.10, which I installed by formatting Vista.  Then, I sucessfully upgraded to 9.04 (the beta).  Naturally, most of my sources in the repositories were disabled, so I added the jaunty source for Boxee.  I opened it after installing, and it suddenly closed.  I tried it with XBMC, same deal.  Then I tried Elisa, and it opened but ran extremely slow.  I finally tried opening some .avi movie files in VLC, and same thing again.  I'm guessing it's because of my graphics driver or something, so I Googled some stuff and opened the xorg.conf file in etc/x11.  I edited some stuff then coudln't save because it said I didn't have permission but didn't prompt me for a password because I am on the only account, and therefore am an admin.  I apparently have an integrated Intel graphics card so I think I need the i810 driver.  In xorg.conf, it doesn't show anything for the driver or type of card.  I figured that out by running lspci.  Please help!

Also, I had another issue some time back and asked for help, and I recieved some response to add something to some document.  I couldn't even figure out how to open the document.  I'm extremely proficient with Mac and Windows (which I hate, by the way), and just started experimenting with Ubuntu.  Thanks a lot guys!

---

### Post by vinay427 on 2009-05-28
Anyone have any suggestions?  Please?  Thanks a lot in advance!

---

### Post by zvacet on 2009-05-28
> I edited some stuff then coudln't save because it said I didn't have permission but didn't prompt me for a password because I am on the only account, and therefore am an admin. 

You must use **sudo**.

```
gksudo gedit /etc/X11/xorg.conf
```

Read [RootSudo.]("https://help.ubuntu.com/community/RootSudo")

---

### Post by vinay427 on 2009-05-28
> **zvacet said:**
> You must use **sudo**.

```
gksudo gedit /etc/X11/xorg.conf
```

Read [RootSudo.]("https://help.ubuntu.com/community/RootSudo")

Thanks!  Well, I tried it now, and it edited fine, but the applications still don't work.  I got that info from post #3 [here]("http://forum.boxee.tv/showthread.php?t=8741").  Anyone have any suggestions?

---

### Post by vinay427 on 2009-05-29
Now, I figured out how to add my graphics driver.  I can now run VLC fine but Boxee opens then closes in about ten seconds.  Any help?

---

### Post by ugm6hr on 2009-05-29
If VLC works OK now, it is no longer a video driver issue.

Therefore, it is likely a bug in Boxee.

I think Boxee is based on XBMC, which remains a a little buggy on Jaunty too.

---

### Post by vinay427 on 2009-05-30
> **ugm6hr said:**
> If VLC works OK now, it is no longer a video driver issue.

Therefore, it is likely a bug in Boxee.

I think Boxee is based on XBMC, which remains a a little buggy on Jaunty too.

Ok, thanks a lot for the clarification!  I'll try reinstalling Boxee because right during the ten seconds it is running there is some white writing at the top that started after I updated the graphics driver.  Anyone else seen this?

---

### Post by vinay427 on 2009-05-31
Now, I found out Boxee runs but exits right after the login screen.  I just installed Moovida, and as you might expect, it ALSO doesn't work.  The first time it's launched after a restart it shows a splash screen but then closes.  Until the next restart, it won't do anything.  Please help!  I have three seasons of a TV show waiting for me!

---

### Post by vinay427 on 2009-06-07
Anyone have any suggestions?

---

