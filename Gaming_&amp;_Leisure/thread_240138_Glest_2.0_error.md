---
title: "Glest 2.0 error"
date: 2006-08-20
forum: Gaming &amp; Leisure
---

### Post by Icon41 on 2006-08-20
I tried installing glest, it looks pretty nice and i installed it and no errors. I tried to run it and it didnt come up, so i tried it with terminal and it gave me 

billy@billy-desktop:~$ glest
./glest.bin: error while loading shared libraries: libopenal.so.0: cannot open shared object file: No such file or directory

---

### Post by Hairy_Palms on 2006-08-20
install libopenal0 
and libopenal0a from synaptic

or 

sudo apt-get install libopenal0 libopenal0a

---

### Post by Icon41 on 2006-08-20
option 1 is wierd, Synapic will not even open, when i look at the task bar at the bottom it shows up for a milisecond and closes.

and option 2 i got this
billy@billy-desktop:~$ sudo apt-get install libopenal0 libopenal0a
Password:
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libopenal0a: Conflicts: libopenal0 but 0.2005080600-2.1build2 is to be installed
E: Broken packages






also it says i need to update but when i click install updates, it says it installs them for a second or two and then it brings me back and there still there and not installed.

---

### Post by Hairy_Palms on 2006-08-20
it sounds like you have some strange repos added, post the contents of your /etc/apt/sources.list here for us to look at

---

