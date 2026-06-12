---
title: "only boots to failsafe after i upgraded"
date: 2008-03-11
forum: Desktop Effects &amp; Customization
---

### Post by Jeremy_Kyle_Vanhorn on 2008-03-11
i upgrade ubuntu to the latest version, ever since i did i wont let me boot to in to reg gnome... i have to use failsafe mode.... and also i believe the reason that my desktop effects <like the cube and stuff like that> wont work.... im not use to ubuntu, ive only been playing with it for about a week, any help?

thanks you all [http://ubuntuforums.org/images/smilies/icon_smile.gif:](http://ubuntuforums.org/images/smilies/icon_smile.gif:))

---

### Post by Live-Dimension on 2008-03-11
The quickest, easiest and fastest way is to do a clean install, since you've been playing around with it.

I'm kinda new to ubuntu, so sorry that I can't help more. This is in the wrong forum, btw.

---

### Post by Zorael on 2008-03-11
I'll tell you right away, you'll avoid many headaches if you just do a clean Gutsy install.

That said, if you still want to make it work, please post the contents of your **/etc/X11/xorg.conf** file, and your **/var/log/Xorg.0.log** file.

You can probably make it start in non-failsafe if you reset your xorg.conf file, but do post those before doign that, as you'd only fix the problem without finding out what it was, so nothing learned.

```
$ sudo dpkg-reconfigure -phigh xserver-xorg
```

When you restart/reload X (Ctrl+Alt+Backspace), it will load up with the default settings; meaning low resolution, ugly, extra mouse/screen configurations gone, etc. But then you take it from there.

---

### Post by Jeremy_Kyle_Vanhorn on 2008-03-12
Quote: 
     I'll tell you right away, you'll avoid many headaches if you just do a clean Gutsy install.

That said, if you still want to make it work, please post the contents of your /etc/X11/xorg.conf file, and your /var/log/Xorg.0.log file.

You can probably make it start in non-failsafe if you reset your xorg.conf file, but do post those before doign that, as you'd only fix the problem without finding out what it was, so nothing learned.


Code:
$ sudo dpkg-reconfigure -phigh xserver-xorgWhen you restart/reload X (Ctrl+Alt+Backspace), it will load up with the default settings; meaning low resolution, ugly, extra mouse/screen configurations gone, etc. But then you take it from there.



i tried that but the only thing that happened was that my comp. screen went black for 5 sec and it had no responce to the command.... 
i think the best thing i can hope for is to just reinstall ubuntu (the latest version)
sadly i dont have the boot cd. but life will go on.

---

### Post by Therion on 2008-03-12
nVidia user?  If so, try downloading and using the latest version of Envy.  Kernel updates busted my setup too, but Envy got things straightened out for me.

No, NOT the repo version get it *from the website*.  Install the Restricted Driver using Envy, reboot, etc.  

Afterwards, you may need to go into xorg.conf and make some minor adjustments like monitor resolution.

---

### Post by Zorael on 2008-03-12
If it is indeed the Nvidia kernel issue you can **completely remove/purge** (in Synaptic/Adept Manager) the nvidia-glx-new (nvidia-glx, or nvidia-glx-legacy) package, then reinstall it, if you want to keep the community-supported version.

Console command, if you don't want to do it through Synaptic/Adept:
```
$ sudo apt-get remove --purge nvidia-glx*
$ sudo apt-get install nvidia-glx-new
```
Obviously, replace nvidia-glx-new with nvidia-glx-legacy if you have an old card.

If you don't have an Nvidia card, this couldn't be the problem, of course.


Regardless; could you post the contents of your /etc/X11/xorg.conf and /var/log/Xorg.0.log file?

---

### Post by Jeremy_Kyle_Vanhorn on 2008-03-12
im running on ati...... so i dont know, i mean i have no clue, becouse before i udated to the latest version the desktopp effects worked, ....

---

### Post by Zorael on 2008-03-12
Okay.

But could you please post the contents of your /etc/X11/xorg.conf and /var/log/Xorg.0.log files? Just open them in gedit, and copy/paste here. Then we can hopefully see what's wrong.

---

### Post by Jeremy_Kyle_Vanhorn on 2008-03-12
i hate to say this but i really dont undertand what you ment... im fairly new at this so will you please exlain better if u dont mind, i opened gedit but i really dont understand what you mean,  and for that im sorry :(

---

### Post by Zorael on 2008-03-13
Fair enough. :)

Open Gedit or some other text editor you have. It should be under Applications someplace.

Go to Open, and browse to **/etc/X11/**. Then double-click on the file **xorg.conf**.

Copy all the text there, and paste the contents into a new reply here.

Then do the same for **/var/log/Xorg.0.log** (Gedit -> open -> **/var/log/** -> doubleclick on Xorg.0.log -> copy -> paste into here).

Then post. :)

---

### Post by crocowhile on 2008-03-15
Same thing happened to me. I figured it was the xserver update. I forced back to the older version and reinstalled the nvidia drivers. My guess is that reinstalling the driver would probably have been enough.
Now everything works again: only thing I get a 5 seconds blackout at start before running compiz.

---

### Post by freec on 2008-03-17
same here
i have the same problem after upgrading from 7.04 to 7.10
i have to configure the screen resolution and desktop effects wont work
my graphics card is an Intel Graphics Media Accelerator 950
what could be the problem?

---

