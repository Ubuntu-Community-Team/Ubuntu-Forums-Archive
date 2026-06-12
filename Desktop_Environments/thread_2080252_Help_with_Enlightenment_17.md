---
title: "Help with Enlightenment 17"
date: 2012-11-03
forum: Desktop Environments
---

### Post by Argenteus on 2012-11-03
I've started using E17, and so far I really like it. But it has some crucial issues that, if I can't find a way to solve, will make me return to Gnome-Shell. Can anyone help with these issues?

1. No digital clock on panel - That analog clock is nigh unreadable at the small size I have the shelf set at, and I don't want to waste more screen realestate.

2. Serious glitchiness with GTK apps - Programs that use gtk have serious glitchiness. They dont resize properly, sometimes get odd bits of transparency or freeze up. They also don't theme properly, but I can fix that by launching the gnome-settings-daemon.

3. (Minor) No scale plugin or expose - When I was using Unity with Compiz, I had scale plugin. With Gnome-Shell, the activities overview functioned similarly. And I know Mac has something similar called Expose. The point is, while I can do without it, my entire method of managing windows before consisted of minimize and the scale plugin or overview.

4. No way to have buttons on left side without using a not very good theme - I tried recompiling the theme and changing it to look better, but it wouldn't compile after I deccompiled.

5. Occasional segfaults on menus - These used to be whenever I passed over "Accessories" or "Other", but I fixed that by removing certain problem items. Now it just occasionally does it randomly.

6. Keyboard volume control buttons don't work - I have to use the Mixer module.

Other than these issues, I love it, so if you can help me solve any of these issues, please help.

---

### Post by ajgreeny on 2012-11-03
As I understand it, the best implementation of E17 is probably in Bodhi Linux, now at version 2.1.0.

It is based on Ubuntu, does everything the Ubuntu way, ie sudo etc, uses the Ubuntu repositories, and you can also use synaptic (not sure about software-center; I never use it in Ubuntu).

I have tried it out on a test partition I keep for that sort of trial, and liked it very much; it certainly has the ability to use a digital clock in the panel.  I can't comment on your other problems associated with adding E17 to ubuntu, but in my test of Bodhi I never saw any of the problems you speak of, which may not mean they don't exist, more that I use my computer differently to your way.

Have a look at [http://jeffhoogland.blogspot.co.uk/2012/09/bodhi-linux-210-released.html](http://jeffhoogland.blogspot.co.uk/2012/09/bodhi-linux-210-released.html) for more details and information.

---

### Post by Argenteus on 2012-11-03
I've heard of Bodhi Linux, but I didn't really want to switch distros and have to go through the hassle of copying over all my stuff to an external drive, and my tiny 32gb ssd doesn't have room for a dual boot. I could try through the live usb, but that's far from a long term solution. I'll give it a try, though, if I'm ever distro-surfing. Anyone else know of solutions to the bugs in my OP?

---

### Post by kevinmchapman on 2012-11-04
I don't know how old the version of E17 is that you are using, or which modules are included, but I'm basing my responses on a fairly current version of the Arch packages.

> **Argenteus said:**
> 
1. No digital clock on panel - That analog clock is nigh unreadable at the small size I have the shelf set at, and I don't want to waste more screen realestate.


A while back, there were separate digital and analogue clock modules, but now they are combined as Clock. Check the settings to switch between digital/analogue, week start day, etc.

> **Argenteus said:**
> 
2. Serious glitchiness with GTK apps - Programs that use gtk have serious glitchiness. They dont resize properly, sometimes get odd bits of transparency or freeze up. They also don't theme properly, but I can fix that by launching the gnome-settings-daemon.


I have not seen this myself. I can only suggest playing with the settings in the Composite module. Worst case, try removing the .e directory from your home directory, and setting up your E17 preferences again.

> **Argenteus said:**
> 
3. (Minor) No scale plugin or expose - When I was using Unity with Compiz, I had scale plugin. With Gnome-Shell, the activities overview functioned similarly. And I know Mac has something similar called Expose. The point is, while I can do without it, my entire method of managing windows before consisted of minimize and the scale plugin or overview.


Composite Scale is one of the modules which seems to missing from my current install, but it was there in several previous releases. I don't know if that is a deliberate or accidental Arch packaging change, or if there is a wider issue and it is broken, so not included in current snapshots.

> **Argenteus said:**
> 
4. No way to have buttons on left side without using a not very good theme - I tried recompiling the theme and changing it to look better, but it wouldn't compile after I deccompiled.


I believe it is tied into the theme. I have never bothered with themes, so cannot help with manipulating the edje packages.

> **Argenteus said:**
> 
5. Occasional segfaults on menus - These used to be whenever I passed over "Accessories" or "Other", but I fixed that by removing certain problem items. Now it just occasionally does it randomly.


I have seen the first problem too, and fixed it by removing some .desktop items (xterm principally).

> **Argenteus said:**
> 
6. Keyboard volume control buttons don't work - I have to use the Mixer module.


Probably hardware-specific, as mine work. If reassigning the keys in the Keys settings does not work, it may be worth using a separate application like xbindkeys.

---

### Post by Argenteus on 2012-11-04
I'm using the latest version accessible via apt-get on 12.04, but it may be heavily outdated, I don't know. The clock doesn't actually seem to have that setting you mentioned, so this is sort of likely. I even tried using the really old WM independant tool Skippy-xd for expose, and also tried using the windows utility DExpose2 with Wine, but neither worked at all, the first saying my WM wasn't standards compliant enough to allow it, and the second not recognizing any windows as existing. I guess I'll just wait until the Arch switch I was planning to do around christmas time and try e17 again then. Until then, unless someone else has some advice, I'll have to use Gnome-Shell (which having now used something much better, I'm beginning to despise).

---

