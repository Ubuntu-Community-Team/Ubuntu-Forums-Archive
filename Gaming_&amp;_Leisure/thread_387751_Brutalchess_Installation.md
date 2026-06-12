---
title: "Brutalchess Installation"
date: 2007-03-18
forum: Gaming &amp; Leisure
---

### Post by Virgo53 on 2007-03-18
I downloaded Brutalchess to try out, but so far haven't been able to install it.
It's been unzipped into a temporary folder as of now.
The needed dependencies libxmu-dev and libxi-dev are installed according to
Synpatic. I'm a noob to Ubuntu and have no experience at compiling, so any help
will be most appreciated- thanks!

---

### Post by MonkeyBoy on 2007-03-19
It's not the most up to date version but if you have your repositories open the 0.3 version is there.  if you type "sudo apt-get install brutalchess" then just type "brutalchess" to play.

---

### Post by glotz on 2007-03-19
The basic drill is to
unzip the tarball
cd to the folder
./configure
make
sudo make install

Usually configure will give you some errors you'll need to address.

---

### Post by Virgo53 on 2007-03-19
Yes- I think I'm in way over my head on this! Thanks anyway!

---

