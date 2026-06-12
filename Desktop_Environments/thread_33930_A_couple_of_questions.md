---
title: "A couple of questions"
date: 2005-05-12
forum: Desktop Environments
---

### Post by ramtap on 2005-05-12
I need to drag and drop the latest eagle usb driver source to /usr/local/src but when I try to, I'm given a warning I don't not have permission to write to that folder. 

How do I get around this? 

One other question, how do I cd to the cdrom at the terminal?

Thanks

---

### Post by lepetitalbert on 2005-05-12
hello,

start nautilus as root 

sudo nautilus

or use cp in prompt

sudo cp -R /hereareyourfiles/ * /usr/local/src/

to find the cdrom

cat /etc/fstab

Have a nice day.

---

### Post by ramtap on 2005-05-12
Thanks! that did the trick.

---

