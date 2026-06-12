---
title: "All-In-One Packages for Ubuntu!!!"
date: 2005-07-02
forum: Desktop Environments
---

### Post by Prudentissimus on 2005-07-02
Hello!

  If there is such a thing, would you not be intrigued?!

-

---

### Post by Stemp on 2005-07-02
Hi,
What do you mean by "all in one package" ?

---

### Post by Prudentissimus on 2005-07-02
[QUOTE=Stemp]Hi,
What do you mean by "all in one package" ?[/QUOTE]
 All the packages on 1 DVD.

---

### Post by XDevHald on 2005-07-02
[QUOTE=Prudentissimus]All the packages on 1 DVD.[/QUOTE]
 I see what you mean, but still a little lost on how this would benefit?

---

### Post by Xian on 2005-07-02
[QUOTE=BB]I see what you mean, but still a little lost on how this would benefit?[/QUOTE]
1 user on dialup + 1 friend with Broadband + 1 DVD Burner = [img]http://my.opera.com/forums/images/smilies/party.gif[/img]

---

### Post by bored2k on 2005-07-02
[QUOTE=Xian]1 user on dialup + 1 friend with Broadband + 1 DVD Burner = [img]http://my.opera.com/forums/images/smilies/party.gif[/img][/QUOTE]
 You could create your own DVD. I always have backup of my downloaded .debs. With one singly command, all of them get deployed to their respective folder, and after that, a single dist-upgrade is a painless process. Great for users like me who reinstall their distro(Ubuntu) when they find nothing else to do.

There's also an official DVD containing every file in main.

---

### Post by Xian on 2005-07-02
[QUOTE=bored2k]There's also an official DVD containing every file in main.[/QUOTE]
Wouldn't want to go far beyond main less we also end up with [14](http://cdimage.debian.org/debian-cd/3.1_r0a/i386/iso-cd/) CD's.
But hey, that good burnin'. :)

---

### Post by Kyral on 2005-07-03
[QUOTE=bored2k]You could create your own DVD. I always have backup of my downloaded .debs. With one singly command, all of them get deployed to their respective folder, and after that, a single dist-upgrade is a painless process. Great for users like me who reinstall their distro(Ubuntu) when they find nothing else to do.

There's also an official DVD containing every file in main.[/QUOTE]
 Dude, whats the command to do that?

---

### Post by bored2k on 2005-07-03
[QUOTE=Kyral]Dude, whats the command to do that?[/QUOTE]
 There would be a million+1 ways to do that, being the easiest:

1. Backing repository info/files:
```
sudo tar zcvf backup.tgz /etc/apt/ /var/lib/apt/ /var/cache/apt/
```
2. Burn this file to a disc (using your favorite software).

3. To restore your repository info/files:
- In your cdrom/dvdrom folder (possibly by cd /media/cdrom0):
```
sudo tar zxvf backup.tgz -C /
```

[http://ubuntuguide.org/#backuprestoredownloadedrepositoriescache](http://ubuntuguide.org/#backuprestoredownloadedrepositoriescache)

---

### Post by Sionide on 2005-07-03
[http://mrbass.org/linux/ubuntu/](http://mrbass.org/linux/ubuntu/)

Is talking about this? The Ubuntu add-on cd and/or add-on zip?

---

### Post by Prudentissimus on 2005-07-03
[QUOTE=Sionide][http://mrbass.org/linux/ubuntu/](http://mrbass.org/linux/ubuntu/)

Is talking about this? The Ubuntu add-on cd and/or add-on zip?[/QUOTE]
 What is the Addon CD? Is it containing almost all of the files in Package.Ubuntu.com?

Can someone mail me a DVD / CD of all the IMPORTANT/USEFUL packages in Ubuntu? I'm sick of downloading things and later find out i need another file. (I'll pay you money through Paypal).

---

### Post by Morimando on 2005-07-03
Look at [http://ubuntuguide.org](http://ubuntuguide.org) and download the "Add-On CD". With this you should've most needed programs. I think it should be an official part of Ubuntu, as a second CD or such.
If you need the whole set of programs.... well it's ~70Gigs, because you'll have to download the whole mirror ^^

---

### Post by Prudentissimus on 2005-07-03
[QUOTE=Morimando]Look at [http://ubuntuguide.org](http://ubuntuguide.org) and download the "Add-On CD". With this you should've most needed programs. I think it should be an official part of Ubuntu, as a second CD or such.
If you need the whole set of programs.... well it's ~70Gigs, because you'll have to download the whole mirror ^^[/QUOTE]
 so it's kinda like Service Pack in Windows?

---

### Post by Morimando on 2005-07-04
No, Service Pack fixes error and sometimes adds extra functionality. The Add-On CD for Ubuntu adds media support, some vital players and stuff, to make Ubuntu able to play almost every media format and to guarantee a complete Desktop Experience (e.g. it adds the most needed programs that don't come with "normal" Ubuntu)

---

### Post by AllenGG on 2005-07-04
Think !  (imagine Aretha Franklin singing here)
Prude has a wonderfull point,  namely, how can any one of us create a , probably, custom DVD, that's bootable, that is a complete package. Sure, not a one size fits all, but: one that will fit many users and machines.  Of course dividing this up by "need".
Let's say we're doing it for our old aunt Martha.  She has a P4 with 256MB ram, a 40G HDD, a CD burner, maybe she got it from "Dell" !  DVD that also works, bootable, that even good old Auntie can boot.
This might also be usefull for a non-profit organization that has many NON-networked desktops.
One of my desktop units is an "anybody can use this" standalone. But it took me a few hours to figure out which packages to add. (I'm slow)
Best suggestion wins a case of "Blue".

---

### Post by jiyuu0 on 2005-07-04
Add-On-Cd, Read:
[http://ubuntuforums.org/showthread.php?t=30147&highlight=add-on-cd](http://ubuntuforums.org/showthread.php?t=30147&highlight=add-on-cd)

Basically, the add-on-cd contains the UbuntuGuide and the apps mentioned in it's add-on section

It also comes with an install script, that will help u install most of the common apps and configure your multimedia to play properly

Other than that, ubuntu security fixes packages are in it too...

---

### Post by Prudentissimus on 2005-07-04
[QUOTE=Sionide][http://mrbass.org/linux/ubuntu/](http://mrbass.org/linux/ubuntu/)

Is talking about this? The Ubuntu add-on cd and/or add-on zip?[/QUOTE]
 Dude, this is sweet, it was EXACTLY What I have been looking for. Anything more alike? Thanks.!!!

---

### Post by XDevHald on 2005-07-07
[QUOTE=bored2k]There would be a million+1 ways to do that, being the easiest:

1. Backing repository info/files:
```
sudo tar zcvf backup.tgz /etc/apt/ /var/lib/apt/ /var/cache/apt/
```
2. Burn this file to a disc (using your favorite software).

3. To restore your repository info/files:
- In your cdrom/dvdrom folder (possibly by cd /media/cdrom0):
```
sudo tar zxvf backup.tgz -C /
```

[http://ubuntuguide.org/#backuprestoredownloadedrepositoriescache](http://ubuntuguide.org/#backuprestoredownloadedrepositoriescache)[/QUOTE]
 Always got a nice trick up your sleeve eh bored? :D

---

### Post by sb73542 on 2005-07-07
[QUOTE=BB]Always got a nice trick up your sleeve eh bored? :D[/QUOTE]
 Add-on CD is now discontinued.  That stinks.

---

### Post by bored2k on 2005-07-07
[QUOTE=sb73542]Add-on CD is now discontinued.  That stinks.[/QUOTE]
 BB meant a custom CD of your/my creation ;).

And yes -mr Dell hotshot- BB, I try to learn something new every now and then ;).

---

### Post by Morimando on 2005-07-08
[QUOTE=sb73542]Add-on CD is now discontinued.  That stinks.[/QUOTE]
Why?

---

### Post by bored2k on 2005-07-08
[QUOTE=Morimando]Y??[/QUOTE]
 Legal Issues.

---

