---
title: "How can I get a normal volume slider?"
date: 2010-03-03
forum: Desktop Environments
---

### Post by saz on 2010-03-03
Hi,

I just installed xubuntu on my dad's notebook (he was using Arch previously, but I dont have the time to mantain it for him, so xubuntu's easy maintenance was the way to go).

The volume applet on the top bar of Xfce4 opens up the mixer, but he just wants a normal, simple slider to control the main volume, like he would get in gnome...

I'd like some help to solve this issue... What can I do and what options are there?

Thanks!

---

### Post by labinnsw on 2010-03-10
Double click should open the mixer. Single click should be the volume control. Is that what is happening?

---

### Post by saz on 2010-03-10
no. that would be nice. 

whats happening is one click opens mixer, double clicker opens mixer... 

:x

---

### Post by labinnsw on 2010-03-11
If you haven't done this yet:

Right click on the panel.
Select add to panel.
Scroll to volume control and select it.
Test the new control to see if it works as it should.
If it works, you can remove the old one. If not, you are fresh out of luck and I am fresh out of ideas.

---

### Post by inobe on 2010-03-11
if it's 9.04 it's just like that for whatever reason, upgrading to 9.10 i had a volume control slider up on the right side panel next to the time.

---

### Post by kerry_s on 2010-03-11
> **labinnsw said:**
> If you haven't done this yet:

Right click on the panel.
Select add to panel.
Scroll to volume control and select it.
Test the new control to see if it works as it should.
If it works, you can remove the old one. If not, you are fresh out of luck and I am fresh out of ideas.

xfce4 changed the volume control.

@ saz,
 you do know you just scroll on the icon to change the volume, there's no need to open anything.
but if you just have to, there's "xfce4-xfapplet-plugin" you can try using gnomes volume control, if it's stable enough & doesn't crash in xfce4.

---

### Post by kerry_s on 2010-03-11
> **inobe said:**
> if it's 9.04 it's just like that for whatever reason, upgrading to 9.10 i had a volume control slider up on the right side panel next to the time.

so they changed it again? :lolflag:
guess they just can't decide what people want. ;)
it would be nice if they just made it a preference option.

---

### Post by saz on 2010-03-11
> **labinnsw said:**
> If you haven't done this yet:

Right click on the panel.
Select add to panel.
Scroll to volume control and select it.
Test the new control to see if it works as it should.
If it works, you can remove the old one. If not, you are fresh out of luck and I am fresh out of ideas.

been there done that.

@ kerry_s

well the scroll isnt very practic cuz its a notebook (old) so no easy access to scroll) 

ill try the other option as soon as i get home (a couple of hours from now)

tyvm

---

### Post by kerry_s on 2010-03-11
> **saz said:**
> been there done that.

@ kerry_s

well the scroll isnt very practic cuz its a notebook (old) so no easy access to scroll) 

ill try the other option as soon as i get home (a couple of hours from now)

tyvm

no scroll on your touchpad?

you can always create some keyboard shortcuts or you can  use icons if all else fails.
the commands are:

raise by 3-> amixer set Master 3+
lower by 3-> amixer set Master 3-
mute/unmute-> amixer set Master toggle


i've had to do that before, i've even done scripts where i could just select it by %
example:
amixer set Master 25%
amixer set Master 50%
amixer set Master 75%
amixer set Master 100%

it's easy in xfce4 cause you can put several launchers on 1 icon.

---

### Post by saz on 2010-03-11
ok i've got XfApplet up and running, but i have no idea whats the name of the volume control applet, i've installed a lot of them,  but no volume control yet... anyone knows the name of the package to install?

---

### Post by kerry_s on 2010-03-11
> **saz said:**
> ok i've got XfApplet up and running, but i have no idea whats the name of the volume control applet, i've installed a lot of them,  but no volume control yet... anyone knows the name of the package to install?

"gnome-applets" has the volume control.

---

### Post by saz on 2010-03-11
> **kerry_s said:**
> "gnome-applets" has the volume control.

you sure? cuz i've installed that already, and that installed a bunch of gnome applets (finance, that fish, monitors and etc) but not the volume control...

---

### Post by kerry_s on 2010-03-11
see pic

---

### Post by kerry_s on 2010-03-14
so did you get it, i tried it & it works, but i'm running xfce4-panel in gnome.

---

