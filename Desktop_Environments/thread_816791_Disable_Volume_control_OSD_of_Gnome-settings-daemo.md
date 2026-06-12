---
title: "Disable Volume control OSD of Gnome-settings-daemon"
date: 2008-06-03
forum: Desktop Environments
---

### Post by SoAnIs on 2008-06-03
How would one go about disabling the volume control OSD in gnome-settings-daemon. It steals focus and crashes some programs I use in WINE. Preventing it from stealing focus would be ok too.

---

### Post by ScarySquirrel on 2008-12-01
I have had some problems with this myself.
     Currently, the Volume Control Widget Popup keeps respawning and increasing or decreasing the volume repeatedly when I press either of the volume change buttons on my laptop.
     If I cannot fix this problem, how do I disable this popup widget?

---

### Post by hapsis on 2008-12-25
Same problem with my HP Laptop ZV6150 - have you got the solution for this volume button problem? It worked on earlier versions of Ubuntu but not on 8.10...

---

### Post by MaestroTech on 2009-01-24
my goodness we need to bump this up and get a solution. this seems so simple.

---

### Post by zachalekos on 2009-02-28
bump

---

### Post by zachalekos on 2009-02-28
i've disabled media-keys in gnome-settings-daemon but now I need to use the mouse to control the volume. It's not a perfect solution.

---

### Post by derekbuc on 2009-03-22
Any solution on this yet lads?

---

### Post by zachalekos on 2009-03-23
No solution yet. It seems the powers that be don't consider it a bug.

---

### Post by JohnFH on 2009-03-23
I had a similar issue in KDE.  I removed the default media key functionality and created a global keyboard input to make a dcop call to change the volume instead.  Now the volume changes in smaller steps and with no OSD.  Not sure how, or if it's possible, to do the same thing in Gnome.  Sorry.

By the way, there are big changes in this area in Jaunty, so you may just want to wait (not long now) until the next release before spending too much time on this.

---

### Post by ldrn on 2009-05-14
I was having horrible performance issues with it and Compiz... like JohnFH, I just removed the default functions. In my case I used aumix to control it with scripts like:
aumix -v +1 
aumix -v -1
aumix -v 0

For up, down, and mute. (Unmute requires a bit more of a complicated script.)  I even added OSD notification back via xosd, but that's probably not what you all are after if it crashes.

---

### Post by therendus on 2009-10-16
> **SoAnIs said:**
> How would one go about disabling the volume control OSD in gnome-settings-daemon. It steals focus and crashes some programs I use in WINE. Preventing it from stealing focus would be ok too.

To disable the osd all the way:
[http://ubuntuforums.org/showthread.php?t=1164960&highlight=Disable+volume+OSD#td_post_7315643](http://ubuntuforums.org/showthread.php?t=1164960&highlight=Disable+volume+OSD#td_post_7315643)

---

### Post by gchatzim on 2010-03-22
> **therendus said:**
> To disable the osd all the way:
[http://ubuntuforums.org/showthread.php?t=1164960&highlight=Disable+volume+OSD#td_post_7315643](http://ubuntuforums.org/showthread.php?t=1164960&highlight=Disable+volume+OSD#td_post_7315643)

this does not work for me.
i was bothered by the volume osd because it through me out of fullscreen whether on youtube or vlc.
i fixed it by setting the focus_prevention_level to 2.
to set this run gconf-editor go to /apps/compiz/general/screen0/options.
of course this has the unfortunate side-effect that some other windows that i would like to have auto-focus (like the 'run application') no don't.

---

