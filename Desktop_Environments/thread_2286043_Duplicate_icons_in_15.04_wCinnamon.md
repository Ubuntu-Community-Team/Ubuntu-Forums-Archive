---
title: "Duplicate icons in 15.04 w/Cinnamon"
date: 2015-07-09
forum: Desktop Environments
---

### Post by treii28 on 2015-07-09
I recently upgraded to 15.04 then re-installed cinnamon from the default repository. Now whenever I place a file of any kind in the ~/Desktop folder, the icon appears twice. One of the icons is selectable/movable/deletable, and the other seems to drop starting from the top left (under the default icons if any) tiled and cannot be selected. Removing the file removes both icons. Does anyone know how to fix this?

---

### Post by adlerhn on 2015-08-18
You should report this as a defect: [https://github.com/linuxmint/Cinnamon/issues/](https://github.com/linuxmint/Cinnamon/issues/)

---

### Post by adlerhn on 2015-08-18
Actually, there is already a defect that seems to be similar to what you are reporting: [https://github.com/linuxmint/Cinnamon/issues/4512](https://github.com/linuxmint/Cinnamon/issues/4512)

Maybe you should add your case there.

---

### Post by exit02 on 2015-08-18
"pkill nautilus" appears to work-around the problem for me in the short term.

---

### Post by leycec-3 on 2015-10-29
exit02 helpfully provided a longer-term solution in this [Cinnamon issues thread]("https://github.com/linuxmint/Cinnamon/issues/4512#issuecomment-132350100"):

[FONT=courier new]gsettings set org.gnome.desktop.background show-desktop-icons false[/FONT]

Running the above command in a terminal window both *immediately* and *permanently *fixed this issue on my system. With any volunteer luck, Cinnamon developers will begin providing sane defaults under Ubuntu. Until that glory day, the above should suffice.

---

### Post by jcmcnch on 2016-01-06
Thanks for posting, fixed it for me too! I was also having this weird problem where the desktop background would revert to the gnome desktop, which for some reason I had set to a picture of a duck drinking water out of a puddle. So it was rather infuriating to find my desktop icons duplicated and this duck staring at me. Thanks for saving my sanity!

---

### Post by Mike_DeMattia on 2016-02-02
Thanks for posting this!  Fixed the exact issue I was having with Cinnamon in 14.04!

Cheers!

---

### Post by Paul5mith on 2016-03-04
This issue can also be fixed by removing Nautilus since Cinnamon uses Nemo instead.

---

### Post by goofprog on 2016-03-06
Actually, I got this issue when I installed an alternate window manager to unity.  The window managers were sharing resources somehow.  I did reverted back to unity by removing cinnamon.

---

### Post by oldos2er on 2016-03-07
Since this thread concerns a version of Ubuntu which is no longer supported (15.04), closing.

---

