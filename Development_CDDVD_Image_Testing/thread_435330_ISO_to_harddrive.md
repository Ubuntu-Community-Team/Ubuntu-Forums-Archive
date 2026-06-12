---
title: "ISO to harddrive"
date: 2007-05-06
forum: Development CD/DVD Image Testing
---

### Post by osok the devil on 2007-05-06
i would like to know if it is possible to put the iso on slim drive and boot it off of that instead of burning it to dvd/cd to boot off of ? if so how can it be done and where to find the information. please email me. the reason why is becaues i work on a hole bunch of different computer at different times. i would like to keep my information like e-mail etc instead of entering it evertime i boot the cd/dvd???

thank you
[email]jasonshiplack@gmail.com[/email]

---

### Post by jerrylamos on 2007-05-06
Depends on what level Linux you're running.  Ubuntu Dapper 6.06 and Ubuntu Edgy 6.10 have a "persistent" mode where the CD Live stores settings, files, and even package installs on a USB pen drive.  So you take your CD and the pen drive around with you, portable system to go.  (it's busted on Feisty 7.04 fix "promised").

Plug in the pen drive.  They usually come Microsoft formatted, and may show up on the desktop as "disk".  Various sizes work, I like 1 gb or 2 gb though 512 mb might work.

System, Administration, Gnome Partition Editor
- Careful here, could wipe out your hard drive - !!

At upper right corner there's a box with a down arrow.  Click down to see if you can get a line displayed with your pen drive on it.  It may show up as /dev/sda1 or /dev/sdb1 or /dev/sdc1 or whatever.

If it looks absolutely certain you've got it, checking size, etc. then
right click  on it and unmount it.
right click on it and format choosing ext3
may take a little while
exit Gnome Partition Editor (a.k.a. GParted)
Applications, Accessories, Terminal
sudo e2label /dev/sdc1 casper-rw                     (whatever dev it is you formated)
Wait briefly, unplug the pen drive, wait a little, and replug.
It should auto mount on Desktop as casper-rw so you can see it.  It should have a lost+found icon which is part of the ext3 file system.

If all this went O.K., reboot CD Live and push F6 at the selection menu , add
persistent 
at the end of the line, example
...... quiet splash persistent
then boot up.
This can be a bit slower to boot depending on how much the pen drive has to hold.
Note you should NOT see the pen drive show up on Desktop.  When you click Places, Home Folder you'll be seamlessly looking at the home folder on the USB Pen drive.

With the USB pen drive plugged in, formatted ext3 and labelled casper-rw, and you boot CD Live F6 "persistent" you should have a version of what you wanted.

My usual observation, do not use that USB pen drive for anything else but "persistent", i.e. don't add files or delete files directly.

Cheers, Jerry:)

---

