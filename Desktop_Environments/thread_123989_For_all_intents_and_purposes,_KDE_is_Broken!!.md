---
title: "For all intents and purposes, KDE is Broken!!"
date: 2006-01-31
forum: Desktop Environments
---

### Post by AlexanRO on 2006-01-31
Sorry, but that is the nicest way I could say it.   I performed an expert install of Kubuntu (unaware of the issue I will be expounding on momentarly), expert install is necessary for me to configure apt to use proxy here at work.  During the expert install I configured root password, I later discover that the root is not necessarily root (in essence).  Please allow me to continue, for some reason in spite of the previous steps an apt.conf file containing proxy and authentication credentials was not created/written. Nor did I config env-var's, needless to say apt can not access mirrors as a result.  No problem open console-> su-> enter root (perhaps fake root) password-> cd /etc/apt-> ls - no apt.conf in sight-> touch apt.conf -> vi apt.conf-> entered :

```
APT::Default-Release "breezy";
APT::Cache-Limit 30000000;
APT::Get::Purge;
APT::Get::ReInstall;
Acquire::cdrom::Mount "/media/cdrom";

ACQUIRE {
    Retries "3";
    Http {
        Proxy "http://uid:passwd@proxy.com:port/";
    }
};

```

esc-> shift+: ->wq!-> 

```
apt-get update
``` 

poof, presto, a-la-ka-zam I can't think of any others, but you get the picture I'm sure.  I'm not a big fan of Adept, although not opposed to change either (obviously, I use GNU/Linux as opposed to M$ Windows right??) I like to use apps that just simply work.  I 

```
apt-get install kynaptic
``` 

(it has a more similar Synaptic appeal, and I have not yet configured my sources to point to mirrors that contain Synaptic.)  I launch Kynaptic, I'm greeted with the usual "Run as Root- KDE su" dialog box as I expected.  I enter the root password that I configured during the "expert install".  Instead of being greeted with Kynaptic KDE responds with a "Sorry KDE su" dialog box containing an error that states that I have entered an incorrect password.  Prior to posting I made absolutely sure to comb this forum, the wiki and Google for possible solutions for this problem I found none.  I even tried some of the ridiculous short-term fixes for gp (with the execption of logging on as root because that is just ,hhhmmm how should I put it? Stupid!!!) with no good results mind you. I am unable to "properly" administer KDE using gui utils, therefore, for all intents and purposes, KDE is Broken!!

I have included a screen capture for your viewing displeasure....

AlexanRO

---

### Post by NeoChaosX on 2006-01-31
KDE is not broken. Did you try entering your own password? By default, the root account in (K)Ubuntu is disabled, and you're supposed to enter your own account's password to do anything that requires admin rights.

---

### Post by wd3thatsme on 2006-01-31
same here. it seems that after i updated and upgraded my system, all hell broke loose. same problem. i thinking about going to back to the suse 10 i just downloaded.

---

### Post by AlexanRO on 2006-01-31
[QUOTE=NeoChaosX]Did you try entering your own password? By default, the root account in (K)Ubuntu is disabled, and you're supposed to enter your own account's password to do anything that requires admin rights.[/QUOTE]

#include <stdio.h>

main()

if (answer=yes) {
     //KDE is Broken
     printf("\n answer=yes\n");
}
else {
    //do not apply band-aid apply fix
    printf("\ndo not apply band-aid apply fix\n");
}

Please excuse my frustration, my sarcasm is not intentionally directed at you I know that you are only trying to help. The root and localuser accounts share the same password because this is a test enviornment, so far Kubuntu is failing miserably.  It is fair to say that until issues like this are resolved prior to release, well Kubuntu/KDE will be as useless as the above code... Now repeat after me :twisted: Broken, Broken, BROKEN!!!

AlexanRO

---

### Post by matthew on 2006-01-31
Well, if all you want to do is get this off your chest then the rant is fine. If you genuinely want to be helpful the best thing to do is file a bug report that the developers will see. To do that [go here]("https://launchpad.net/malone"). Please do so. I think your input could be valuable.

---

### Post by AlexanRO on 2006-01-31
[QUOTE=matthew]Well, if all you want to do is get this off your chest then the rant is fine. If you genuinely want to be helpful the best thing to do is file a bug report that the developers will see. To do that [go here]("https://launchpad.net/malone"). Please do so. I think your input could be valuable.[/QUOTE]

You know you are right and I intend on doing just what you suggest.  However, there is this one small caveat that I think the developers will have a problem with. Before I go flame dodging let me share with you the reason why.  I have used the following distros --RHT 7.3, 8.0, 9.0, FC1, 2, 3, presently 4, MDV (formerly MDK) 8.2, 9.1, 10.0, 10.1, 2005, 2006,  presently Deb 3.1 (sarge stable), Simply Mepis 3.3.1, Ubuntu 5.04 (KDE 3.4.3 resides on this Ubuntu box), to continue on would be moot. My point is that from RHT7.3 up until the present this problem did not exist (at least not with any of these installs), it is not something that can be isolated to KDE as I have only experienced it while using Kubuntu 5.10 the Breezy Badger --apparently I'm not the only who is ranting [(rant,rant,rant)]("http://ubuntuforums.org/showthread.php?t=75114") see for your self.

AlexanRO

I thought that I would include a screen capture of my box at home running Ubuntu 5.04 ,by the way no problems here..[KDE on Ubuntu 5.04]("http://www.lynucs.org/index.php?screen_id=803948136439ba1383d699&p=screen")

---

### Post by Antoine.L on 2006-01-31
I thought I'd read that configuring a root password can break some of the GUI admin tools?  Kubuntu isn't really meant to be used that way, anyway.

Maybe I'm missing your point.

---

### Post by matthew on 2006-01-31
[quote=AlexanRO]However, there is this one small caveat that I think the developers will have a problem with. Before I go flame dodging let me share with you the reason why...it is not something that can be isolated to KDE as I have only experienced it while using Kubuntu 5.10 the Breezy Badger --apparently I'm not the only who is ranting [http://ubuntuforums.org/showthread.php?t=75114]("http://ubuntuforums.org/showthread.php?t=75114") see for your self.[/quote]
Umm... Okay. That makes it sound like your input would be more, not less valuable to the Ubuntu developers at the site I linked to in my previous post.

I'm not a developer, just a user hanging out in the forums. I'm not sure if the defensive tone/posture in your post was intentional or accidental, but I have no plans to attack you. If you are having problems with Kubuntu's implementation of KDE and not that of any other distro's it makes sense to file a bug report with Ubuntu. That's all I'm saying. You don't need to point at a ton of evidence of others having similar problems to convince me of anything...I'm just trying to tell you how to express your observations to people who are working very hard to make Ubuntu and Kubuntu great. The devs don't generally read these forums--they're busy working. The bug reports are read and answered, though, and fixed as soon as possible.

---

### Post by zachariah on 2006-01-31
Odd - I installed Kubuntu 5.10 with all default options and was able to use sudo apt-get install synaptic with no prior modifications (except to tell the Windows ISA server to let this box have free access to the internet). After which sudo synaptic worked without a hitch. What were these special proxy settings you needed, and why couldn't they wait till after a default install to set up?

PS you can log in as root if you really want to - you have to change a line in xorg.conf from false to true (or vice versa, can't remember) about allowing root login - AFTER giving the root account a password.

---

### Post by Kuprin on 2006-01-31
This, to me (I'm a dev, though not an Ubuntu dev so nobody mistake me for one) looks like a user error; though it could be a bug, for sure. I'd give it 50/50. Since you're an experienced user, I'm assuming you double-checked your passwords file and everything to ensure you didn't mistype anything during account creation, it's probably a bug. File a bug report and hopefully this mystery will be cleared up shortly. :)

---

### Post by N8K99 on 2006-02-01
I just used   [SIZE="2"]sudo apt-get install kynaptic[/SIZE] and then used it to install some packages. I am running Kubuntu Kbreezy Kbadger 5.10 this is my first linux distro and have not had and trouble with it whatsoever. There have been moments where I have to look for answers. But I have found them and really am quite pleased with the results. Keep up the good work guys.

---

### Post by localzuk on 2006-02-01
Why not do a normal install and then change the configuration afterwards? It seems to me that the fiddling you have done has caused problems elsewhere. I would have done a vanilla kubuntu install from a normal ISO download and then reconfigured apt to use proxy etc...

Why do you need to access the proxy before you have a vanilla install set up?

---

### Post by Al3xanR0 on 2006-03-29
[QUOTE=AlexanRO]Sorry, but that is the nicest way I could say it.   I performed an expert install of Kubuntu (unaware of the issue I will be expounding on momentarly), expert install is necessary for me to configure apt to use proxy here at work.  During the expert install I configured root password, I later discover that the root is not necessarily root (in essence).  Please allow me to continue, for some reason in spite of the previous steps an apt.conf file containing proxy and authentication credentials was not created/written. Nor did I config env-var's, needless to say apt can not access mirrors as a result.  No problem open console-> su-> enter root (perhaps fake root) password-> cd /etc/apt-> ls - no apt.conf in sight-> touch apt.conf -> vi apt.conf-> entered :

```
APT::Default-Release "breezy";
APT::Cache-Limit 30000000;
APT::Get::Purge;
APT::Get::ReInstall;
Acquire::cdrom::Mount "/media/cdrom";

ACQUIRE {
    Retries "3";
    Http {
        Proxy "http://uid:passwd@proxy.com:port/";
    }
};

```

esc-> shift+: ->wq!-> 

```
apt-get update
``` 

poof, presto, a-la-ka-zam I can't think of any others, but you get the picture I'm sure.  I'm not a big fan of Adept, although not opposed to change either (obviously, I use GNU/Linux as opposed to M$ Windows right??) I like to use apps that just simply work.  I 

```
apt-get install kynaptic
``` 

(it has a more similar Synaptic appeal, and I have not yet configured my sources to point to mirrors that contain Synaptic.)  I launch Kynaptic, I'm greeted with the usual "Run as Root- KDE su" dialog box as I expected.  I enter the root password that I configured during the "expert install".  Instead of being greeted with Kynaptic KDE responds with a "Sorry KDE su" dialog box containing an error that states that I have entered an incorrect password.  Prior to posting I made absolutely sure to comb this forum, the wiki and Google for possible solutions for this problem I found none.  I even tried some of the ridiculous short-term fixes for gp (with the execption of logging on as root because that is just ,hhhmmm how should I put it? Stupid!!!) with no good results mind you. I am unable to "properly" administer KDE using gui utils, therefore, for all intents and purposes, KDE is Broken!!

I have included a screen capture for your viewing displeasure....

AlexanRO[/QUOTE]


open console (as root) run visudo command added the following line :

userid    ALL=(ALL) ALL

F3 edited file name to /etc/sudoers

enter-> y (to overwrite)

ctrl + x to exit

Fixed Fixed Fixed !!!

For all intents and purposes of course.

---

