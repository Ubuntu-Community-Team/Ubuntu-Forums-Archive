---
title: "Dual Head"
date: 2006-06-22
forum: Desktop Environments
---

### Post by DarkDancer on 2006-06-22
Ok, so I finally got my ATI card working with 3d and all, and not I would like to get the dual head aspect going, to see what I've done so far go [here.]("http://ubuntuforums.org/showthread.php?p=1171444#post1171444")

My secondary monitor acts as if it is going to work, but, well, I'll copy and past from the other post...

> Let me try explaing it. If I were to reboot right now, when I first get to the login screen, before being able to see my actual desktop, I could put my mouse cursor at the extreme left edge of the primary screen and then move it to the extreme right edge of the secondary screen (although for the time it is on the secondary screen, the text cursor dissapears from the login box until the mouse cursor is back on the primary screen).

Once I log into Ubuntu and am at my desktop if I go to the extreme left edge of the primary monitor, then move the the secondary monitor, the mouse cursor will appear at the extreme left edge of secondary and stop. If I take the program I am using now, and grab the title bar (which says Ubuntu Forums - Reply to Topic - Swiftfox) near the swiftfox symble, I can drag it onto the other screen until my mouse cursor stops at the edge. The part of the window that is on the secondary monitor can not be seen, but the part on the primary can, and I can drag it back to primary and it is fine. That's what is happening now.

Any ideas?

---

### Post by DarkDancer on 2006-06-23
Do you all need more info?

---

### Post by scxtt on 2006-06-23
i was able to use these 2 commands to get dual-screen working:
[indent]aticonfig --initial=dual-head --dtop=horizontal --screen-layout=right --iagp=off -v
/etc/init.d/gdm restart[/indent]2 monitors are:
[indent]1. Sceptre 20.1", max res. 1600x1200
2. ViewSonic 17", max res. 1280x1024[/indent]

i'm able to have the both working (no extra xorg.conf editing) w/ each max res. -- i use the 17" to watch TV ...

only problems right now is that Xine acts really weird (looks fullscreen for no reason, tvtime is fine - except that it drops frames more than i'd like) ...

---

### Post by DarkDancer on 2006-06-23
Ok, I tried it and got this.

> aticonfig: unrecognized option `--initial+dual-head'
aticonfig: parsing the command-line failed.


---

### Post by scxtt on 2006-06-23
typo.  (it's not "--initial+dual-head", it's "--initial=dual-head" ...

---

### Post by DarkDancer on 2006-06-23
Ok, made the change and this time I got:

> aticonfig: unrecognized option `--initial+dual-head'
aticonfig: parsing the command-line failed.


---

### Post by DarkDancer on 2006-06-24
bump

---

### Post by DarkDancer on 2006-06-26
Anyone? Any clues at all?

---

