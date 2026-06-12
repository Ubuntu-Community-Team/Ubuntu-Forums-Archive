---
title: "install mplayer grrrr"
date: 2006-08-10
forum: Desktop Environments
---

### Post by thick0 on 2006-08-10
The disk on my laptop was wiped recently so I just installed dapper again. I installed xmms & tbird last night. Today I was going to add mplayer.
[INDENT]
tim@room2401:~$ sudo apt-get install mozilla-mplayer
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mozilla-mplayer[/INDENT]

so I thought about mplayer-586...

[INDENT]tim@room2401:~$ sudo apt-get install mplayer-i586
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mplayer-i586[/INDENT]

I tried a few other installs eg amarok and everything works fine. Is it just a problem with mplayer which will fix itself in  time?

---

### Post by JKoder on 2006-08-10
Hy. In order to apt-get mplayer you need Ubuntu universe or multiverse in your repositories (not really sure )
Mabye i can check my apt-get config file and let you know.

If you succseed let me know !
JKoder

---

### Post by JKoder on 2006-08-10
OK i am back
Here is my sources.list file.
You can copy it . be aware that i am using ALL repositories !

deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security universe main restricted multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by thick0 on 2006-08-10
thanks for that but no good. Still the same response.

It seems to me that none of the repos understands mozilla-mplayer!

---

### Post by Titus A Duxass on 2006-08-10
Do a search with Synaptic for mplayer or with apt-cache search mplayer.

---

### Post by maniacmusician on 2006-08-10
have you tried using automatix to install it? they do have that as a selection, I believe.

[http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025)

also, try installing some other random package to make sure that your synaptic is still working

---

### Post by thick0 on 2006-08-10
Yes, that does the trick. Many thanks.

I am still puzzled why the usual repos don't work!

---

### Post by maniacmusician on 2006-08-10
did you do automatix or a search with synaptic as Titus suggested? if you're saying the usual repos don't work, i'm assuming you did automatix. in that case, could you try installing any old package from the repos just to see if it was just mplayer that was faulty or if you can't access them at all.

---

### Post by thick0 on 2006-08-10
Yes, I used automatix...I tried amarok via synaptic with no problems. Only mplayer causing probs

---

### Post by randell6564 on 2006-08-11
> **thick0 said:**
> thanks for that but no good. Still the same response.

It seems to me that none of the repos understands mozilla-mplayer!

Are you sure you are'nt suppose to just type sudo apt-get install mplayer?

I have mplayer and I just called it mplayer at the terminal.

---

### Post by randell6564 on 2006-08-11
Hey thick!  I just did a sudo apt-get install mozilla-mplayer and it worked.

Heres my sources.list if ya want to use it.

[B]deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe[/B]

---

### Post by thick0 on 2006-08-18
okay, I may be sounding like a broken record but...I copied Randell's sources.list and the thing still doesn't work. This time though I tried a couple of other installs (eg. azureus) and they didn't work either. So, from synaptic I can't install a blinking thing!

automatix still works but I would be eternally grateful if someone could point me in the right direction. This is becoming really frustrating!

[COLOR="Red"]tim@room2401:/etc/apt$ cat sources.list
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
tim@room2401:/etc/apt$ sudo apt-get install sun-java5-jre sun-java5-plugin
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-java5-jre
tim@room2401:/etc/apt$
[/COLOR]

---

### Post by randell6564 on 2006-08-18
> **thick0 said:**
> okay, I may be sounding like a broken record but...I copied Randell's sources.list and the thing still doesn't work. This time though I tried a couple of other installs (eg. azureus) and they didn't work either. So, from synaptic I can't install a blinking thing!
tim@room2401:/etc/apt$ sudo apt-get install sun-java5-jre sun-java5-plugin
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-java5-jre
tim@room2401:/etc/apt$
[/COLOR]

Did you copy my list, save it, THEN do a sudo apt-get update first?

And why are you cd'd into /etc/apt?

After you do an update, go to System>Administration>synaptic Package Manager, after entering your password type Ctrl+F, and type in 'java'. 
You can find the current java packages in synaptic.

---

### Post by BrunoProg64 on 2006-08-25
It happens to me also. In [Spanish Forums of Ubuntu]("http://www.ubuntu-es.org") people said that Mplayer is not on the repositories. If that is true you don't have another choice to compiling by yourself.

Good luck.

---

### Post by randell6564 on 2006-08-25
> **BrunoProg64 said:**
> It happens to me also. In [Spanish Forums of Ubuntu]("http://www.ubuntu-es.org") people said that Mplayer is not on the repositories. If that is true you don't have another choice to compiling by yourself.

Good luck.

OH, I beg to differ!  Mplayer CAN in fact be found in synaptic!

System>Administration>Synaptic Package Manager,

type, 'Ctrl+F' then type in mplayer, and see what you get!

---

