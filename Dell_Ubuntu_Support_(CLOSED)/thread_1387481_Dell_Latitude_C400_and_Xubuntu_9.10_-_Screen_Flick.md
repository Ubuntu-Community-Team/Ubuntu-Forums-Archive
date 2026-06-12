---
title: "Dell Latitude C400 and Xubuntu 9.10 - Screen Flicker and Cursor Issue"
date: 2010-01-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mremic01 on 2010-01-21
Hi. I'm relatively new to the world of Linux. I was hoping to install Xubuntu on my Dell Latitude C400 after I tried Ubuntu and it turned out to be too much for the hardware. I just tried Xubuntu with the live CD. After it boots up, the screen flickers constantly. It makes me feel like I'm going to have a seizure. The mouse cursor also seem to click a few pixels up and to the right of where the cursor is located on the screen, making it difficult to click on anything. I would like to figure out a fix for these problems before actually installing Xubuntu so if I decide Xubuntu is too slow, I won't have to spend hours putting Windows XP back on it and reloading all the drivers. Can anyone help me out, or would I have to actually install Xubuntu to do anything?

Thanks in advance.

---

### Post by mcrysler on 2010-02-10
I'm having the exact same issue with Ubuntu 9.10 and Kubuntu 9.10.  Anyone have any ideas how to fix this?  I've tried changing settings in the xorg.conf file but nothing seems to help!

---

### Post by mcrysler on 2010-02-11
Anyone??  Bueller?

---

### Post by ottosykora on 2010-02-11
Lucky guys

I have not been able to install anythnig beyond the xubuntu 8.10 on that machine. Thought I gave it 1g of ram etc, but even then the xubuntu graphic does not run well, it is just on the edge of its capabilities I think.

---

### Post by Jose Catre-Vandis on 2010-02-11
Try a command line install (F4 at boot) and then a minimal xorg environment with openbox (see psychocats tutorial)..... or xfce.

---

### Post by excogitation on 2010-03-20
just fyi - I just installed 9.10 on a C400 and the flickering stops after ~5 seconds also I can't confirm the mouse cursor issue.


Runs quite nice on the 1.4GHz version with 512MB

apart from not waking up from standby.

---

### Post by bobcollard on 2010-03-21
Need something light, fast and stable?  Not a plug, but, you might check out Fluxbox on Linux Mint.  It's based on Ubuntu with a lot of trimming, a great menu and support by our forum.
[http://www.linuxmint.com/download_ce.php](http://www.linuxmint.com/download_ce.php)

---

### Post by Ramthebuffs on 2010-03-22
puppy linux works on the c400 without issue.

---

### Post by bandoba on 2010-04-17
I was yet another soul looking for a fix to flickering problem on C400 with Ubuntu or XUbuntu. Here is what helped me:

1. Boot XUbunt from HDD.
2. Press Ctrl-Alt-F2 to go to 2nd virtual console.
3. Just issue sudo apt-get update followed by sudo apt-get dist-upgrade.
4. Upgrade took about 10-15 minutes.
5. Reboot after upgrade.
6. Got a nice stable XUbunt login window.

Try one more reboot if you don't see the stable screen on #6 above. HTH.

---

### Post by lalunatech on 2010-05-14
I had the flickering screen issue with a Dell C400 (And other Linux boot CDs) and turning off screen video expansion in the bios setup fixed it. Hit F2 on bios screen and Alt-P to get down to the apposite page.

I think that is the 1st time I have used the word apposite in my life!

---

