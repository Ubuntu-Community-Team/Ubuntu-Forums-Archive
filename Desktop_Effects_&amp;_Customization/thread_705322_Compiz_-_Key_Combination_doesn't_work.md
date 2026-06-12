---
title: "Compiz - Key Combination doesn't work"
date: 2008-02-23
forum: Desktop Effects &amp; Customization
---

### Post by swatto on 2008-02-23
Hi all,

I have compiz and the manager installed so I can see Advanced Desktop Effects and select plugins etc.  But when i press a key combination to use one of the plugins nothing happens.

Please can someone help me out,

Cheers.

---

### Post by swatto on 2008-02-23
```
[1] 5849
swatto@swatto-desktop:~$ Checking for Xgl: not present.
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity
no /usr/bin/metacity found, exiting
```

that is my console output when I checked if it was running, im using restricted drivers on an ATI Radeon 9550 graphics card.

---

### Post by ultrageeky on 2008-03-19
This may sound over simplistic but I had the same issue in Kubuntu.  The solution I found was...type "compiz" into the "Run Command" menu item.  I tried it in Katapult, Console and got nothing, only after typing it (compiz) into the Run Command menu item did it run.

I also advise that you check Adept Installer (Synaptic) to ensure that all the required modules are installed (I had a few missing!).

Hope this has helped.

Note:

Just in case everything goes tits-up after running Compiz (i.e you lose your Desktop/GUI), make a note of (and use) the following tips:

To restart gdm (Ubuntu Desktop), use the following instructions:

Ctrl+Alt+F1
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
Ctrl+Alt+F1

To restart KDM (Kubuntu Desktop), use the following instructions:

Ctrl+Alt+F1
sudo /etc/init.d/kdm stop
sudo /etc/init.d/Kdm start
Ctrl+Alt+F1

For both Ubuntu and Kubuntu - if neither the above help you with recovering your desktop then you will need to reconfigure it.  Use the following instructions:

type "sudo dpkg-reconfigure xserver-xorg"

When prompted, choose the options you think most appropriate.  When it asks for the graphix driver choose "vesa".  Use the tab key to move and the spacebar to select your monitor's highest resolution and all options below that. 

type "startx"

Once back at your desktop, re-install your graphix driver.

Edit:

Take a look at this thread (I found it very useful)
[https://help.ubuntu.com/community/CompositeManager/CompizFusion]("https://help.ubuntu.com/community/CompositeManager/CompizFusion")

For the key/mouse combinations, look at [http://computerbits.wordpress.com/2006/11/02/compiz-key-combinations-list/]("http://computerbits.wordpress.com/2006/11/02/compiz-key-combinations-list/")

Edit 2:

To remove compiz from your start-up configuration, find (ctrl+f) the file "Autostart" and remove the script called "compiz" (I cut and pasted mine to my desktop).

If this has helped then please post to say so such that others in a similar spot know the usefulness of these posts. Thank You.

---

### Post by ultrageeky on 2008-03-20
> **ultrageeky said:**
> 

type "sudo dpkg-reconfigure xserver-xorg"



According to the file at /etc/X11/xorg.conf

the above quoted line can also be written:

sudo dpkg-reconfigure -phigh xserver-xorg

And remember: to access a terminal from boot, when the boot options are shown choose "Safe Mode" else press "Esc"

---

