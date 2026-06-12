---
title: "Need to backup my files"
date: 2006-07-19
forum: Desktop Environments
---

### Post by Razer on 2006-07-19
Hey

I'm going to format the Ubuntu and Ubuntu Home partitions on my harddrive and I was wondering what I will have to do in order to backup all my system files so that after I reinstall Ubuntu, all the settings such as my XGL and other programs will be present. Please tell me what programs I will have to use and what to do. Thanks!

---

### Post by llamakc on 2006-07-19
If you want things exactly as they are why do you want to format the hard drive? Do you need to resize a partition instead?

You would want to copy your /etc/apt/sources.list, /etc/X11/xorg.conf, /etc/gdm/gdm.conf-custom files offsite, like email them to yourself somewhere.

Next you'd want a list of applications currently installed. You can get this from the command line (CLI) in a terminal with:

from: [http://216.239.51.104/search?q=cache:9onMmVzpJ_YJ:www.debian.org/doc/manuals/reference/ch-package.en.html+dpkg+migrate+package+list+from+one+machine&hl=en&gl=us&ct=clnk&cd=3](http://216.239.51.104/search?q=cache:9onMmVzpJ_YJ:www.debian.org/doc/manuals/reference/ch-package.en.html+dpkg+migrate+package+list+from+one+machine&hl=en&gl=us&ct=clnk&cd=3)
**6.4.9 Record/copy system configuration**

   To make a local copy of the **package** selection states:  
     $ **dpkg** --get-selections "*" >myselections   # or use \*
  "*" makes myselections include **package** entries for "purge" too.  
 You can transfer this file to another computer, and install it there with:  
     # dselect update
     # **dpkg** --set-selections <myselections
     # apt-get -u dselect-upgrade    # or dselect install


But once more, why?

---

### Post by SamZor on 2006-07-19
[http://www.ubuntuforums.org/showthread.php?t=35087&highlight=howto+complete+system+backup](http://www.ubuntuforums.org/showthread.php?t=35087&highlight=howto+complete+system+backup)

i would just use tar and a variation of what is posted in the above guide. There is no external program needed, you already have the tools :)

---

### Post by Razer on 2006-07-19
I have two harddrives and one of them is an IDE 160gig and for some reason my dad attached a pci card to the it. Now my dad needs it for an ATA harddrive so as soon as he takes it off, Ubuntu won't load. So now I want to just install Ubuntu without the PCI card. If there is a way for Ubuntu to recognize the harddrive and load that would be helpful.

---

### Post by Dubbayoo on 2006-07-19
I would use rsync

---

### Post by ardchoille on 2006-07-20
Here is my backup scheme:

1) Create a new directory to hold the backups, I did sudo mkdir /home/backups

2) I use these commands in a root script to create the backups:

```

cd /home
tar cjf /home/backups/$(date +%Y%m%d)-backups.tar.bz2 username

```

The "username" would be your username (the user of whom you want backups made). The backup will end up with a file name like "20060718-backups.tar.bz2" showing the year, month, day, the word "backups" and the extension "tar.bz2".

You can copy the backups to a new drive or machine, or you can burn them to CD/DVD.

Hope this helps.

---

