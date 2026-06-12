---
title: "Deleted /usr/share: what can i do?"
date: 2009-06-22
forum: General Help
---

### Post by revo8778 on 2009-06-22
Basically, i unwittingly deleted the /usr/share folder with a *sudo mv -t* command thru terminal. Anyways...

1. what exactly is the folder for?
2. Can i restore it?
3 If not, can i copy that folder from the Ubuntu 9.04 cd? (I'm using Ubuntu 9.04)

---

### Post by surfed on 2009-06-22
> **revo8778 said:**
> Basically, i unwittingly deleted the /usr/share folder with a *sudo mv -t* command thru terminal. Anyways...

1. what exactly is the folder for?
2. Can i restore it?
3 If not, can i copy that folder from the Ubuntu 9.04 cd? (I'm using Ubuntu 9.04)


mv just moves a directory, so you could move it back. Remember where you moved it to? Now what where you thinking?

---

### Post by revo8778 on 2009-06-22
i think it was:

sudo mv -t docs /usr/share

i had a folder called docs that I wanted to merge with the docs folder in /usr/share. What exactly does the -t command do (the mv --help decribes it, but the description was a little cryptic)

---

### Post by surfed on 2009-06-22
> **revo8778 said:**
> i think it was:

sudo mv -t docs /usr/share

i had a folder called docs that I wanted to merge with the docs folder in /usr/share. What exactly does the -t command do (the mv --help decribes it, but the description was a little cryptic)

your usr/share is in your docs directory now. -t = target dir so you moved /usr/share to docs
it should be docs/share
do a

cd docs
sudo mv share /usr/

---

### Post by Cheesemill on 2009-06-22
Why were you playing about with the Unix Sysem Resources folder?

I'd personally not touch it unless I knew exactly what I was doing :)

---

### Post by revo8778 on 2009-06-22
Tried booting into Ubuntu, getting as far as just before the welcome screen, where it halted with an error message that was simply repeating "blank boxes" Restarted with an Ubuntu live cd and moved my misplaced share folder to it's correct location and rebooted. Now it's working fine again. Thx!

FYI I was trying to install an .rpm library (libreadline4-4.3) in order to get a Macintosh emulator (Sheepshaver) to work. in the process of moving it's files in i moved share to my desktop.

---

