---
title: "ndiswrapper de los muertos"
date: 2006-04-24
forum: Desktop Environments
---

### Post by Banter on 2006-04-24
Hey, i'm a linux noob. so, sorry for not knowing much

I'm trying to follow [this]("http://ubuntuforums.org/showthread.php?t=104539&highlight=compile+ndiswrapper+source") tutorial on installing ndiswrapper. I don't have a connection to the net thru linux, so i have do download a whole bunch of dependencies manually. anyway, i get a whole bunch of em downloaded, then i try to start the tutorial . . .

```
sudo apt-get install linux-headers-$(uname -r)
``` causes . . . 

```
linux-headers-2.6.12-9-386 is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  build-essential: Depends: g++ (>= 3:3.3) but it is not going to be installed
  gcc: Depends: gcc-4.0 (>= 4.0.3-1) but it is not going to be installed
  gcc-3.4: Depends: cpp-3.4 (< 3.4.5) but 3.4.6-1 is to be installed
  gij-4.0: Depends: gcc-4.0-base (= 4.0.1-4ubuntu9) but 4.0.3-1 is to be installed
  libc6-dev: Depends: libc6 (= 2.3.2.ds1-22sarge3) but 2.3.5-1ubuntu12 is to be installed
  libgcj6: Depends: gcc-4.0-base (= 4.0.1-4ubuntu9) but 4.0.3-1 is to be installed
  libstdc++6: Depends: gcc-4.0-base (= 4.0.1-4ubuntu9) but 4.0.3-1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

any help with this would be greatly appreciated!

---

### Post by az on 2006-04-24
What card do you have?  It usualy is not neccessary to recompile ndiswrapper, just use the most recent .inf file - the one that came with your device may be too old.

---

### Post by Banter on 2006-04-24
@ azz

Thanks for the reply!

I have a D-link airplus card
(G DWL-G510 Wireless PCI Adapter rev. b)

I'm really a noobie at linux. I just downloaded the os a few days ago and installed it dual boot with xp pro. That was hell in and of itself! I actually managed to loose some homework over it :-( Enough with the sob story tho, i do have some questions . . .

So, i found this .inf file: NetA3AB
I found it here: [ftp://ftp.dlink.com/Wireless/dwlg520_revB/Drivers](ftp://ftp.dlink.com/Wireless/dwlg520_revB/Drivers)
(actually, some lady on a microsoft site found it there, anyway . . .)

How would i implement this .inf file? Is it even the right one!?

Thanks, man.

---

### Post by Banter on 2006-04-25
Hey azz,

I had to reinstall ubuntu. So im back to square one with this. I'm going to start another threat with my new problem. dang.

---

