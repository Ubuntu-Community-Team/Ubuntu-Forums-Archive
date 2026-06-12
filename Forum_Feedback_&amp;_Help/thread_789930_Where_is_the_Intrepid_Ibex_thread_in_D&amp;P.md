---
title: "Where is the Intrepid Ibex thread in D&amp;P?"
date: 2008-05-11
forum: Forum Feedback &amp; Help
---

### Post by disturbedite on 2008-05-11
title says it all.  shouldn't the intrepid section be in the dev & prog section by now?

---

### Post by LaRoza on 2008-05-11
> **disturbedite said:**
> title says it all.  shouldn't the intrepid section be in the dev & prog section by now?

Are people able to really test the packages yet?

I have a Hardy install all ready to be Intrepided...

---

### Post by KIAaze on 2008-05-11
I've been searching for it too.
I allready updated my sources.lst and upgraded to intrepid.
However, since my updates yesterday, I can't start X anymore. :(

I get a message about get-edid not being installed.
I installed the read-edid package but still can't start X.

I also noticed a package conflict between system-config-printer-kde and system-config-printer-gnome.
They seem to have a common file. So I couldn't upgrade the gnome one without removing the one from KDE.

(I have gnome,xfce,kde,enlightment and ratpoison installed. Not really a clean Hardy system to upgrade from. ^^').

---

### Post by LaRoza on 2008-05-11
> **KIAaze said:**
> I've been searching for it too.
I allready updated my sources.lst and upgraded to intrepid.
However, since my updates yesterday, I can't start X anymore. :(

I get a message about get-edid not being installed.
I installed the read-edid package but still can't start X.

I also noticed a package conflict between system-config-printer-kde and system-config-printer-gnome.
They seem to have a common file. So I couldn't upgrade the gnome one without removing the one from KDE.

(I have gnome,xfce,kde,enlightment and ratpoison installed. Not really a clean Hardy system to upgrade from. ^^').

Perhaps the forum should wait until it is at least bootable to a functional desktop for a few seconds at least before having such a forum.

---

### Post by KIAaze on 2008-05-11
Mmh, I don't like this...
I can't even start in vesa mode. (I booted in safe mode with a Feisty LiveCD I had and copied the device, monitor and screen sections from there to my xorg.conf.)

I think I'll only upgrade from command-line from now one with a script that logs upgraded packages so I can know what changed.

edit: Found something:
[http://ubuntuforums.org/showthread.php?p=4909796](http://ubuntuforums.org/showthread.php?p=4909796)

---

### Post by KIAaze on 2008-05-11
Ok, X is working again. :)

I was unable to download the hardy version of libxfont1 (packages.ubuntu.com seemed down), so I had to do it through apt-get.
After changing my sources.lst to hardy and doing "apt-get install --reinstall libxfont1", it still didn't work.
Installing libxfont1 from source worked but didn't solve the problem.

So I had to remove it completely, which removed almost all xserver packages, then install it again.
After that I just installed the ubuntu-desktop package to get all necessary xserver packages.

So if anybody has the same problem:
```
cd /etc/apt
sudo sed -i.bak s/intrepid/hardy/g /etc/apt/sources.list
sudo apt-get update
sudo apt-get remove libxfont1
sudo apt-get install libxfont1
sudo apt-get install ubuntu-desktop
sudo cp sources.list.bak /etc/apt/sources.list

```

---

### Post by 23meg on 2008-05-11
It would be a good idea to have the forum running in time for UDS-Intrepid.

---

### Post by LaRoza on 2008-05-11
> **23meg said:**
> It would be a good idea to have the forum running in time for UDS-Intrepid.

When is that?

---

### Post by disturbedite on 2008-05-11
> **LaRoza said:**
> Are people able to really test the packages yet?

I have a Hardy install all ready to be Intrepided...
yes.  i have been for about a week.

about not being able to boot X, the xserver isn't really the problem, per se.  it is (was?) a bug in libxfont1.  it caused a buffer overflow that made xserver unable to start correctly.  the solution is, at this point, simply not to upgrade the libxfont1 package.  (you can lock it in synaptic).

@ LaRoza
nice avatar btw, i'm a shameless trekkie. :mrgreen:

---

### Post by LaRoza on 2008-05-11
> **disturbedite said:**
> yes.  i have been for about a week.

about not being able to boot X, the xserver isn't really the problem, per se.  it is (was?) a bug in libxfont1.  it caused a buffer overflow that made xserver unable to start correctly.  the solution is, at this point, simply not to upgrade the libxfont1 package.  (you can lock it in synaptic).

@ LaRoza
nice avatar btw, i'm a shameless trekkie. :mrgreen:

Cool. I will upgrade my other Hardy install. 

I am not able to make these decisions, but I will ask the people who can make the forum about it. The fact that I will upgrade to it, and other already have, justify making it now I think.

Thanks. PrivateVoid made it after I selected the image. Resistance is futile.

[img]http://www.freesmileys.org/smileys/alien003.gif[/img]

---

### Post by disturbedite on 2008-05-11
> **LaRoza said:**
> Cool. I will upgrade my other Hardy install. 

I am not able to make these decisions, but I will ask the people who can make the forum about it. The fact that I will upgrade to it, and other already have, justify making it now I think.

Thanks. PrivateVoid made it after I selected the image. Resistance is futile.

[IMG]http://www.freesmileys.org/smileys/alien003.gif[/IMG]
cool.  thanks for asking around.  the kubuntuforums don't have an intrepid section yet either.

i can make them too.  i'm proficient in photo editing/manipulation.  as a matter of fact, i make all my avatars, among many other things...

---

### Post by LaRoza on 2008-05-11
> **disturbedite said:**
> cool.  thanks for asking around.  the kubuntuforums don't have an intrepid section yet either.

i can make them too.  i'm proficient in photo editing/manipulation.  as a matter of fact, i make all my avatars, among many other things...

I made a request. I hope it comes for before I upgrade.

Cool. I tried to use the GIMP, following a guide step by step. I failed.

---

### Post by p_quarles on 2008-05-11
> **LaRoza said:**
> I tried to use the GIMP, following a guide step by step. I failed.
Revision3 publishes a series of video podcast tutorials called PixelPerfect. Of course, it uses Photoshop, but I've learned a lot of the basics of pixmap editing watching those tutorials. In my view, the principles of image editing are the difficult part, and the specific interface is just something that takes trial and error. I recommend it. 
[/off-topic]

---

### Post by ubuntu-geek on 2008-05-12
Done! [http://ubuntuforums.org/forumdisplay.php?f=346](http://ubuntuforums.org/forumdisplay.php?f=346)

---

### Post by disturbedite on 2008-05-12
thanks guys.

---

### Post by 23meg on 2008-05-12
> **LaRoza said:**
> When is that?

[https://wiki.ubuntu.com/UDS-Intrepid](https://wiki.ubuntu.com/UDS-Intrepid)

---

### Post by wesley_of_course on 2008-05-12
> **ubuntu-geek said:**
> Done! [http://ubuntuforums.org/forumdisplay.php?f=346](http://ubuntuforums.org/forumdisplay.php?f=346)

  Thank You !  From the middle of my harddrive .

---

