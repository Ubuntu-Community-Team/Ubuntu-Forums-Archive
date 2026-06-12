---
title: "Remastersys and own distro cration"
date: 2009-05-30
forum: General Help
---

### Post by j_arquimbau on 2009-05-30
Hi!

I'm trying to create my own ubuntu distro and I'm using remastersys. The problem is that I want to create a distro but with the themes and programs I've installed. e.g. I've set cairo-dock to launch at the beginning.

If I type:

# remastersys dist

I'll get a live CD with the ubuntu default theme and with no cairo-dock at the beginning. I wont have some programs I installed wine.

On the other hand, if I make a backup with

# remastersys backup

I'll get a Live CD just the way I wanted but with no installation icon on the desktop and with my user name.

I aimed to enter my Ubuntu as root and set everything as I wanted de live CD to be, but with the "# remastersys dist" command, that won't work.

So my question is: what are the files I have to modify to get a Live CD fully configurated with no predetermined user and with the installed programs I had on my normal installation? I would also like to get the installation icon on the desktop just like the "# remastersys dist" command did.

Could anybody help me with this problem?

Thank you a lot

---

### Post by billbear on 2009-05-30
You can try this script to backup your ubuntu into bootable squashfs:
[http://ubuntuforums.org/showthread.php?t=1169505](http://ubuntuforums.org/showthread.php?t=1169505)
It does not create a CD image, but you can save the backup on an external disk and boot other computers, then install the backup system.

---

### Post by j_arquimbau on 2009-05-31
I discovered the way to do it!

I had to copy some hidden files from the user folder to the /etc/skel folder

Thank you!!

---

### Post by j_arquimbau on 2009-05-31
How can I set this thread as solved???

---

