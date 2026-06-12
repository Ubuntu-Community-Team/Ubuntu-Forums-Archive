---
title: "how do i get my aim working properly ??"
date: 2009-03-19
forum: General Help
---

### Post by ynotsk8on420@aol.com on 2009-03-19
i use aim on my other comp upstairs and down here i have this one WITH LINUX somebody sent me an im but i cannot get to my buddy list so aim is there i think but to make shur how to i do this right so it works ? also i cant watch things on websites like youtube must b the flash player can i also have help on this as well so it is fixed thank you    tony

---

### Post by jlochhead on 2009-03-19
Pidgin (installed by default) will do AIM. Just go Applications > Internet > Pidgin and add your AIM account.

The easiest way to enable flash is to grab Ubuntu Restricted Extras:

1) Applications > Terminal
2) Copy this:

sudo apt-get install ubuntu-restricted-extras

3) Edit > Past into the terminal
4) Press Enter
5) Enter your password and press enter
6) If prompted type yes
7) Restart Firefox

If you use 64 bit Ubuntu this is not an ideal solution. The ideal solution is a little harder though.

---

### Post by ynotsk8on420@aol.com on 2009-03-19
also i forgot to mention pidgen lockes up and freezes and then i hav to restart my comp umm also i would like to get my automatic updates working mind i forgot to tell you im on wierleses if this matters at all ...this software isnt it designed for you to develop it from the ground up if u kno what i mean

---

### Post by ynotsk8on420@aol.com on 2009-03-19
ok i tried to do what you said for the flash it wont work it wont let me put my password in  then wen done enough it saysE: Type 'wget' is not known on line 3 in source list /etc/apt/sources.list
E: The list of sources could not be read.

---

### Post by 3Miro on 2009-03-19
> **ynotsk8on420@aol.com said:**
> also i forgot to mention pidgen lockes up and freezes and then i hav to restart my comp umm also i would like to get my automatic updates working mind i forgot to tell you im on wierleses if this matters at all ...this software isnt it designed for you to develop it from the ground up if u kno what i mean

No way Pidgin can crash your computer so badly. Go to Terminal and start it from there (type pidgin) see if there are any error messages appearing. Also, if it crashes, you can go to System -> Administration -> System Monitor and select the pidgin process and kill it.

You can install flash without the terminal, go to Applications -> Add/Remove Programs, select all available software and search for Ubuntu restricted-extras. Flash comes with it.

Updates work the same way regardless if you are using wireless or not. I would make sure you have Internet connection and then you can go to System -> Administration -> Synaptic Package Manager and select update from it.

---

### Post by 3Miro on 2009-03-19
> **ynotsk8on420@aol.com said:**
> ok i tried to do what you said for the flash it wont work it wont let me put my password in  then wen done enough it saysE: Type 'wget' is not known on line 3 in source list /etc/apt/sources.list
E: The list of sources could not be read.

Did you mess with your source list? In the terminal, type the following:

less /etc/apt/sources.list

It would show you the content of the sources.list file, post it here, but there shouldn't be any 'wget' in it (unless you somehow put it in).

---

### Post by ynotsk8on420@aol.com on 2009-03-19
i tried the add or remove it says failed to check for installed and avaliable applications

---

### Post by ynotsk8on420@aol.com on 2009-03-19
wget is exactaly what it is

---

### Post by ynotsk8on420@aol.com on 2009-03-19
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update\

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
:

---

### Post by ynotsk8on420@aol.com on 2009-03-19
aims working but i cant see any of my buddies at all cant im or nething

---

### Post by 3Miro on 2009-03-19
wget is a program for downloading files off the Internet. Someone gave you a command to download something and looks like add a key to your source.list files (where Ubuntu is looking for programs and updates), instead the command ended up in the list. (when you don't know about a something you can type man wget in the Terminal or simply google it).

You can do this:

sudo pico /etc/apt/sources.list
 
This will let you edit the file, add a # # sign before the line that says wget. Then use Ctr + O to save the file, enter and then Ctr + X to exit. This should fix the problem.

WARNING: be careful not to change anything else in the file, you may end up causing a lot of damage to your system. In general, editing files should be done very carefully.

---

### Post by 3Miro on 2009-03-19
> **ynotsk8on420@aol.com said:**
> aims working but i cant see any of my buddies at all cant im or nething

By default pidgin shows you only the people that are on-line. You can either go to Buddies -> Show -> Off-line or (in rare cases) you may have to reenter them.

---

### Post by ynotsk8on420@aol.com on 2009-03-19
everything works except the add or remove

---

### Post by 3Miro on 2009-03-19
> **ynotsk8on420@aol.com said:**
> everything works except the add or remove

Add/Remove wouldn't work while you are updating your system. Only one package manager can work at a time. If, after updating, it still doesn't work, type:

gnome-app-install

in the Terminal and see what it says.

---

### Post by ynotsk8on420@aol.com on 2009-03-19
add and remove still dose not work i did exactly what you said to do

---

### Post by fieroboom on 2009-03-19
> **ynotsk8on420@aol.com said:**
> add and remove still dose not work i did exactly what you said to do

Run this command and copy/paste your updated /etc/apt/sources.list please.
```
cat /etc/apt/sources.list
```
:D
-Paul

---

