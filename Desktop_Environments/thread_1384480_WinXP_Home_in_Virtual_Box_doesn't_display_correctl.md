---
title: "WinXP Home in Virtual Box doesn't display correctly"
date: 2010-01-18
forum: Desktop Environments
---

### Post by etech22 on 2010-01-18
Hi,

I have windows xp home sp3 installed on a VirtualBox image on Ubuntu 9.10 x64. The install worked fine the first time I started it to setup windows, but subsequent attempts have an issue with the display at least 85% of the time.

What happens is Windows loads just fine, but when the desktop pops up all that is shown is the wallpaper, with no taskbar, no desktop icons. The mouse also displays, but a right click brings no menu. Also, the screen saver seems to work as well if I leave it up for a while.

Is this a known issue? Does anyone have any suggestions?

Any help would be appreciated.


etech

---

### Post by etech22 on 2010-01-21
Anyone?

---

### Post by howefield on 2010-01-21
Is the guest responsive at all ?

Eg, do keyboard shortcuts work, if you press the windows + E keys together, does windows explorer pop up ?

I'd try installing guest additions, if you already have done that, I'd reinstall the xp guest.

One thing about installing xp into virtualbox, it's a lot speedier than the real thing :)

---

### Post by etech22 on 2010-01-21
> **howefield said:**
> Is the guest responsive at all ?

Eg, do keyboard shortcuts work, if you press the windows + E keys together, does windows explorer pop up ?

I'd try installing guest additions, 

Hi,
Keyboard shortcuts appear to work, meaning the IDE activity icon flashes with windows + E, and the mouse cursor shows activity, but the desktop shows nothing, still just a blank wallpaper.

Same happens when I goto devices > install guest additions. Activity, but nothing shows up.

> if you already have done that, I'd reinstall the xp guest.

I suppose I'll give this a try--another hour wasted :/

> One thing about installing xp into virtualbox, it's a lot speedier than the real thing :)

Agreed! It's nice when it's worked.

Thanks,


etech

---

