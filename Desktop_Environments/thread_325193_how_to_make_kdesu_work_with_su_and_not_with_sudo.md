---
title: "how to make kdesu work with su and not with sudo?"
date: 2006-12-25
forum: Desktop Environments
---

### Post by cap_gemo on 2006-12-25
Hi everyone,

  I have found a pretty fine guide here: [http://ubuntuforums.org/showthread.php?t=6267&highlight=gksu+gksudo](http://ubuntuforums.org/showthread.php?t=6267&highlight=gksu+gksudo)

  It explains, how to make gksu work with su. But I could not find anything similar about kdesu, although I am sure, that a lot of people should have asked about that.

  So, is there a possibility to make kdesu work with su and not with sudo?

  Thank you for your help.

  P.S. Please, do not post answers like: "why do you need su? sudo is okay".

---

### Post by TheWizzard on 2006-12-25
google is your friend: 
> man:/kdesu in konqueror can explain more in detail about the kdesu command.
You can also make kdesu use 'su' as its authentication command if that is what you want.
This is done in ~/.kde/share/config/kdesurc, it should look like this when su is selected:
 frode@light:~ $ cat ~/.kde/share/config/kdesurc
 [super-user-command]
 super-user-command=su
 frode@light:~ $
 (this is a per-user setting. If you want it system wide, put the file in /usr/share/kubuntu-default-settings/kde-profile/default/share/config/ instead.)
You might need to update the system config cache:
 frode@light:~ $ kbuildsycoca --incremental
Now RunAs and 'kdesu' uses 'su' for it's authentication needs. This of course depends on a enabled root account which Ubuntu/Kubuntu does not have by default. 

[https://launchpad.net/distros/ubuntu/+ticket/1983](https://launchpad.net/distros/ubuntu/+ticket/1983)


you can also allow any user to access the X server while logged in as user, use the xhost command (being user):  
```
 xhost +
```


however, i would **strongly **advice you to get used to the ubuntu way of dealing with root permissions. there are no real reasons to activate the root account neither to enable graphical root login. 

PS
in the terminal you can stay in su mode using:
```
sudo -s
```

please read: 
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by cap_gemo on 2006-12-25
> **TheWizzard said:**
> ...neither to enable graphical root login...

I'm not gonna do that ;)

For the other informations thank you very much!

---

### Post by cap_gemo on 2008-05-02
Episode Next: kdesudo strikes back :(

  I have just made an upgrade to hardy heron (which has KDE 3.5.9) and now suddenly this super-user-command entry in the config file completely lost its functionality. Kdesu asks me for my user password and not for the root password. I even have a feeling, kdesu is now somethink like a simple clone of kdesudo.

  I'd be very grateful, if comeone could help me. Please tell me, how to enable the su functionality for kdesu in KDE 3.5.9 under hardy.

  Thanks in advance!

---

### Post by TheWizzard on 2008-05-02
> **cap_gemo said:**
> Episode Next: kdesudo strikes back :(

  I have just made an upgrade to hardy heron (which has KDE 3.5.9) and now suddenly this super-user-command entry in the config file completely lost its functionality. Kdesu asks me for my user password and not for the root password. I even have a feeling, kdesu is now somethink like a simple clone of kdesudo.

  I'd be very grateful, if comeone could help me. Please tell me, how to enable the su functionality for kdesu in KDE 3.5.9 under hardy.

  Thanks in advance!

by default there is no root account enabled. read: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by cap_gemo on 2008-05-02
> **TheWizzard said:**
> by default there is no root account enabled. read: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

I guess, you haven't read any of the above messages. My root account IS activated, I CAN use su in the konsole, and I HAVE the option super-user-command=su in the config file ~/.kde/share/config/kdesurc but still kdesu works likes kdesudo AFTER THE UPGRADE to KDE 3.5.9 under hardy. Before the upgrade kdesu worked just as I wanted with feisty and gutsy. And that is my problem.

---

### Post by cap_gemo on 2008-05-10
Ok, now I got it. There's absolutely no kdesu package in hardy, but only kdesudo, and the command kdesu seems to be just a simlink, or something like this. This drives me really mad. Is there any way to install the normal kdesu?

---

### Post by cap_gemo on 2008-05-10
Problem solved!!!!

I just downloaded the source of kdebase from kde.org, ran ./configure and make and then simply copied the kdesu binary to /usr/bin. Now kdesu works.

------------------------------------------

Here a short guide for everyone, who is interested in using kdesu and not kdesudo. Open a konsole and run the following commands:

```

wget ftp://ftp.kde.org/pub/kde/stable/3.5.9/src/kdebase-3.5.9.tar.bz2
tar -xvjf kdebase-3.5.9.tar.bz2
cd kdebase-3.5.9
./configure
make
cd kdesu/kdesu
sudo cp kdesu /usr/bin

```

Enjoy!

P.S. By writing sudo I just follow the usual "ubuntu convention". What I actually did, was su and then cp kdesu /usr/bin :) :) :)

---

