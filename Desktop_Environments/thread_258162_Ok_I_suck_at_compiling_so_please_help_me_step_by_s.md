---
title: "Ok I suck at compiling so please help me step by step..."
date: 2006-09-15
forum: Desktop Environments
---

### Post by maddbaron on 2006-09-15
I downloaded "Konverter" as a tgz. Its the graphical frontend gui for mencoder. I downloaded it to a folder called mozillabaron which is in in my home folder. how do i compile it so i can use it?

i've tried compiling tgz before and i can never get it to work.

can someone tell me ztep by step how to get it from my mozillabaron folder into whatever other folder it should be in so it can be used from the start menu or terminal.

Thank you in advance.

---

### Post by gborzi on 2006-09-15
Perhaps you have not installed the development libraries to compile this program. The compilation is quite simple:
1) install kdelibs4-dev and libxine-dev > sudo apt-get install kdelibs4-dev libxine-dev
2) extract the archive, i.e. > tar -xzf konverter-0.93.tar.gz
3) change to the new directory > cd konverter
4) compile > make
5) install > sudo make install
6) if you don't like it > sudo make uninstall
I hope this helps.

---

### Post by aysiu on 2006-09-15
They have a precompiled .deb for it. Have you tried that? ```
wget -c http://www.kraus.tk/projects/konverter/packages/konverter_0.93-1_i386.deb
sudo dpkg -i konverter_0.93-1_i386.deb
```

---

### Post by maddbaron on 2006-09-15
> **aysiu said:**
> They have a precompiled .deb for it. Have you tried that? ```
wget -c http://www.kraus.tk/projects/konverter/packages/konverter_0.93-1_i386.deb
sudo dpkg -i konverter_0.93-1_i386.deb
```


THANK YOU!!!!!!!!!

if this works i can dump xpo for good on my laptop!

i tried make file and all that no idea what i was doing, i am a alittle gunshy after trying to compile another program and my laptop shutting down and me getting kernal panic afterwards...now i pretty much have everything i need just need to learn how to make my webcam work and my flash drive and i am set....


THANK YOUUUUUUUUUUU again!!!!!!!!!!!

---

### Post by aysiu on 2006-09-15
If that doesn't work, they have several other binaries worth a shot.

Two other .deb files--I think one's for Debian Sid.

There are also weird scenarios where an *alien*ed .rpm actually has better compatibility with Ubuntu than a .deb

Do you know how to install .rpm files?

---

### Post by maddbaron on 2006-09-15
> **aysiu said:**
> If that doesn't work, they have several other binaries worth a shot.

Two other .deb files--I think one's for Debian Sid.

There are also weird scenarios where an *alien*ed .rpm actually has better compatibility with Ubuntu than a .deb

Do you know how to install .rpm files?

nah i read i have to change them to .deb files..but the thing u gave me works perfect but there is no wmv/rmvb file option...i want to convert avi's into either one of those formats since they are smaller than avi's and save me much more space...are mpeg-4 files smaller than avi's? divx? i have been hunting for months for a video converter lol....i want to leave windows so bad, i have found the use of kubuntu so much nicer than xp smoother and everything and treats me hardware nioer too lol...but i need a way to convert avi's to wmv or rmvb files...maybe even .mov files... i keep looking for the command line for those 2 or 3 things but everything is so complicated lvac and -i's...very confusing....anyways i am rambling sorry for that...i will keep googling for a way unless u know the codes to convert to wmv or rmvb or even mov ?

---

