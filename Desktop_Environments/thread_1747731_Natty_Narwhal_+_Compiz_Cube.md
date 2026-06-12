---
title: "Natty Narwhal + Compiz Cube?"
date: 2011-05-02
forum: Desktop Environments
---

### Post by erahm on 2011-05-02
Does anybody know how to get the cube working again in 11.04?

I got the same basic functionality, but I don't have a cube. I only have 2 sides that flip. I really miss having the full 4 desktops.

---

### Post by mc4man on 2011-05-03
go back into ccsm and under general options > Desktop size go w/ 4 or more horizontal and normally 1 vertical
(you can't rotate up, but can rotate on other v levels by moving there.

---

### Post by Teito on 2011-05-03
Hi

I tried to enable the cube option and then he asked me to disable some plugin which I clicked "Yes", and when I re-started I'm not able to view a single interface. just icons, no taskbar and any interface as in everything is shattered. Please let me know if there is any command line option wherein I can enable the plugins.

---

### Post by JOHNNYG713 on 2011-05-03
> **Teito said:**
> Hi

I tried to enable the cube option and then he asked me to disable some plugin which I clicked "Yes", and when I re-started I'm not able to view a single interface. just icons, no taskbar and any interface as in everything is shattered. Please let me know if there is any command line option wherein I can enable the plugins.

see this for resetting unity and compiz back to the original settings ! [http://www.webupd8.org/2011/04/how-to-reset-unity-launcher-icons-or.html](http://www.webupd8.org/2011/04/how-to-reset-unity-launcher-icons-or.html)

---

### Post by Mad-Halfling on 2011-05-03
Do not use the compiz manager to change settings (or be very cautious if you do so) - I've found you need to do it manually - my answer from another thread will probably help:-

----------------------------
I found that enabling the compiz cube, and other settings hosed my window manager when using 11.04 in classic mode, so I went back to Unity. However there are ways you can get the cube working in Unity, so these should work in classic, too, I would guess. What I've found is DON'T use the compiz settings manager, this seems to wreak merry hell, but you could try manually editing the config files - this certainly (as I mentioned) worked for the desktop cube in Unity.

Have a look at this

[http://www.omgubuntu.co.uk/2011/04/compiz-cube-natty/](http://www.omgubuntu.co.uk/2011/04/compiz-cube-natty/)

it's supposed to be for Unity but I don't see any reason why it shouldn't work in classic - the downside is that you have to manually edit the config file, but it might help. Personally I'm really disappointed at this lack of regression functionality from Canonical - I really expected it to be a flawless transition back. I would imagine this may drive a lot of people away from Ubuntu if they don't want to use Unity and certainly (IMHO) goes against the "Linux for human beings" ethos - I've used Ubuntu for nearly 6 years now, and haven't ever seriously considered changing distro but I actually had Mint downloading in the background while I was poking around with this, in case a reinstall to a different distro was less painful that fixing the problem

---

### Post by Pablo Pablovski on 2011-05-03
Quite. I tried upgrading to 11.04 from 10.10 and had the same problems with CCSM settings, and lost toolbars, couldn't move windows on the desktop etc. plus I lost the cube rotation and desktop switchers. Faffed about with it for a while, but eventually got fed up and restored 10.10 from backup - instant gratifcation. And I get AWN back!

I'm sure they'll get this sorted out soon, but it's disappointing to suffer such a significant regression - so I'm planning to leave 11.04 alone for a while.

---

### Post by dreamslides on 2011-05-03
Yea but enabling it doesn't allow me to use Cube Reflection & Deformation or 3D Windows does it? Are they still broken.

---

### Post by erahm on 2011-05-03
I've actually got all this working again. Installed compiz-fusion plugins as well and restored my desktop to the way it was before I upgraded.

Turns out that I was on the right path, just had 2 rows and 2 columns when I needed 1 row and 4 columns for the cube to actually work. That's why I only had a 2-sided panel.

---

