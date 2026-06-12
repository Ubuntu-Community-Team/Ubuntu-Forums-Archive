---
title: "volume..."
date: 2009-02-08
forum: General Help
---

### Post by LoneWolfJack on 2009-02-08
this issue is not at all limited to ubuntu/linux... but why does every stupid program have to have its own volume toggle? I feel like I'm spending half the day moving volume bars back and forth.

is there any program that will attach to ALSA or so and normalize all volumes to 98% so I only have to adjust the volume in one place?

as a second-best solution I'd go with a program that can normalize mp3 and flv-files.

any ideas?

---

### Post by hwttdz on 2009-02-09
To normalize mp3 files, you can use mp3gain.  It puts volume information in the tags without editing the file.  You also need to make sure your music player is using the tag information.  For rhythmbox, in gconf-editor I believe it's apps->rhythmbox->use gain tags or somesuch.  I found the automagic to be not the best and the default volume ok, I supposed you'd get best results if you just did it for each file by ear, but that would take time.  And there's something satisfying about doing mp3gain -options *.  

note: to turn spaces into underscores in filenames (useful)
rename 's/ /_/g' *.mp3

---

### Post by sujoy on 2009-02-09
setup xbindkeys with amixer (or your mixer of choice) and then you can use those keybindings everywhere and forget about the individual volume controls

---

