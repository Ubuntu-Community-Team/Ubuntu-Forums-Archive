---
title: "[SOLVED] Wolfenstein ET installtion on a amd 64 machine"
date: 2008-03-01
forum: Gaming &amp; Leisure
---

### Post by misfito on 2008-03-01
Hello, I tried to install Wolfenstein on an AMD machine without succes , I downloaded the file from Filefront. 
The installer is called: 
  et-linux-2.55.x86.run
I went to terminal and executed the file from there after updating the system, and got this message:

```
misfito@misfito-desktop:~$ /home/misfito/Desktop/et-linux-2.55.x86.run
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.55...........................................................................................................................................................................................................................................................................................................
It is recommended to install as the super user
Please enter the root password or hit enter to continue as is
Password: 
su: Authentication failure
Sorry.
This installation doesn't support glibc-2.0 on Linux / unknown
(tried to run setup)
See http://zerowing.idsoftware.com/linux/ for troubleshooting
The setup program seems to have failed on unknown/glibc-2.0

See http://zerowing.idsoftware.com/linux/ for troubleshooting
misfito@misfito-desktop:~$ setup
bash: setup: command not found
```

I went to the place in the link above and found this:

> Setup and execution on 64 bits CPUs

If you are running a x86_64 Linux distribution with support for 32 bits x86 binaries, then the regular Quake III Arena binaries should work (your mileage may vary).

It's likely that the installer scripts will get confused though, and will refuse to install giving you an error: "This installation doesn't support glibc-2.1 on Linux / unknown". If you run the installer through the emulated 32 bits environement it should work: $ linux32 sh quake3... Or you can extract the game files manually by passing --keep on the command line when running the setup script. Once the files are unpacked, you will need to copy them manually to /usr/local/games. You probably want to have a working installation to refer to while doing this. This also applies to RTCW and ET

But the thing is that I don't know how to emulate the 32 enviroment or extract the the files manually. 

Does anyone knows how to install the game on a 64 machine?

---

### Post by Perfect Storm on 2008-03-01
```
sudo aptitude update && sudo aptitude safe-upgrade
sudo aptitude install ia32-libs
cd ~/Desktop
linux32 et-linux-2.55.x86.run
```

Should do it.

---

### Post by misfito on 2008-03-01
Well I've done all of that. :(

what I want is to know how to emulate the 32 enviroment or extract the the files manually. Do you have any ideas?

Cause i did what you said again and I got the same message. :(

---

### Post by Perfect Storm on 2008-03-01
check if following libs are installed:

libc6 libc6-i386 
libc6-dev 
libc6-dev-i386

and redo the installation again.

---

### Post by misfito on 2008-03-01
ok thax for your reply, unfortunatelly I checked and installed what I was missing from the options that you gave me. Then I try to reinstall... Nothing.... well actually I got the same message I postd before: 
> su: Authentication failure
Sorry.
This installation doesn't support glibc-2.0 on Linux / unknown
(tried to run setup)
See [http://zerowing.idsoftware.com/linux/](http://zerowing.idsoftware.com/linux/) for troubleshooting
The setup program seems to have failed on unknown/glibc-2.0

See [http://zerowing.idsoftware.com/linux/](http://zerowing.idsoftware.com/linux/) for troubleshooting
I don't know man, maybe it's something realy simple that I'm forgeting.

---

### Post by Perfect Storm on 2008-03-02
Just hold on....I'm going to download this and report back later.

---

### Post by Perfect Storm on 2008-03-02
Okay got it running.


```
cd ~/Desktop
chmod +x et-linux-2.55.x86.run
linux32 ./et-linux-2.55.x86.run --target et
```

Just ignore the error.

```
cd et
bin/Linux/x86/et.x86
```

Note, this will only play the game not installing it a fancy place. You might move it to your local Games folder (if you don't have one create one). And then make a script to launch the game.

---

### Post by misfito on 2008-03-02
Let me see if it works... :P

---

### Post by misfito on 2008-03-02
May I ask how do I do this?
> You might move it to your local Games folder (if you don't have one create one). And then make a script to launch the game.
 
Sorry for my ignorance I hope I'm not bothering you to much:???:

---

### Post by internetishere on 2008-03-02
```
wget -c http://ftp.games.skynet.be/pub/wolfenstein/et-linux-2.60.x86.run
```

[https://help.ubuntu.com/community/EnemyTerritory](https://help.ubuntu.com/community/EnemyTerritory)

---

### Post by Perfect Storm on 2008-03-02
> **misfito said:**
> May I ask how do I do this?

 
Sorry for my ignorance I hope I'm not bothering you to much:???:

Like this:
```
mkdir ~/.Games
cd ~/Desktop
mv et ~/.Games
nano ~/.Games/ET-launch.sh
```

fill in;

[b]#!/bin/bash

cd ~/.Games/et
bin/Linux/x86/et.x86[/b]

Save [ctrl]+[o]
Exit [ctrl]+[x]

next;
```
chmod +x ~/.Games/ET-launch.sh
alacarte
```

Go to the Game section in Alacarte and push the New Item button. Fill in;

**Name:** ET: Wolfenstein
**Command:** sh /home/**USERNAME**/.Games/ET-launch.sh
**Comment:** <optional>

**Icon:** ~/.Games/et/ET.xpm

---

### Post by kinematic on 2008-03-02
.

---

### Post by misfito on 2008-03-04
Thank you my friend ;) I appreciate it


But I still couldn't figure it out how to do it... Nothing happens when I double click on the icon in the game folder. The one I just created.

---

### Post by Perfect Storm on 2008-03-04
```
sh ~/.Games/ET-launch.sh
```

please post output.

---

### Post by misfito on 2008-03-05
misfito@misfito-desktop:~$ sh ~/.Games/ET-launch.sh
cd: 3: can't cd to /home/misfito/.Games/et
```
/home/misfito/.Games/ET-launch.sh: 4: bin/Linux/x86/et.x86: not found
misfito@misfito-desktop:~$ mkdir ~/.Games
mkdir: cannot create directory `/home/misfito/.Games': File exists
misfito@misfito-desktop:~$ cd ~/Desktop
misfito@misfito-desktop:~/Desktop$ mv et ~/.Games
mv: cannot stat `et': No such file or directory
misfito@misfito-desktop:~/Desktop$ nano ~/.Games/ET-launch.sh
misfito@misfito-desktop:~/Desktop$ chmod +x ~/.Games/ET-launch.sh
misfito@misfito-desktop:~/Desktop$ alacarte
misfito@misfito-desktop:~/Desktop$ sh ~/.Games/ET-launch.sh
cd: 3: can't cd to /home/misfito/.Games/et
/home/misfito/.Games/ET-launch.sh: 4: bin/Linux/x86/et.x86: not found
misfito@misfito-desktop:~/Desktop$ 

```

---

### Post by Perfect Storm on 2008-03-05
> mv: cannot stat `et': No such file or directory

This is the error. For some reason (most be under when you extracted the game) there aren't et folder (which contains the game).

---

### Post by Machiavelli on 2008-10-10
> **Artificial Intelligence said:**
> Okay got it running.


```
cd ~/Desktop
chmod +x et-linux-2.55.x86.run
linux32 ./et-linux-2.55.x86.run --target et
```

Just ignore the error.

```
cd et
bin/Linux/x86/et.x86
```



thank you! I'm now able to install Quake3 on my system =)

---

### Post by PhazzedOut on 2010-05-07
Thank you Artificial Intelligence! I got ET to work, got some knowledge off here. :D

---

