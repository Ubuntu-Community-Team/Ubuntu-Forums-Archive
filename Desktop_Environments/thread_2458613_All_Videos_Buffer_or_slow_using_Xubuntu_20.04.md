---
title: "All Videos Buffer or slow using Xubuntu 20.04"
date: 2021-02-28
forum: Desktop Environments
---

### Post by jt3222 on 2021-02-28
Hello,

I just upgraded from Xubuntu 18.04 and noticed that any video that I play is either buffering or playing very slowly.

Regards,

John...

---

### Post by T6&amp;sfpER35% on 2021-02-28
in terminal run
```
sudo add-apt-repository multiverse
```
to see if multiverse repository is enabled
then run
```
sudo apt install ubuntu-restricted-extras
```

when you get to the end user license agreement just press *tab* till it goes to *ok ,*then *enter*

---

### Post by jt3222 on 2021-02-28
Thanks friend, but I already have both of this installed.

---

### Post by ajgreeny on 2021-02-28
What hardware do you use?

Show us the output of command ***inxi -Fzx*** in terminal and please use code tags for your pasted output; see my signature below for a "How-to".

---

### Post by ajgreeny on 2021-03-01
And is this just streaming videos, eg in a browser, or all videos, even local ones playing from your hard disk?

---

### Post by jt3222 on 2021-03-01
It was mostly YouTube, but I everything started going bad after the upgrade. I noticed that I was running Ubuntu and not Xubuntu after the upgrade. I did a clean install of 20.10 and things are perfect now.

Thanks...

---

