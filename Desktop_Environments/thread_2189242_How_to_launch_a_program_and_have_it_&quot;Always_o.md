---
title: "How to launch a program and have it &quot;Always on Top&quot;?"
date: 2013-11-21
forum: Desktop Environments
---

### Post by coeg2 on 2013-11-21
I love that I can right click on any window and tell it to always stay on top. However, some programs that i use, i always keep on top, no exceptions. I'm wondering if there is a way to make these programs launch with that option enabled? I am using Xubuntu 12.04. An example would be using speedcrunch. What would i have to type in the terminal to make it launch as always on top? I would then like to tweak the launcher for the program.

---

### Post by deadflowr on 2013-11-21
Though I'm sure there is a command line instruction to do this, I don't know it.
So for this I would use compizconfig-settings-manager, and go to window rules.
There you can add entries for such things like above, below sticky and other fun stuff.
Simply grab the window and add the entry to the ones you want.

---

### Post by vasa1 on 2013-11-21
> **deadflowr said:**
> Though I'm sure there is a command line instruction to do this, I don't know it.
So for this I would use compizconfig-settings-manager, and go to window rules.
There you can add entries for such things like above, below sticky and other fun stuff.
Simply grab the window and add the entry to the ones you want.
Xubuntu does not come with compiz. Compiz *may* slow a machine down.

---

### Post by Toz on 2013-11-21
>  I'm wondering if there is a way to make these programs launch with that option enabled?Devilspie will do that for you.

Resources:
- [https://help.ubuntu.com/community/Devilspie]("https://help.ubuntu.com/community/Devilspie")
- [http://www.foosel.org/linux/devilspie]("http://www.foosel.org/linux/devilspie") (see the Skype example)

No need to tweak the launcher as devilspie will apply the rules no matter how the application is launched.

---

### Post by deadflowr on 2013-11-21
> **vasa1 said:**
> Xubuntu does not come with compiz. Compiz *may* slow a machine down.

Yeah, somehow the word xubuntu wasn't read on my screen.(or my mind rejected it's existence)

Devil's pie is the app you want.

---

