---
title: "Window freeze till mouse is moved"
date: 2009-07-11
forum: Desktop Environments
---

### Post by Gsundbrunn on 2009-07-11
Hi,

strange behaviour. I installed the latest kubuntu on my Amilo Laptop. Looks well, but:

The screen freezes continously till I move the mouse or type some text. It looks like the complete system is waiting for an action. 

As an example: downloading a huge file will start and then stop after 5%. If I do nothing, nothing happens. Then I move the mouse and it continous. The same with the mousecursor. These to spinning little "balls" - during a whatever they stop spinning. When I move the mouse or touch a key, it starts orking again.

An additional effekt is that the clock stops counting, too! After two hours at the laptop the clock lost about 45 minutes and I have to set the correct time manually again.

Some help would be appreciated...

Regards

Stefan

---

### Post by Gsundbrunn on 2009-07-12
Update: Issue ist still existing. I tried Gnome, XFCE as Windows Manager. No difference. Same issue. Even if I disable Compiz it happens.

Any help is appreciated...

Thanks!

Stefan

---

### Post by Zorael on 2009-07-13
Intel graphics? I seem to remember reading about some bug where the screen wouldn't update unless you moved the cursor. Related?

Here it is, [fdo#21555](http://bugs.freedesktop.org/show_bug.cgi?id=21155) (actually [fdo#20896](http://bugs.freedesktop.org/show_bug.cgi?id=20896[/url)). Supposedly fixed in newer drivers; perhaps you could find an update in the backports repository, or from [ubuntu-x-swat](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates), or [xorg-edgers](https://launchpad.net/~xorg-edgers/+archive/ppa), or [tormodvolden's ppa](https://launchpad.net/~tormodvolden/+archive/ppa).

---

### Post by RJARRRPCGP on 2009-07-13
> **Gsundbrunn said:**
> 

The screen freezes continously till I move the mouse or type some text. It looks like the complete system is waiting for an action. 

As an example: downloading a huge file will start and then stop after 5%. If I do nothing, nothing happens. Then I move the mouse and it continous. The same with the mousecursor. These to spinning little "balls" - during a whatever they stop spinning. When I move the mouse or touch a key, it starts orking again.



Sounds like what I encountered when running Windows XP (IIRC) on QEMU. 

It seems to go faster when I keep moving the mouse!

---

### Post by Gsundbrunn on 2009-07-13
> **Zorael said:**
> Intel graphics? I seem to remember reading about some bug where the screen wouldn't update unless you moved the cursor. Related?

Yes... Thanks... Sounds like the same issue. I will try suspending and will see. But its an ATI grafik, not an Intel. I installed the latest driver fom ATI - no change.

I will continue checking.

Thanks!

Stefan

---

### Post by pc.maint on 2013-02-13
Exactly the same issue on an Acer TM4200 laptop with Ubuntu 12.04.2 and GNOME desktop. Does the same with Unity.

It will run for a minute or two and then the desktop freezes (applications stop, clock applet stops, any audio/video output stops or loops, uploads/downloads stop). A nudge of the mouse or touch any key and the system continues from where it left off.

---

