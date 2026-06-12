---
title: "Cant seem to install instant messengers"
date: 2006-07-25
forum: Desktop Environments
---

### Post by Luthy on 2006-07-25
I want to install the AIM instant messenger and the Yahoo instant messenger for Linux but cat seem too. Anyone else have this prob? i know i have Gaim but would not want to use it. BTW: I am LOVING ubuntu dapper over my Simpley mepis. ABSOLUTLY LOVING IT! :KS :KS :KS

---

### Post by aysiu on 2006-07-25
Paste these commands in the terminal: ```
wget -c http://channels.netscape.com/wrap/linker.jsp?floc=at_oslin_1_l3&ref=http://ftp.newaol.com/aimgen/380469/aim_1.5.286-2_i386.deb
wget -c http://in.dld.yahoo.com/i/in/messenger/linux/debian_sid/ymessenger_0.99.17-1_i386.deb
sudo dpkg -i *.deb
```

---

### Post by daniel of sarnia on 2006-07-25
I don't use AIM, but I am sure AOL dose not make a linux messenger.

edit: guess I was wrong, shows what I know

---

### Post by Luthy on 2006-07-25
luthy@luthy-desktop:~$ wget -c [http://channels.netscape.com/wrap/linker.jsp?floc=at_oslin_1_l3&ref=http://ftp.newaol.com/aimgen/380469/aim_1.5.286-2_i386.deb](http://channels.netscape.com/wrap/linker.jsp?floc=at_oslin_1_l3&ref=http://ftp.newaol.com/aimgen/380469/aim_1.5.286-2_i386.deb)
[1] 11468
luthy@luthy-desktop:~$ --22:53:23--  [http://channels.netscape.com/wrap/linker.jsp?floc=at_oslin_1_l3](http://channels.netscape.com/wrap/linker.jsp?floc=at_oslin_1_l3)
           => `linker.jsp?floc=at_oslin_1_l3'
Resolving channels.netscape.com... 64.12.147.87, 205.188.136.184
Connecting to channels.netscape.com|64.12.147.87|:80... connected.
HTTP request sent, awaiting response... 302 Found
Cookie coming from channels.netscape.com attempted to set domain to compuserve.com
Location: [http://channels.netscape.com/wrap/](http://channels.netscape.com/wrap/) [following]
--22:53:23--  [http://channels.netscape.com/wrap/](http://channels.netscape.com/wrap/)
           => `index.html'
Reusing existing connection to channels.netscape.com:80.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://www.netscape.com/page_not_found/](http://www.netscape.com/page_not_found/) [following]
--22:53:23--  [http://www.netscape.com/page_not_found/](http://www.netscape.com/page_not_found/)
           => `index.html'
Resolving [www.netscape.com](www.netscape.com)... 64.12.128.33, 64.12.129.33, 64.12.130.33, ...
Connecting to www.netscape.com|64.12.128.33|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
22:53:23 ERROR 404: Not Found.

---

### Post by Luthy on 2006-07-25
luthy@luthy-desktop:~$ wget -c [http://in.dld.yahoo.com/i/in/messenger/linux/debian_sid/ymessenger_0.99.17-1_i386.deb](http://in.dld.yahoo.com/i/in/messenger/linux/debian_sid/ymessenger_0.99.17-1_i386.deb)
--22:54:21--  [http://in.dld.yahoo.com/i/in/messenger/linux/debian_sid/ymessenger_0.99.17-1_i386.deb](http://in.dld.yahoo.com/i/in/messenger/linux/debian_sid/ymessenger_0.99.17-1_i386.deb)
           => `ymessenger_0.99.17-1_i386.deb'
Resolving in.dld.yahoo.com... 203.84.221.245
Connecting to in.dld.yahoo.com|203.84.221.245|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 529,336 (517K) [text/plain]

100%[====================================>] 529,336      101.46K/s    ETA 00:00

22:54:27 (101.27 KB/s) - `ymessenger_0.99.17-1_i386.deb' saved [529336/529336]

luthy@luthy-desktop:~$ sudo dpkg -i *.deb
(Reading database ... 136846 files and directories currently installed.)
Preparing to replace ymessenger 1.0.4_1 (using ymessenger_0.99.17-1_i386.deb) ...
Unpacking replacement ymessenger ...
Preparing to replace ymessenger 0.99.17-1 (using ymessenger_1.0.4_1_i386.deb) ...
Unpacking replacement ymessenger ...
More than one copy of package ymessenger has been unpacked
 in this run !  Only configuring it once.
dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on libgdk-pixbuf2 (>= 0.13.0); however:
  Package libgdk-pixbuf2 is not installed.
 ymessenger depends on libssl0.9.6; however:
  Package libssl0.9.6 is not installed.
 ymessenger depends on xlibs (>> 3.3.6); however:
  Package xlibs is not installed.
dpkg: error processing ymessenger (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ymessenger
luthy@luthy-desktop:~$ sudo apt-get install libssl0.9.6
Reading package lists... Done
Building dependency tree... Done
Package libssl0.9.6 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libssl0.9.6 has no installation candidate
luthy@luthy-desktop:~$

---

### Post by daniel of sarnia on 2006-07-25
maybe look on google for the deb files, or enable the other ubuntu repositories.

---

### Post by loell on 2006-07-25
you can try [GYachI]("http://ubuntuforums.org/showthread.php?t=190900&highlight=gyachi")

its a yahoo messenger for linux
that supports webcam and voice chat in rooms :)

---

### Post by Luthy on 2006-07-25
Thanks! is there one that works like AIM? i know they have one for AIM for Linux @ the AIM website but doesnt seem to work ^^^wrote the stuff a bit ago. :-(

---

### Post by Luthy on 2006-07-25
Dl'd that GYachI but says " Failed to Satisfy all dependencies" (broken cache) any suggestions?

---

### Post by loell on 2006-07-25
perhaps you should do

  sudo apt-get update

and

 sudo apt-get install -f

maybe it can satisfy dependecies

---

### Post by Luthy on 2006-07-25
Did that and it worked just fine hun. Now is there an AIM for linux that actually works? or should i try to install The AIM for linux again since i did that neat little trick you taught me?

---

### Post by loell on 2006-07-25
maybe you should :)

but well, it might make your system unstable if you do further force install
but as part of learning, i think you should try them all :)

---

### Post by Luthy on 2006-07-25
I installed the AIM for linux just fine :) XD ! But new prob: Cant find them. Both the AIm and the other one isnt in my Applications>Internet thingy :-(

---

### Post by loell on 2006-07-25
you can do

whereis aim 

or

whereis gyachi

and make a shortcut in desktop pointing to the path where they are installed

or

just execute it in the terminal 

or in the command launcher ... :KS

---

### Post by Luthy on 2006-07-25
k i restarted my comp, and Gyachi was where it was supposed to be but not AIM. So i did what you told me to do and found AIM but when i went to usr>local>bin>aim and clicked on AIM it wont start? Am i doing something wrong? Or am i just a dumb blonde?

---

### Post by loell on 2006-07-26
can you start aim via terminal?
what is the output?

---

### Post by Luthy on 2006-07-26
> **loell said:**
> can you start aim via terminal?
what is the output?
Um im a n00b @ that one huns, how do i do that. OMG im so blonde eek! :confused:

---

### Post by loell on 2006-07-26
sorry, i got a lot of assumptions :D lol

i believe in the system menu there is "Terminal" or "Terminal console"
then click, if you have a little backgraound in Windows, its kinda the equivalent of command line prompt :)

basically it is where you type the command 

apt-get ...

from the previous post

---

### Post by loell on 2006-07-26
ah i get it, just type

aim 

:)

---

### Post by Luthy on 2006-07-26
luthy@luthy-desktop:~$ sudo apt-get aim
Password:
E: Invalid operation aim
luthy@luthy-desktop:~$

um im not that much of a n00b, i can work the the terminal ut some tings are new to me. . thats what i got. and Gayachi keeps crashing.

---

### Post by Luthy on 2006-07-26
luthy@luthy-desktop:~$ aim
aim: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory
luthy@luthy-desktop:~$

*quick note:GaYAchi will open but then close suddenly, was working fine, now it hates me.

---

### Post by stebrepar on 2006-10-31
> **aysiu said:**
> Paste these commands in the terminal: ```
wget -c http://channels.netscape.com/wrap/linker.jsp?floc=at_oslin_1_l3&ref=http://ftp.newaol.com/aimgen/380469/aim_1.5.286-2_i386.deb
wget -c http://in.dld.yahoo.com/i/in/messenger/linux/debian_sid/ymessenger_0.99.17-1_i386.deb
sudo dpkg -i *.deb
```

I wasn't able to get AIM for Linux working with this either, not because the wrong info was given, but because the info from AOL is old (and/or wrong). And the .deb file that got downloaded was apparently built wrong somehow by AOL; when trying to dpkg install it, a message consistently says it doesn't seem to be in a valid .deb format and may have been corrupted, perhaps by downloading in ASCII rather than binary.

But...I was able to get it working eventually a few minutes ago on my shiny new Ubuntu 6.10/edgy system, and here's how (if I can remember it all correctly now). First for reference, the Linux AIM download page is here:
[http://www.aim.com/get_aim/linux/latest_linux.adp?aolp=0](http://www.aim.com/get_aim/linux/latest_linux.adp?aolp=0)
And their FAQ addressing several problems is here:
[http://www.aim.com/help_faq/using/linux.adp](http://www.aim.com/help_faq/using/linux.adp)

Step 1: Download the package.
Problem #1: The .deb file won't work.
Solution: Use the .tgz instead. I chose the latest version, 1.5.286, downloaded to my Desktop via the ordinary Firefox download function.

Step 2: Open a terminal, move the file to root, and go there yourself.
```
cd ~/Desktop
sudo mv aim-1.5.286.tgz /
cd /
```

Step 3: Unzip the file to get the original .tar file.
```
sudo gunzip -vr aim-1.5.286.tgz
```

Step 4: Extract the .tar file's contents (while still at '/').
```
sudo tar -xvf aim-1.5.286.tar
```

Step 5: AIM is built with (at least) a couple old libraries that are no longer installed with our systems, so you need to fix that--which I learned when trying to run AIM and it crashed, complaining it couldn't find a couple library files. First it needed libgtk-1.2.so.0, so I installed libgtk1.2 via Synaptic... (I don't know if a symbolic link to the newer 2.0 version (see Step 6 below) would have also worked.)

Step 6: Then it also needed /usr/lib/libstdc++-libc6.1-1.so.2, which is addressed in the FAQ, saying you need to create a symbolic link between that filename and the newer version of the actual file that's already on your system. But the FAQ is old (or just wrong) in what the new actual file is. There were a couple possibilities for which file might be the right one in my /usr/lib, and I chose (partly just guessing) libstdc++.so.6. So the link command was:
```
sudo ln -ivs /usr/lib/libstdc++.so.6 /usr/lib/libstdc++-libc6.1-1.so.2
```

Step 7: Run AIM.
Problem: The directory structure described on the download page for the .tgz file (i.e., /usr/local/bin/aim) is wrong.
Solution: It's actually /usr/bin/aim to start AIM.

And then it finally worked. Hooray! Sadly, the font in the various windows looks terrible (at least for me; my screen defaulted to 1280x1024 when I installed Ubuntu, so I don't know if it would look better at a lower resolution). And from the messages I see now on my terminal, it looks like sounds aren't working: "AimSounds: esdplay: not found". Maybe because the sound generating part of the package still thinks it's supposed to be at /usr/local/bin as the download page says? I don't know. But clearly, with the old libraries and old information online, it needs some more work. (Or if it were included in Synaptic to more easily transition Windows users to Ubuntu users, that would be even better... (hint, hint to the devs ;-))
-- 
Stephen

---

