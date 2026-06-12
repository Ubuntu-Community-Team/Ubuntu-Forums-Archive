---
title: "MATE theme not applying to Gtk3 programs"
date: 2014-04-05
forum: Desktop Environments
---

### Post by jwbrase on 2014-04-05
At some point in the process either of installing MATE on my 5 year old laptop, or of upgrading MATE to 1.6, I had run into a problem with my preferred theme not being applied to Gtk3 programs. I know I somehow solved this problem because my theme currently applies system-wide on that machine. The laptop has been through Jaunty, Karmic, and Lucid with Gnome 2 and Precise with MATE 1.4 and 1.6, and I've been using pretty much the same theme through all that time.

I am currently in the process of setting up a new desktop with Trusty (I plan to phase it in and the laptop out as Trusty approaches final release). Last night I moved my ~/ across to the new machine, and in that process my theme was moved across, but for whatever reason I'm having issues again with the theme not being applied to Gtk3 programs. I can't for the life of me remember how I solved the issue last time, and Google so far has come up dry.

Does anyone have any pointers?

---

### Post by Frogs Hair on 2014-04-05
Make sure the theme is compatible , Trusty uses GTK 3.10 and older themes might not work correctly or not at all.

---

### Post by jwbrase on 2014-04-05
Is 3.10 not back-compatible with earlier versions of GTK-3? I'm fairly certain that my theme had originally been incompatible with GTK 3, as I'd run into the issue before, but I somehow managed to fix it. There's a chance that the original version of the theme may have been loaded rather than the fixed one, and that's actually what I thought had happened, so I was hoping to rediscover how I'd upconverted the theme. But if 3.10 has incompatibilities with earlier versions of 3, then I may well be SOL.

---

### Post by Frogs Hair on 2014-04-05
> Is 3.10 not back-compatible with earlier versions of GTK-3? No, some will work and others will not work at all or only partially. This is why some who make themes have given up on updating them because the themes are broken after Gnome updates. After 14.04 is released there will be updates and there are some 3.10 themes available now

---

### Post by olliemonster on 2014-05-14
Make sure that the programs in question suport gtk2 (mate) because if they don't they may not work.

---

