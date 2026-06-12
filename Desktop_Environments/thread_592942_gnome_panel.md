---
title: "gnome panel"
date: 2007-10-26
forum: Desktop Environments
---

### Post by monoufo on 2007-10-26
I did a fresh install of gutsy last night, because i was experiencing problems.  My flash is working now.  I still can't use sun-java-6, but the icedtea OS java JRE seems to be working so far.  I'm in the middle of tweaking appearences. my VLC and stuff is fixed to.

I use AWN as a complete replacement for gnome-panel.  The repository version is working this time, so I'm using that.  I used to need to build from source.  I even found a calendar app, the only thing missing before.  How, i can't seem to get rid of my top gnome panel.  I try setting it to trash in the sessions list, but it always comes back.  How do i make gnome-panel not start up?  I still have plenty of things to tweak. gutsy is great if i can keep it stable.

---

### Post by carlos1992 on 2007-10-28
I did something similar i remove the one down and i just right-click on the panel and click delete this panel, and that was it.:lolflag:

---

### Post by monoufo on 2007-10-28
that's how to remove them all except the last one.  go ahead, try and delete your last one.

---

### Post by hamster_billy on 2007-10-29
I've not actually tried this to see if it'll work, as I don't want to delete my panels, but it looks like the thing to do. Open the Sessions dialogue (menu > system > preferences > sessions) and go to the Current Session tab. You'll see that gnome-panel is set to restart (in my box, and I assume this is default, gnome-panel, gnome-cups-icon, nautilus and vino-session are set to restart). Change it to Normal (or Trash or Settings - I'm not sure what effect these have) and you should be able to close it without it reopening.

---

### Post by monoufo on 2007-10-31
That worked before, but now it's only half the solution.  You have to chose remove, to get it to close right away.  Then, you have to go to the next tab and hit the save button, or it won't remember the change.  that's kinda gay.  I hope they fix it. It should automatically save, or at least ask. It's better now.

> **hamster_billy said:**
> I've not actually tried this to see if it'll work, as I don't want to delete my panels, but it looks like the thing to do. Open the Sessions dialogue (menu > system > preferences > sessions) and go to the Current Session tab. You'll see that gnome-panel is set to restart (in my box, and I assume this is default, gnome-panel, gnome-cups-icon, nautilus and vino-session are set to restart). Change it to Normal (or Trash or Settings - I'm not sure what effect these have) and you should be able to close it without it reopening.

---

