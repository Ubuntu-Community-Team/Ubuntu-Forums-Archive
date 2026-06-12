---
title: "Steam not working"
date: 2016-04-26
forum: Gaming &amp; Leisure
---

### Post by lgt2 on 2016-04-26
I just got Ubuntu, because my windows just got to boring. I tired to install my steam, but it said admin blocked permission, so i download to terminal and did 
```
sudo apt-get install steam
```
 it worked but when i tried to open steam it started to install, but then it said 
```
You are missing the following 32-bit libraries, and Steam may not run:
libXtst.so.6
libXrandr.so.2
libgobject-2.0.so.0
libglib-2.0.so.0
libgtk-x11-2.0.so.0
libpulse.so.0
libgdk_pixbuf-2.0.so.0
```









If you can help me please do :D

---

### Post by MikeCyber on 2016-04-27
Your command installs from repositories and not your local download. For that do
cd ~
or where your steam is and execute alike
./steam
Never use sudo only when you have to.
I guess you didn't install the proprietary graphics driver? Nvidia etc.
Try again after removing in your home the hidden steam folder
cd ~
rm -rf .steam

---

### Post by lgt2 on 2016-04-27
Can you please tell me step by step also in a simpler way, I'm brand new to this "linux distro", also coding and commands

---

### Post by lgt2 on 2016-04-27
Also if you can can you help with another problem


this keeps happening to me

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


Help?

---

### Post by lgt2 on 2016-04-27
I try to open steam the icon pops out but its just loads for a few seconds then goes away

its dowloading update, also said unpacking steam.
Help :D

---

### Post by oldrocker99 on 2016-04-27
> **lgt2 said:**
> Also if you can can you help with another problem


this keeps happening to me

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


Help?

**Permission denied** responses usually result in not using```
sudo <command>
```
When you do this, it'll ask for your password. Type it in. It will NOT show what you type. If you typed it correctly, the command will run. 

Sudo stands for Super User DO, and, by the way, is pronounced Soo-Doo, not Soo-Doh. It gives you super user privileges needed to alter anything in the operating system, like installing programs or editing system text files, and it only lasts about 8-10 minutes. You need to type your password in again.

Now, to fix your Steam install:```
sudo apt-get -f install
``` That should install the missing dependencies. The best way to install Steam, which always works for me, is still using the terminal thus:```
sudo apt-get install steam
``` All the libraries will be installed along with Steam.

If you have an nVidia card, you need to install the proprietary drivers from "Additional Drivers." If you have ATI, the drivers are already installed.

Let us know if that fixed your problems.

---

### Post by oldrocker99 on 2016-04-27
Steam has to install its runtime, which is what gets downloaded and expanded. It goes into your home folder, in the folder .steam.

Is Steam running?

---

### Post by QDR06VV9 on 2016-04-27
Threads merged.

---

### Post by lgt2 on 2016-04-27
I used the command you gave me and at the end it said

Code:
```
sudo apt-get -f install
Sub-process /usr/bin/dpkg returned an error code (1)"

```

"
it also stated the same error when using the 

Code: 
```
sudo apt-get install steam
```

it responded with:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
steam:i386 is already the newest version (1:1.0.0.48-1ubuntu3).
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gcc-5-multilib : Depends: libc6-dev-i386 (>= 2.11) but it is not going to be installed
 libc6-dev-x32 : Depends: libc6-dev-i386 (= 2.23-0ubuntu3) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

THEN: when i tried using apt-get -f install it responded with
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  dreamchess-data libfluidsynth1 libmad0 libmikmod3 libmxml1 libopenal-data
  libopenal1 libsdl-image1.2 libsdl-mixer1.2 libsdl1.2debian libstdc++-5-dev
  musescore-soundfont-gm timgm6mb-soundfont
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libc6-dev-i386
The following NEW packages will be installed:
  libc6-dev-i386
0 upgraded, 1 newly installed, 0 to remove and 19 not upgraded.
128 not fully installed or removed.
Need to get 0 B/1,265 kB of archives.
After this operation, 6,940 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 203341 files and directories currently installed.)
Preparing to unpack .../libc6-dev-i386_2.23-0ubuntu3_amd64.deb ...
Unpacking libc6-dev-i386 (2.23-0ubuntu3) ...
dpkg: error processing archive /var/cache/apt/archives/libc6-dev-i386_2.23-0ubuntu3_amd64.deb (--unpack):
 trying to overwrite '/usr/include/bits', which is also in package libc6-dev-amd64:i386 2.23-0ubuntu3
Errors were encountered while processing:
 /var/cache/apt/archives/libc6-dev-i386_2.23-0ubuntu3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Should i just install a new linux distro or something i really need help.

---

### Post by QDR06VV9 on 2016-04-27
Hi lgt2
try this and post back any errors
```
sudo apt-get upgrade --fix-missing
```

---

### Post by lgt2 on 2016-04-27
Hello runrickus i did what you said and the same error in the same location came up, also will doing this command steam-launcher came up to install and is saying waiting install. Also here is the error:

```
Errors were encountered while processing:
 /var/cache/apt/archives/libc6-dev-i386_2.23-0ubuntu3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

P.s also few minutes later i got a notification that steam was not working...

---

### Post by QDR06VV9 on 2016-04-27
Ok! Lets see if we can fix it then.
```
sudo dpkg -i /var/cache/apt/archives/*.deb
```
And after that run
```
sudo dpkg --configure -a
```
Fingers Crossed

---

### Post by lgt2 on 2016-04-27
Ugh here you go error:

```
dpkg: dependency problems prevent configuration of libc6-dev-x32:
 libc6-dev-x32 depends on libc6-dev-i386 (= 2.23-0ubuntu3); however:
  Package libc6-dev-i386 is not installed.

dpkg: error processing package libc6-dev-x32 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gcc-5-multilib:
 gcc-5-multilib depends on libc6-dev-i386 (>= 2.11); however:
  Package libc6-dev-i386 is not installed.
 gcc-5-multilib depends on libc6-dev-x32 (>= 2.11); however:
  Package libc6-dev-x32 is not configured yet.

dpkg: error processing package gcc-5-multilib (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gcc-multilib:
 gcc-multilib depends on gcc-5-multilib (>= 5.3.1-3~); however:
  Package gcc-5-multilib is not configured yet.

dpkg: error processing package gcc-multilib (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libc6-dev-x32
 gcc-5-multilib
 gcc-multilib
```

---

### Post by QDR06VV9 on 2016-04-27
Fun Stuff Huh? lol
Well lets poke at this a bit
```
 sudo dpkg -r --force-depends libc6:i386

```

---

### Post by lgt2 on 2016-04-27
Very fun i love errors and coding 

Now what do i, do after that

---

### Post by QDR06VV9 on 2016-04-27
Now we see if everything is in a good state
```
sudo dpkg --configure -a
```
And if that goes well
```
sudo apt update
sudo apt upgrade
```

---

### Post by lgt2 on 2016-04-27
well here you go

Code:
```
sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of libc6-dev-x32:
 libc6-dev-x32 depends on libc6-dev-i386 (= 2.23-0ubuntu3); however:
  Package libc6-dev-i386 is not installed.

dpkg: error processing package libc6-dev-x32 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gcc-5-multilib:
 gcc-5-multilib depends on libc6-dev-i386 (>= 2.11); however:
  Package libc6-dev-i386 is not installed.
 gcc-5-multilib depends on libc6-dev-x32 (>= 2.11); however:
  Package libc6-dev-x32 is not configured yet.

dpkg: error processing package gcc-5-multilib (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gcc-multilib:
 gcc-multilib depends on gcc-5-multilib (>= 5.3.1-3~); however:
  Package gcc-5-multilib is not configured yet.

dpkg: error processing package gcc-multilib (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libc6-dev-x32
 gcc-5-multilib
 gcc-multilib
```

---

### Post by QDR06VV9 on 2016-04-27
Stubborn little dickens isn't it?
What dose this report?
```
apt-cache policy libc6-dev-i386
```

---

### Post by lgt2 on 2016-04-27
yes it is stubborn holy crap didnt know this would happen


```
apt-cache policy libc6-dev-i386
libc6-dev-i386:
  Installed: (none)
  Candidate: 2.23-0ubuntu3
  Version table:
     2.23-0ubuntu3 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
```

---

### Post by QDR06VV9 on 2016-04-27
Lets see if we can get it happy
```
sudo apt install libc6-dev-i386
```

---

### Post by lgt2 on 2016-04-27
it said try

: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by lgt2 on 2016-04-27
well it worked until... surprise 



trying to overwrite '/usr/include/bits', which is also in package libc6-dev-amd64:i386 2.23-0ubuntu3
Errors were encountered while processing:
 /var/cache/apt/archives/libc6-dev-i386_2.23-0ubuntu3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by QDR06VV9 on 2016-04-27
Hope you packed your lunch....my jokes are bad I know.:P
well maybe then
```
sudo apt-get -f install
```

---

### Post by lgt2 on 2016-04-27
Love them jokes keeping me sane from all this coding and terminal stuff

also how do i do the code thing

Here is the new ERROR


```
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  libstdc++-5-dev
Use 'sudo apt autoremove' to remove it.
The following additional packages will be installed:
  libc6-dev-i386
The following NEW packages will be installed:
  libc6-dev-i386
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0 B/1,265 kB of archives.
After this operation, 6,940 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 203359 files and directories currently installed.)
Preparing to unpack .../libc6-dev-i386_2.23-0ubuntu3_amd64.deb ...
Unpacking libc6-dev-i386 (2.23-0ubuntu3) ...
dpkg: error processing archive /var/cache/apt/archives/libc6-dev-i386_2.23-0ubuntu3_amd64.deb (--unpack):
 trying to overwrite '/usr/include/bits', which is also in package libc6-dev-amd64:i386 2.23-0ubuntu3
Errors were encountered while processing:
 /var/cache/apt/archives/libc6-dev-i386_2.23-0ubuntu3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by lgt2 on 2016-04-27
well i have to go if you want to message me anymore command please Do: 
my work email is

---

### Post by QDR06VV9 on 2016-04-27
I will just post here in the forums.
Gives me enough time to eat and think a bit.

---

### Post by QDR06VV9 on 2016-04-28
Hey there lgt2:)
Lets give this a little harder poke
```
sudo apt-get autoremove
```
Now this if it will allow us.
```
sudo rm -fr  /var/cache/apt/archives/libc6-dev-i386_2.23-0ubuntu3_amd64.deb
```
Now lets look at your source list... paste back the content's
```
 gedit /etc/apt/sources.list
```
Maybe today we will fix this...

---

### Post by lgt2 on 2016-04-28
Here you go i need my steam and computer to work PLease halp and work




```
#deb cdrom:[Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1)]/ xenial main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
```

---

### Post by QDR06VV9 on 2016-04-28
How did the autoremove go? any errors?

---

### Post by lgt2 on 2016-04-28
Nothing that i could see, but here 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 gcc-5-multilib : Depends: libc6-dev-i386 (>= 2.11) but it is not installed
 libc6-dev-x32 : Depends: libc6-dev-i386 (= 2.23-0ubuntu3) but it is not installed
E: Unmet dependencies. Try using -f.
```

---

### Post by QDR06VV9 on 2016-04-28
I hope this is a newish install or you have made a good back-up for files or anything you might miss if the worst happens.
Then we proceed
```
sudo dpkg --purge --force-depends gcc
```

---

### Post by lgt2 on 2016-04-28
Now what?

Also this is a new install just like 3 days so anything and i can full restart

---

### Post by QDR06VV9 on 2016-04-28
Ok run the next commands one line at a time

```
sudo apt-get  clean
sudo apt-get update
sudo apt-get -f install
```

---

### Post by lgt2 on 2016-04-28
so everything was going good no error until last command 
Same error with the same folder maybe that folder is Bugged?

here is the error:


```
Errors were encountered while processing:
 /var/cache/apt/archives/libc6-dev-i386_2.23-0ubuntu3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by QDR06VV9 on 2016-04-28
Yuck!  That is one persistent show stopper.
How did you install steam? A link would be good.
Or an explanation on how you installed steam.

---

### Post by lgt2 on 2016-04-28
Fist i tried from their website steam and ubuntu software popped p to install steam, i put install but the installation didn't work it would show for like a sec then put a icon on my sidebar, but wont downlaod.

Then i put in terminal sudo apt-get install steam it worked, but then it said i was missing something... there you go

---

### Post by QDR06VV9 on 2016-04-28
Never mind I went back an read through to here.
I have to do a little fact checking here to get to a possible solution.
I will return.

---

### Post by QDR06VV9 on 2016-04-28
> **lgt2 said:**
> **Fist i tried from their website steam and ubuntu software popped p to install steam, **i put install but the installation didn't work it would show for like a sec then put a icon on my sidebar, but wont downlaod.


Ah OK run this then
```
sudo apt-get purge --auto-remove steam
```
Fingers crossed

---

### Post by lgt2 on 2016-04-28
i dont if this is bad, but here 



 ```
sudo apt-get purge --auto-remove steam
[sudo] password for lgt: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gcc-5-multilib : Depends: libc6-dev-i386 (>= 2.11) but it is not going to be installed
 libc6-dev-x32 : Depends: libc6-dev-i386 (= 2.23-0ubuntu3) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

---

### Post by QDR06VV9 on 2016-04-28
What dose this report
```
apt-cache policy lib32gcc1
```

---

### Post by lgt2 on 2016-04-28
This what it reports


```
lib32gcc1:
  Installed: 1:6.0.1-0ubuntu1
  Candidate: 1:6.0.1-0ubuntu1
  Version table:
 *** 1:6.0.1-0ubuntu1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main amd64 Packages
        100 /var/lib/dpkg/status
```

---

### Post by QDR06VV9 on 2016-04-28
I am at a loss here!?! :confused:

---

### Post by lgt2 on 2016-04-28
ugh that doesnt sound good should i download a new distro

---

### Post by QDR06VV9 on 2016-04-28
> **lgt2 said:**
> ugh that doesnt sound good should i download a new distro
Not sure what you mean by new Distro? Ubuntu is fine and from what I have heard Steam is available in the multiverse repo which yours is already enabled from what you posted back to me.
So in other words you should be able to install it with
```
sudo apt-get install steam
```
If you mean download a new image of Ubuntu that might not be a bad idea.
Link for 16.04 Unity [http://releases.ubuntu.com/xenial/](http://releases.ubuntu.com/xenial/)

---

### Post by oldrocker99 on 2016-04-29
As I've said before ```
sudo apt-get install steam
``` has worked every time for me.

I tried Manjaro MATE, and liked it, but several Steam games wouldn't run, so it was back to Ubuntu MATE.

---

### Post by QDR06VV9 on 2016-04-29
> **oldrocker99 said:**
> As I've said before ```
sudo apt-get install steam
``` has worked every time for me.

I tried Manjaro MATE, and liked it, but several Steam games wouldn't run, so it was back to Ubuntu MATE.
+1:D
And I am sorry for butting in here oldrocker99, I kind of missed your reply's when I merged his two threads.
So my apologies.

---

### Post by oldrocker99 on 2016-04-30
> **runrickus said:**
> +1:D
And I am sorry for butting in here oldrocker99, I kind of missed your reply's when I merged his two threads.
So my apologies.

No apology required!

---

### Post by MikeCyber on 2016-04-30
In case it hasn't been said, remove the hidden steam folder in your home before a reinstall from repo or steam website.
cd ~
rm -rf .steam

---

### Post by lgt2 on 2016-05-01
Is unbuntu 16.04 LTS work with steam or is it only 12.04 LTS?

---

### Post by oldrocker99 on 2016-05-01
> **lgt2 said:**
> Is unbuntu 16.04 LTS work with steam or is it only 12.04 LTS?

Yes, indeed 16.04 works with Steam. Just install from the Ubuntu repos and you should be all set.

---

### Post by lgt2 on 2016-05-03
Thank you all for the help i somewhat fixed it i downgraded and download it :D

---

