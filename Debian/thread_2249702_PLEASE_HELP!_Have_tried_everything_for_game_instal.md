---
title: "PLEASE HELP! Have tried everything for game installation..."
date: 2014-10-24
forum: Debian
---

### Post by Off_Ghetz on 2014-10-24
I don't know very much about Linux except some very basic terminal commands, so if some of you gents could help me please without using jargon or abbreviations or acronyms, I would be most obliged.                                                 I've joined the forum just to ask for help with this problem, as I've taken about 2 hours attempting to solve it, and with my limited knowledge I can only do so much. I won't go into detail about what I tried, because I don't even remember, because most of the time I had no clue what I was doing. Suffice to say, whatever I did, I was not able to overcome my initial very basic problem. I will therefore just start at the beginning and state it below.
SYSTEM: Debian 3.10.5-1, i386, XFCE4 
PROBLEM: I am attempting to download and install and play the Linux version of Legend of Zelda: Return of the Hylian.
1. Downloaded the Linux version from this site: [http://www.zeldaroth.fr/us/dlroth.php2](http://www.zeldaroth.fr/us/dlroth.php2). The file downloaded to the /home/user/Downloads folder, and was entitled "ZeldaROTH_US.tar.gz". 
2. I right-clicked the file, "Extract Here". The extracted folder is called "ZeldaROTH_US". 
3. Within the extracted folder, among other things, is an executable file also entitled "ZeldaROTH_US". 
4. I made sure I had executive permissions for the folder and all files therein, by Right-click > "Properties" > Permissions.
5. I attempted to double-click on the executable file. I attempted to Right-click > "Execute" the executable file. Nothing happened in either instance.
6. I appealed to the Terminal for help: 
cd /home/user/Downloads/ZeldaROTH_US
./ZeldaROTH_US
It replied thusly:
./ZeldaROTH_US: error while loading shared libraries: libSDL_gfx.so.4: cannot open shared object file: No such file or directory
Now, my friends, I appeal to you for help.

---

### Post by Off_Ghetz on 2014-10-24
BY THE WAY: I was forced to write out my message in HTML because for some reason the forum formats my final post as is I had never pressed "Enter", running the lines together. If anyone can help me with this issue as well...?

---

### Post by Off_Ghetz on 2014-10-24
I don't know very much about Linux except some very basic terminal commands, so if some of you gents could help me please without using jargon or abbreviations or acronyms, I would be most obliged.I've joined the forum just to ask for help with this problem, as I've taken about 2 hours attempting to solve it, and with my limited knowledge I can only do so much. I won't go into detail about what I tried, because I don't even remember, because most of the time I had no clue what I was doing. Suffice to say, whatever I did, I was not able to overcome my initial very basic problem. I will therefore just start at the beginning and state it below.SYSTEM:Debian 3.10.5-1i386XFCE4 PROBLEM: I am attempting to download and install and play the Linux version of Legend of Zelda: Return of the Hylian.1. Downloaded the Linux version from this site: [http://www.zeldaroth.fr/us/dlroth.php2](http://www.zeldaroth.fr/us/dlroth.php2). The file downloaded to the /home/user/Downloads folder, and was entitled "ZeldaROTH_US.tar.gz".2. I right-clicked the file, "Extract Here". The extracted folder is called "ZeldaROTH_US".3. Within the extracted folder, among other things, is an executable file also entitled "ZeldaROTH_US".4. I made sure I had executive permissions for the folder and all files therein, by Right-click > "Properties" > Permissions.5. I attempted to double-click on the executable file. I attempted to Right-click > "Execute" the executable file. Nothing happened in either instance.6. I appealed to the Terminal for help: > cd /home/user/Downloads/ZeldaROTH_US./ZeldaROTH_USIt replied thusly:> ./ZeldaROTH_US: error while loading shared libraries: libSDL_gfx.so.4: cannot open shared object file: No such file or directoryAnd now, my friends, I appeal to you for help.

---

### Post by Bucky Ball on 2014-10-24
*Thread moved to **Debian**.*

Welcome. ***Installations & Upgrades*** is for installing and/or upgrading the OS, not apps. 

Please keep in mind that there are many females, both staff and members, on the forums. Please simply address your posts to the community as you did here:

> **Off_Ghetz said:**
> And now, my friends, I appeal to you for help.

... rather than to the 'gents'. Thanks and good luck. ;)

---

### Post by MikeCyber on 2014-10-24
Without reading all there's a libsdl-gfx package in synaptic on Ubuntu.

---

### Post by Bucky Ball on 2014-10-24
> **MikeCyber said:**
> Without reading all there's a libsdl-gfx package in synaptic on Ubuntu.

Which means you will find it in Software Centre if you are not using Synaptics (as far as I know, Synaptics is not installed by default in Ubuntu).

PS: I have just moved this again to ***Debian*** as I noticed you are not using Ubuntu. While you are welcome to post in this section of the forum you would have more luck posting in a Debian forum rather than a Ubuntu one. They are not the same.

---

### Post by /ADM on 2014-10-24
If you know some commands (rather than navigating the GUI) you could run:

'sudo apt-get install libsdl-gfx'

I always found the GUI's to be rather slow (and I dislike waiting) :)

---

