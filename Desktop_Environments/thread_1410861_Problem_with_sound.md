---
title: "Problem with sound"
date: 2010-02-19
forum: Desktop Environments
---

### Post by argos3016 on 2010-02-19
I boot in text mode. I can't hear anything with rythmbox or cmus (when I switch to X mode).I put in grub.cfg the "text" boot option of the kernel, because I was want to disable GDM. Maybe is that.
Sorry for my english.

---

### Post by MooPi on 2010-02-19
I'm not certain what is not starting but I had a similar issue. I was using startx  from the command prompt into an Openbox environment. My alsa sound would not function unless I used a root terminal. So I suppose that you'll need to append your xinitrc file. here is a link: [https://wiki.ubuntu.com/CustomXSession](https://wiki.ubuntu.com/CustomXSession)

---

### Post by argos3016 on 2010-02-19
Doesn't work.
The thing that i want is switch to X mode only typing xinit or startx.(with sound)

---

