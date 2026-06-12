---
title: "Help with 9.04 upgrade"
date: 2009-04-23
forum: General Help
---

### Post by GabrielsHorn314 on 2009-04-23
Hey guys, I was trying to upgrade to 9.04 real quick today, but these errors showed up. I was wondering if anyone could help me with my problem. It's not really an emergency but I would like to check out what new 9.04 stuff has. Thanks for the help in advance, here are the errors (3 in total) ...

W:Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


, W:Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


, E:Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by HankB on 2009-04-23
If you haven't already read these, you may find help here:
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

If you are already familiar with that, then provide a description of what you're doing to upgrade.

-hank

---

### Post by GabrielsHorn314 on 2009-04-23
that page doesn't really help much because it doesn't go up to 9.04 and im trying to do a very basic upgrade. When i get this error message, i am in update manager and click on upgrade next to " New distribution release '9.04' is available", then after about 5 minutes those errors appear and the upgrade shuts down. thats about all the info I would know to produce on the matter. thanks for the help hank.

---

### Post by HankB on 2009-04-24
That page did mention that they don't recommend upgrading more than one generation. From your information it looks like you might be trying to upgrade from Hardy to Jaunty - skipping Intrepid. If so, that's not something that is recommended.

Do you have CD's selected in your Software Sources? I ask because that's mentioned in the error message. It may be that the upgrade manager is trying to include them and it probably shouldn't.

-hank

---

### Post by GabrielsHorn314 on 2009-04-24
i am on 8.10 right now, i know it says 8.04 but i havent switched any info, and i dont know why it would say that in the error message. How can i check if i have CD's selected in your Software Sources? what can i do about this? thanks so much for the help hank.

---

### Post by HankB on 2009-04-24
> **GabrielsHorn314 said:**
> i am on 8.10 right now, i know it says 8.04 but i havent switched any info, and i dont know why it would say that in the error message. How can i check if i have CD's selected in your Software Sources? what can i do about this? thanks so much for the help hank.

Have you been updating your 8.10 install regularly? If not, you probably should before you try to update.

Check sources at System -> Administration -> Software Sources.

Or you can edit /etc/apt/sources.list (make a backup copy first just in case.)

best,
hank

---

### Post by GabrielsHorn314 on 2009-04-24
I have been updating regularly. just for your information here are my settings under software sources updates.

Checked:
 Important security Updates
 Recommended updates
 Check for updates: daily
 Only notify about available updates
 Show new distribution releases : Normal releases

although sometimes when i do update i get the same error messages, but it never effected any of my downloads before until now.

---

### Post by GabrielsHorn314 on 2009-04-24
these are the error messages i get when leaving this software sources update window:

Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by HankB on 2009-04-24
Can you post the contents of /etc/apt/sources.list? I'm thinking that a previous update (from hardy) has left something in there that the present GUI is not dealing well with.

In particular, the first line of mine is
```
# deb cdrom:[Ubuntu-Netbook-Remix 9.04 _Jaunty Jackalope_ - Release i386 (20090421)]/ jaunty main multiverse restricted
```

The '#' at the beginning of the line means that this  line will not be processed. If you have any lines that start with "deb cdrom:..." I would likewise comment them as I don't think you want them in there now. In fact, there should probably be no hardy sources (unless there is some specific reason you have some hardy source enabled.)

-hank

---

### Post by tom56 on 2009-04-24
> **GabrielsHorn314 said:**
> Hey guys, I was trying to upgrade to 9.04 real quick today, but these errors showed up. I was wondering if anyone could help me with my problem. It's not really an emergency but I would like to check out what new 9.04 stuff has. Thanks for the help in advance, here are the errors (3 in total) ...

W:Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


, W:Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


, E:Some index files failed to download, they have been ignored, or old ones used instead.

Go to System->Administration->Software Sources, and untick any references to the install CDs in the "Ubuntu Software" and "Third Party Sources" tabs.

Here's a screenshot showing what I mean

---

### Post by GabrielsHorn314 on 2009-04-24
heres what mine looks like. nothing to click/unclikc

---

### Post by GabrielsHorn314 on 2009-04-24
hank, sorry i didnt see urs at first. 


deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) intrepid-security restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) intrepid-security restricted main multiverse universe #Added by software-properties

---

### Post by HankB on 2009-04-24
> **GabrielsHorn314 said:**
> hank, sorry i didnt see urs at first. 
No worries. It looks like there is stuff in your sources.list that the GUI is not showing - the first line in particular. You should comment out the lines I have highlighted since you are no longer running Hardy. After that, do an update and an upgrade and then when everything is right, have a go at upgrading to Jaunty.

To the best of my  somewhat limited knowledge, you don't generally have more than one version active at any point in time.
> 
**deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted**
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
**deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse**
**deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse**

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
**deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner**
**deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner**

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) intrepid-security restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) intrepid-security restricted main multiverse universe #Added by software-properties

---

### Post by GabrielsHorn314 on 2009-04-24
should i delete those lines or just put the # symbol in front?

---

### Post by tom56 on 2009-04-24
> **GabrielsHorn314 said:**
> heres what mine looks like. nothing to click/unclikc

Did you check the "Third Party Sources" tab?

---

### Post by GabrielsHorn314 on 2009-04-24
i did check the third party tab and unchecked the first thing, but it still didnt do anything.

---

### Post by GabrielsHorn314 on 2009-04-24
hank, i cant edit the file, i get this message:

Could not save the file /etc/apt/sources.list.
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

---

### Post by HankB on 2009-04-24
> **GabrielsHorn314 said:**
> should i delete those lines or just put the # symbol in front?
Either way - just save a backup copy as insurance. (I would delete as I can't imagine a reason you would want them back.)

-hank

---

### Post by tom56 on 2009-04-24
> **GabrielsHorn314 said:**
> i did check the third party tab and unchecked the first thing, but it still didnt do anything.

When you tried Update Manager again, did you make sure to click "Check"? This refreshes the package list and will make sure it won't try to install from the CD, which is what it is complaining about.

If that doesn't work then carry on editing the file manually. You need to open a terminal, or hit Alt-F2 and enter this:
```
gksu gedit /etc/apt/sources.list
```

You seem to be using 8.10 (Intrepid Ibex) - is that right? If so, you need to delete every line that references Hardy (8.04).

---

### Post by GabrielsHorn314 on 2009-04-24
thanks, i got the first line to get removed, and that seems to be making a difference. i cant really edit the file, so the other 4 lines are still in there.  i did an upgrade, and got no errors, and now im trying 9.04 and i havent gotten any errors yet. ill let u know in about 3 hours if it goes through. thanks so much for your help hank.

---

### Post by HankB on 2009-04-24
> **GabrielsHorn314 said:**
> hank, i cant edit the file, i get this message:

Could not save the file /etc/apt/sources.list.
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

You cannot edit system files as a regular user. You have to use 'sudo' to get temporary root privileges. Try:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.save
sudo gedit /etc/apt/sources.list

```

And then:
```
sudo apt-get update
sudo apt-get dist-upgrade

```
You might have to repeat the last command until there are no more error or warning messages. If there are, please post them here.

-hank

---

### Post by GabrielsHorn314 on 2009-04-24
ok, i edited the file, deleted the 5 lines, and grabbed a new update. this seems like it probably solved the problem, but i cant be sure until i have 9.04 fully downloaded.

---

### Post by tom56 on 2009-04-24
EDIT: nevermind

---

### Post by GabrielsHorn314 on 2009-04-24
although i am no longer getting any error messages, when i hit check in update manager and then show for individual files, a lot of them say failed, even though it goes through, and nothing happens.

---

### Post by HankB on 2009-04-24
> **GabrielsHorn314 said:**
> although i am no longer getting any error messages, when i hit check in update manager and then show for individual files, a lot of them say failed, even though it goes through, and nothing happens.
Can you run "sudo apt-get update" in a terminal and post the results?

-hank

---

### Post by GabrielsHorn314 on 2009-04-24
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

---

### Post by HankB on 2009-04-24
> **GabrielsHorn314 said:**
> E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory
You have to close the GUI before you run command line programs that access the same resources (local apt database.)

---

### Post by GabrielsHorn314 on 2009-04-24
cory@cory-desktop:~$ sudo apt-get update
[sudo] password for cory: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release             
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages
Reading package lists... Done

---

### Post by HankB on 2009-04-24
> **GabrielsHorn314 said:**
> cory@cory-desktop:~$ sudo apt-get update
[sudo] password for cory: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
.
.
.
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages
Reading package lists... Done

Looks fine. Where do the error messages show up?

---

### Post by GabrielsHorn314 on 2009-04-24
when hitting check in update manager, many of the responses are "failed" instead of "Hit" or "Done". I was just wondering if this was a problem before updating to 9.04

---

### Post by HankB on 2009-04-24
Looks like you should be OK to proceed.

---

### Post by GabrielsHorn314 on 2009-04-24
ok great, im downloading now, ill let u know in a few hours if it works. thanks a lot for your help, theres no way i would have been able to figure that out on my own.

---

### Post by GabrielsHorn314 on 2009-04-24
Upgrade worked like a charm. thanks for the help hank

---

### Post by HankB on 2009-04-24
> **GabrielsHorn314 said:**
> Upgrade worked like a charm. thanks for the help hank
Great - I'm glad to hear that everything went well. You're welcome.

best,
hank

---

### Post by lunamystry on 2009-04-27
I also need help with upgrading. Synaptic does not work and I am using a uninversity proxy to access the internet. Apt does not work, I noticed that it stopped working on upgrade day when I got an error that I need proxy authentication. It worked before I don't know why it stopped. 

Synaptics gives a failed on some packages and an error Translation_ZA or somrething of the sort.

---

