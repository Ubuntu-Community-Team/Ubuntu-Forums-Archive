---
title: "Shared libraries error with Return To Castle Wolfenstein"
date: 2007-08-01
forum: Gaming &amp; Leisure
---

### Post by kr0n1x on 2007-08-01
Hi, i have read this wiki to install the game (I've platinum edition): [https://help.ubuntu.com/community/Games/Native/ReturnToCastleWolfenstein](https://help.ubuntu.com/community/Games/Native/ReturnToCastleWolfenstein)

i installed and patched correctly...

infact "wolfsp" works fine, but when i try to launch the multiplayer (wolfmp) i receive this error:
```
pasquale@pasquale-desktop:~$ wolfmp
./wolf.x86: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory
pasquale@pasquale-desktop:~$ 

```

why?

I've installed libstdc++5, libstdc++6 and libstdc++6-4.1-dev for now...

attention: i'm talking about RTCW (return to castle wolfenstein, the game NON-FREE, you need to buy it for play in multiplayer), not about W:ET (wolfenstein enemy territory, only multiplayer game, and FREE).

i hope you have all info you need to help me :) if you need more...ask me :D

thanks, bye

ps: sorry for my bad english

---

### Post by PaulFr on 2007-08-01
Does ```
sudo apt-get install libstdc++2.10-glibc2.2
``` help ?

---

### Post by kr0n1x on 2007-08-02
> **PaulFr said:**
> Does ```
sudo apt-get install libstdc++2.10-glibc2.2
``` help ?

yes, now works :)

thanks, bye! :D

---

### Post by KingHanco on 2007-08-19
Thanks.

wolfded.x86 won't run. What is this?

---

### Post by PaulFr on 2007-08-19
To find where a file is being executed from, use ```
which <file>
```For example, **which ping** returns **/bin/ping**. To guess at what a file is, you can use the command ```
file <path_to_file>
``` For example, **file /bin/ping** returns **/bin/ping: setuid ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.0, dynamically linked (uses shared libs), stripped**. If this returns messages like **ELF 32-bit LSB executable** then the <path_to_file> is a recognized executable.

Then I would suggest you run <path_to_file> manually from a terminal and observe the error messages. Those should give you an idea of why the command is not running.

---

### Post by Sockerdrickan on 2007-08-19
> **KingHanco said:**
> Thanks.

wolfded.x86 won't run. What is this?
You just started dedicated server in memory

---

### Post by kr0n1x on 2007-08-19
wolfded is for host a server game, isn't for a normal multiplayer match i think..

---

### Post by Sockerdrickan on 2007-08-19
Then why ask?

---

### Post by KingHanco on 2007-08-19
I not going to worry about that file.

---

### Post by kr0n1x on 2008-02-09
> **PaulFr said:**
> Does ```
sudo apt-get install libstdc++2.10-glibc2.2
``` help ?

i'm in Ubuntu Gutsy 64 bit now, and i can't find this package in repositories :(

where i can find it? there isn't in getdeb.net

i need it to play wolfmp

---

### Post by Perfect Storm on 2008-02-09
You need to install 32-bit libs for making Return To Castle Wolfenstein work.

---

### Post by kr0n1x on 2008-02-09
> **Artificial Intelligence said:**
> You need to install 32-bit libs for making Return To Castle Wolfenstein work.

good, what is the file name? it is in synaptic?

this isn't the first 32bit game that i play.. quake 3 arena works well... maybe i've already the package that you are talking about

---

### Post by Perfect Storm on 2008-02-09
You can't do that - but check here: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by kr0n1x on 2008-02-09
> **Artificial Intelligence said:**
> You can't do that - but check here: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

```
pasquale@conroe6300:~$ getlibs /usr/local/bin/wolfmp
Cannot determine the dependencies required by this program, it may be a script:
If this program needs a 32-bit library use:
getlibs -l i386librarytoinstall.so
If this program needs a 64-bit library use:
getlibs -64l amd64librarytoinstall.so

pasquale@conroe6300:~$ getlibs -p libstdc++2.10-glibc2.2
The following i386 packages will be installed: libstdc++2.10-glibc2.2
Continue [Y/n]? y
W: Impossibile trovare il pacchetto libstdc++2.10-glibc2.2
E: Nessun pacchetto trovato
Make sure you have all repositories enabled and updated
No packages to install

pasquale@conroe6300:~$ getlibs -l libstdc++-3-libc6.2-2-2.10.0.so libstdc++-libc6.2-2.so.3
libstdc++-3-libc6.2-2-2.10.0.so: libstdc++2.10-glibc2.2
libstdc++-libc6.2-2.so.3: libstdc++2.10-glibc2.2
The following i386 packages will be installed:
libstdc++2.10-glibc2.2
Continue [Y/n]? y
W: Impossibile trovare il pacchetto libstdc++2.10-glibc2.2
E: Nessun pacchetto trovato
Make sure you have all repositories enabled and updated
No packages to install
pasquale@conroe6300:~$
```

how you solved the problem? or you don't play rtcw?
i'm trying bad commands?

---

### Post by Cappy on 2008-02-09
That's odd. That library doesn't even exist for 64-bit. That's why it doesn't work =(

Oh well you can use
> sudo getlibs -w mirrors.kernel.org/ubuntu/pool/universe/g/gcc-2.95/libstdc++2.10-glibc2.2_2.95.4-24_i386.deb

I looked up the package on [http://packages.ubuntu.com](http://packages.ubuntu.com) and found the download link

---

### Post by kr0n1x on 2008-02-09
> **Cappy said:**
> That's odd. That library doesn't even exist for 64-bit. That's why it doesn't work =(

Oh well you can use


I looked up the package on [http://packages.ubuntu.com](http://packages.ubuntu.com) and found the download link

that worked well! thanks :D

---

### Post by Perfect Storm on 2008-02-09
Strange...I better report this so it can be corrected in Hardy.

---

### Post by otchie1 on 2008-04-05
> **Artificial Intelligence said:**
> Strange...I better report this so it can be corrected in Hardy.

As of today it wasn't.

```
wget mirrors.kernel.org/ubuntu/pool/universe/g/gcc-2.95/libstdc++2.10-glibc2.2_2.95.4-24_i386.deb
sudo dpkg --install wget libstdc++2.10-glibc2.2_2.95.4-24_i386.deb

```

works nicely though, thanks

---

### Post by BrEeZiE on 2008-04-27
i am having the same problem since i upgraded to ubuntu 8.04

"sudo apt-get install libstdc++2.10-glibc2.2" doesnt help :(

---

### Post by kr0n1x on 2008-04-27
> **BrEeZiE said:**
> i am having the same problem since i upgraded to ubuntu 8.04

"sudo apt-get install libstdc++2.10-glibc2.2" doesnt help :(

i noticed that the package doesn't exist in Xubuntu 8.04 repositories

---

### Post by Perfect Storm on 2008-04-27
> **kr0n1x said:**
> i noticed that the package doesn't exist in Xubuntu 8.04 repositories

Well, Xubuntu 8.04 repositories is the same as K/U/Go/Edu-buntu repositories.

People can grab it, which is shown in post 18

---

### Post by Cappy on 2008-04-27
> **Artificial Intelligence said:**
> Well, Xubuntu 8.04 repositories is the same as K/U/Go/Edu-buntu repositories.

People can grab it, which is shown in post 18

You spoil all my fun A.I.. Stop reading the thread!

---

### Post by Perfect Storm on 2008-04-27
> **Cappy said:**
> You spoil all my fun A.I.. Stop reading the thread!

:lolflag:

sorry, it's my job :popcorn:

---

### Post by BrEeZiE on 2008-04-27
> **Artificial Intelligence said:**
> Well, Xubuntu 8.04 repositories is the same as K/U/Go/Edu-buntu repositories.

People can grab it, which is shown in post 18

thanks ^ post #18 solved my problem

---

### Post by antiflag1980 on 2011-11-02
libstdc++2.10-glibc2.2_2.95.4-24_i386 I can no longer find this package anywhere.

---

### Post by Perfect Storm on 2011-11-02
This thread is over 3 years old and so is the information.

Thread closed.

---

