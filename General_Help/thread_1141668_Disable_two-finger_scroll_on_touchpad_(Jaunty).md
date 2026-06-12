---
title: "Disable two-finger scroll on touchpad (Jaunty)"
date: 2009-04-28
forum: General Help
---

### Post by chezzo on 2009-04-28
Hi
Just upgraded to Jaunty on my Dell Inspiron 640m laptop. I was previously able to use a two-fingered tap on the (Synaptics) touchpad to middle-click and three-fingered tap to right-click, but Jaunty has now added the ability to scroll by dragging two fingers up and down. Unfortunately, I don't really want this "feature" - it's not an exact science, and a lot of the time when I want to middle-click using a two-finger tap, it gets interpreted as a scroll action instead. And anyway, I'm used to scrolling using the edges of the touchpad.
Is there any way to disable the two-finger scroll motion, whilst keeping all the others?
Thanks!

---

### Post by chezzo on 2009-05-01
... anyone?

---

### Post by Panacid on 2009-05-03
Someone PLEASE tell us how to do this. The two finger scroll is really buggy on my system.

---

### Post by chezzo on 2009-05-05
Solved it! Using this post:[http://ubuntuforums.org/showthread.php?t=1127095&page=2](http://ubuntuforums.org/showthread.php?t=1127095&page=2)

Open a terminal and type:
```
cd /usr/share/hal/fdi/policy/20thirdparty/
sudo cp 11-x11-synaptics.fdi 11-x11-synaptics.fdi.bak
gksudo gedit 11-x11-synaptics.fdi
```
(Second line makes a backup of the file in case something goes wrong)

Then in the text file that opens, find the line
```
<merge key="input.x11_driver" type="string">synaptics</merge>
```

and paste these three lines underneath:
```
<merge key="input.x11_options.SHMConfig" type="string">On</merge>
<merge key="input.x11_options.VertTwoFingerScroll" type="string">0</merge>
<merge key="input.x11_options.HorizTwoFingerScroll" type="string">0</merge>
```

Then save, close and reboot!

---

### Post by Panacid on 2009-05-06
THANK YOU CHEZZO! I can once again surf the interwebs without getting so frustrated that I throw my computer.

With Intrepid, I was using the side of my touchpad to scroll. That is no longer working, so I'm happy just using the up/down arrow keys. Two finger tap once again gives me the middle button function and three finger tap gives right click. THANKS AGAIN!

:guitar:

---

### Post by chezzo on 2009-05-07
> **Panacid said:**
> With Intrepid, I was using the side of my touchpad to scroll. That is no longer working, so I'm happy just using the up/down arrow keys.

That's weird, mine still works fine... If you have gsynaptics (Preferences -> Touchpad) installed there's an option to turn side-scrolling on and off.

---

