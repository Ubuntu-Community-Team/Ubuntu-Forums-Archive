---
title: "Questions about Grub"
date: 2009-04-21
forum: General Help
---

### Post by jfinner1 on 2009-04-21
I hope I'm posting this in the right place. I had a few questions about the Grub screen, and I was hoping someone could clear them up for me. First off, I have my computer dual booted with Jaunty and XP. But my Grub menu has 8 different options, and I was wondering why there were so many, and what they were. Here are all the options I get:

Ubuntu 9.04, kernal 2.6.28-11-generic
Ubuntu 9.04, kernal 2.6.28-11-generic (recovery)
Ubuntu 9.04, kernal 2.6.27-11-generic
Ubuntu 9.04, kernal 2.6.27-11-generic (recovery)
Ubuntu 9.04, kernal 2.6.24-23-generic
Ubuntu 9.04, kernal 2.6.24-23-generic (recovery)
Ubuntu 9.04, memtest86+
Windows XP

Next question. Is there any way to get rid of some of those options, or to rename them? I would like to get that list a bit shorter, and smaller, more like this:

Ubuntu Jaunty
Ubuntu Jaunty (recovery)
Ubuntu memtest (if I need it)
Windows XP

Last question. I've heard that you can kinda customize the look of the Grub screen, like put up a background or something. Can someone point me to a good tutorial that's up-to-date? All the answers are greatly appreciated.

---

### Post by hyperdude111 on 2009-04-21
```
sudo gedit /boot/grub/menu.lst
```

Go to the bottom of the page and filter through the options. Rename as you want.

The extra ubuntu options are there because you updated your kernel from the update manager and incase this goes wrong the old kernel version is added to your grub to allow you to use the old one.

---

