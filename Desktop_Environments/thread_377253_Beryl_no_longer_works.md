---
title: "Beryl no longer works"
date: 2007-03-05
forum: Desktop Environments
---

### Post by Jofaba on 2007-03-05
I'm a day old baby to linux and I realize that beryl is beta, but it's suddenly stopped working and no uninstalling/reinstalling will fix it. 

I am running Kubuntu 6.10 on Nvidia hardware. Everything was fine until I noticed that my windows borders were suddenly gone, so I couldn't grab my windows or anything like that. I rebooted and suddenly all of the effects of beryl were gone. I can load into beryl-manager, but the effects no longer work. 

I'm not sure where to start with what information you'll need and I apologize for that. I've got no problems with beryl crashing, it's going to happen. But it suddenly stopping working brings a dark sad place to my heart. I really miss a lot of the functionality and I've based my linux devotion around it. I'm planning a "nothing but linux at home" adventure to learn as much as I can and beryl is a complete necessity. Beta or not. 

So, what information do you need? Thank you so much in advance. 

btw, even without beryl, (K)ubuntu is fantastic.

---

### Post by old_geekster on 2007-03-05
I am a newbie myself.  I have installed Beryl in Edgy several times, but have never been pleased with the outcome.  Each time there seems to be a different problem.  The major one is a white box with nothing inside when I open the "Terminal".  This isn't good.

Did you try Compiz?  There again, I tried it and had similar problems.  It is another alternative for you to try, however.

There should be some good guides for you to follow.  Here is one for Edgy 6.10: 

[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

I believe it should be the same for Xubuntu.

---

### Post by medley on 2007-03-05
> **Jofaba said:**
> I'm a day old baby to linux and I realize that beryl is beta, but it's suddenly stopped working and no uninstalling/reinstalling will fix it. 

I am running Kubuntu 6.10 on Nvidia hardware. Everything was fine until I noticed that my windows borders were suddenly gone, so I couldn't grab my windows or anything like that. I rebooted and suddenly all of the effects of beryl were gone. I can load into beryl-manager, but the effects no longer work. 

I'm not sure where to start with what information you'll need and I apologize for that. I've got no problems with beryl crashing, it's going to happen. But it suddenly stopping working brings a dark sad place to my heart. I really miss a lot of the functionality and I've based my linux devotion around it. I'm planning a "nothing but linux at home" adventure to learn as much as I can and beryl is a complete necessity. Beta or not. 

So, what information do you need? Thank you so much in advance. 

btw, even without beryl, (K)ubuntu is fantastic.

Beryl is fabulous, but it will frustrate you with these kinds of things. The fix for the borderless problem for me was to edit a file called 'beryl-settings'.

If you are using KDE (ie kubuntu), then start a terminal session, then type

sudo nano /usr/bin/beryl-settings
enter your password
look for the line that says '#!/usr/bin/env python' and change 'python' to 'python2.4' (this is probably the very first line in the file)
press ctrl-x
press y
press enter

Now, restart X by pressing ctrl-alt-backspace. This is a graceful way to restart your X server. Rebooting can cause problems.

BTW, if you are using gnome instead of KDE, you may have to use some other command than 'sudo' above. This is the command that allows you to change things with root priveleges. I think it is gksu or something like that.

Good luck.

---

### Post by Jofaba on 2007-03-05
Yeah as far as I understand, the only difference between Ubuntu and Xubuntu commands is changing them to be kde friendly (can't use gnome commands). 

I love beryl and that's what I want to use. I'm familiar with it after just a single day and have become dependent on several of the interface options (moving to top right to get sorted view, for example). 

There has to be a way to reinstall beryl and start from scratch. I've tried methods that I've found online and they seem to work until I try and activate beryl. I activate it and get the emerald icon but beryl itself is not activated, and none of the effects work. However, all my settings from my previous beryl installation seem to be back in place, so that leads me to believe that I'm not removing beryl correctly. 

I've checked my x and nvidia and everything seems to be good. Any help would be appreciated although I realize that you probably need more info. Just let me know what you need to know and I'll tell you.

---

### Post by Jofaba on 2007-03-05
> **medley said:**
> Beryl is fabulous, but it will frustrate you with these kinds of things. The fix for the borderless problem for me was to edit a file called 'beryl-settings'.

If you are using KDE (ie kubuntu), then start a terminal session, then type

sudo nano /usr/bin/beryl-settings
enter your password
look for the line that says '#!/usr/bin/env python' and change 'python' to 'python2.4' (this is probably the very first line in the file)
press ctrl-x
press y
press enter

Now, restart X by pressing ctrl-alt-backspace. This is a graceful way to restart your X server. Rebooting can cause problems.

BTW, if you are using gnome instead of KDE, you may have to use some other command than 'sudo' above. This is the command that allows you to change things with root priveleges. I think it is gksu or something like that.

Good luck.

Once this movie I'm watching is done I'll try that command, but will that help me get beryl back or just the menu issue? Since I no longer have a beryl environment, is it worth even trying that option? I will once this movie is over, but there seems to be some other underlying issue. 

On  a side note, how long do you think Beryl is to being close to being a stable component of the Ubuntu experience?

---

### Post by jhenager on 2007-03-06
> **Jofaba said:**
> Once this movie I'm watching is done I'll try that command, but will that help me get beryl back or just the menu issue? Since I no longer have a beryl environment, is it worth even trying that option? I will once this movie is over, but there seems to be some other underlying issue. 

On  a side note, how long do you think Beryl is to being close to being a stable component of the Ubuntu experience?

Shame on you for putting a movie ahead of your computer! :popcorn:  

Re:side note.
Since Beryl/Compiz is so hardware dependent, I would think it may be some time before it goes mainstream. I wonder if a separate software package would be warranted? Possibly call it Bubuntu (Beryl + Ubuntu).
During the install, a script could check to see if supported ATI or nVidia hardware is present, and if not, launch Ubuntu with Gnome or Kubuntu. Just an idea.

---

### Post by Jofaba on 2007-03-06
Okay I made the change and rebooted x but Beryl environment is still unresponsive. I'm a little confused though, because I was under the impression that lines preceded by a "#" meant that they were comment lines and not active until the "#" was removed. Should I remove it from that line? 

Also, to clear up any confusion, when I said Xubuntu earlier I meant Kubuntu. 

A lot more information about what I changed last night. I changed quite a bit since I'm on a fresh install and have a lot of options that need "activation". 

First, I got dvd playback working after several attempts with libdvdcss2. "sudo /usr/share/doc/libdvdread3/install-css.sh" seems to have been what finally got it working. I also added several repositories while looking for the fix that were media based, and replaced the entire page with a repository list that I found while looking up media information. I can't find the page again but it was in the wiki and seemed legitimate. If anyone wants, I can copy/paste my repository collection here. 

I also fixed my resolution. 

During my search before posting here, I removed and reinstalled X as well as Beryl (with what claimed to be an absolute removal of all things Beryl related). However when going into the Beryl manager, all my settings appeared to be the same. Odd. 

I appreciate any help and discussion. This is a learning experience for me and I'm quite enjoying it. 

Well, I'm off to work (I mean my job, not to work on this problem), talk to you later.

(ps here's a link to my intro thread which includes my hardware specs) : [http://www.ubuntuforums.org/showthread.php?t=375574](http://www.ubuntuforums.org/showthread.php?t=375574)

---

### Post by Jofaba on 2007-03-06
Do any of this look like it might be conflicting? 

```

deb http://us.archive.ubuntu.com/ubuntu/ edgy main universe multiverse restricted

deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://medibuntu.sos-sts.com/repo/ edgy free
deb http://medibuntu.sos-sts.com/repo/ edgy non-free
deb-src http://medibuntu.sos-sts.com/repo/ edgy free
deb-src http://medibuntu.sos-sts.com/repo/ edgy non-free
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu edgy-commercial main

## Listen
#deb http://theli.free.fr/packages/ edgy listen
deb http://ubuntu.beryl-project.org/ edgy main
deb http://nvidia.limitless.lupine.me.uk/ubuntu edgy stable
```

---

### Post by Jofaba on 2007-03-06
Okay, well don't bother putting too much thought into that. I've decided that since the install is only a day old that it'd be faster to just start all over and keep a log of changes that I make. That way, instead of wondering how something got messed up, I'll most likely know exactly what change caused it. Whatever issues I discover, I'll post about in the bugs section. This way, I'll be doing my part to help the software development instead of just leeching off of it.

---

### Post by medley on 2007-03-06
> **Jofaba said:**
> Okay, well don't bother putting too much thought into that. I've decided that since the install is only a day old that it'd be faster to just start all over and keep a log of changes that I make. That way, instead of wondering how something got messed up, I'll most likely know exactly what change caused it. Whatever issues I discover, I'll post about in the bugs section. This way, I'll be doing my part to help the software development instead of just leeching off of it.

On one of the many times I screwed up my Beryl installation, I found this post in the Beryl forums. 

[http://forum.beryl-project.org/viewtopic.php?f=36&t=4046](http://forum.beryl-project.org/viewtopic.php?f=36&t=4046)

I copied/pasted the code sections into konsole and it fixed everything up. You could try this. It will install what is supposed to be the last stable version.

Good luck (again)

---

### Post by Jofaba on 2007-03-06
I could possibly try that if my computer was working. After loading the livecd and deleting the ubuntu partitions and starting over, I've since discovered that my hard drive is no longer any good. Some reading this might think that this explains the problems I've experienced but it isn't just that this drive is only a year or so old, but that it's a replacement drive and also the fourth drive that I've had fail in two years. I have the most rediculous luck with drives, both storage and optical. I've gone through 3 optical drives as well. I have no friggin idea why this happens to me. But either way, my drive no longer works. I'll try to do some stuff through terminal to clean the mbr but I fear it's a gonner. The really sad part? It's a 75gb Raptor and was working flawlessly until I installed linux. I'm not blaming linux of course, just stating facts. 

At this point I'm kinda stuck. I'll try to revive the disk until this weekend but even if that fails, I refuse to pay retail brick and mortar prices for a hard drive, so I'll have to order one and wait for it to arrive. I'm certinally getting sick of replacing hardware every couple of months though, I tell you what =P

---

### Post by Jofaba on 2007-03-07
After some reading on my lunch break, I'm becoming more and more convinced that I screwed up the mbr by dual booting. I'm burning a dos-based hard drive recovery program that can correct errors and write zeros (wonder how long that'll take). Hopefully that works. If it does, then I'm just going to do a single format and leave windows uninstalled for now.

---

