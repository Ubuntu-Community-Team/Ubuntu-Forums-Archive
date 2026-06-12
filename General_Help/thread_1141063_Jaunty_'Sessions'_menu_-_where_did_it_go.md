---
title: "Jaunty 'Sessions' menu - where did it go?"
date: 2009-04-28
forum: General Help
---

### Post by kneewax on 2009-04-28
Hey guys, I upgraded to Jaunty x64 last week and am very impressed, no bugs, no glitches and a very smooth OS on two very different PCs.

I do have one question though, I just went to change some of the apps I have running on startup and found that my installations of Jaunty no longer have a 'Sessions' option in System Tools> Preferences>

Does anyone know if this tool has been renamed, moved or replaced, I have had a nose around some of the delightful new features, but haven't found those start up progs yet.

Cheers

---

### Post by skymera on 2009-04-28
It's renamed.. for some reason ¬_¬

System > Prefs > Startup Applications

---

### Post by kneewax on 2009-04-28
Deeeerrrr!  I probably should have worked that out!  :redface:

Thanks!

---

### Post by duffrecords on 2009-05-13
So where does it store this information?  ~/.config/autostart appears to have been renamed as well.

---

### Post by drs305 on 2009-05-13
> **duffrecords said:**
> So where does it store this information?  ~/.config/autostart appears to have been renamed as well.

The selected or created autostart apps from *Startup Applications* are listed in $HOME/.config/autostart. You don't see them there? Most are appended with ".desktop".

---

### Post by duffrecords on 2009-05-16
Oh, they're probably not there because this is a new installation and I haven't used the GUI yet.

---

