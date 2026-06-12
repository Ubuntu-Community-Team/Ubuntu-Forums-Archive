---
title: "E:The list of sources could not be read.'"
date: 2009-06-11
forum: General Help
---

### Post by adrian4design on 2009-06-11
Please Help,

I had some issues with a report I have been writing, I saved it from OO to .docx format but the formatting got screwed when I tried to open it in either OO or Word 07. I thought maybe upgrading to OO 3.1 may help as my splash screem say 3.0 ( I now know this doesn't change) I couldn't get any auto upgrade to work so I read a few posts etc. tried to follow a guide and now I have no OO and error messgaes.
I don't know if the error is me adding some souce or something I did in package manager or wether I have a disk that may be corrupting?

Any help please?

---

### Post by pmlxuser on 2009-06-11
Hey why not just reinstall OO . using synaptic package manager search of open office . if it shows that its installed uninstall it completely (mark for complete removal ) and then install it again should work. 

(on a lighter note , damn you screwed the whole OO for just one document. If you are working with OO its better to save first in *.odt format, make a copy then save in other formats. I have found out tha OO doesn't behave predicatbly when saving to other formats apart from those of open format.)

---

### Post by adrian4design on 2009-06-11
The error message I am getting is from the synaptec package manager and in my system tray (is that Win speak)?

Sorry for my delayed response I was trying to sort out a quick screen shot!!

I should have said I am good with computers but new to Unix I have been running a dual boot for a while now and am trying desperately to migrate but I find that particularly the compatibility of a few things a problem.

I have tried a couple of already threaded solutions on this forum  but I am not sure which now!!

---

### Post by bryncoles on 2009-06-11
i suspect you have added the PPa for open office, but not added the public key which allows you to use the PPA. 

does that make sense, or is it gobbledegook?

can you post a link to the guide you followed please?

---

### Post by x33a on 2009-06-11
hi next time please use the print screen button for a screenshot, use png or jpeg format.

on topic: post the output of
```
cat /etc/apt/sources.list
```

from the terminal.

---

### Post by adrian4design on 2009-06-11
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security multiverse
deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) jaunty main


Hope that helps

---

### Post by adrian4design on 2009-06-11
> **adrian4design said:**
> # deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security multiverse
deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) jaunty main


Hope that helps
[http://ubuntuforums.org/showthread.php?t=943135](http://ubuntuforums.org/showthread.php?t=943135)
[https://answers.launchpad.net/ubuntu/+question/67215](https://answers.launchpad.net/ubuntu/+question/67215)
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/376745](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/376745)

Some of the places I was looking for help and tried a few commands!
[B]
bryncoles[/B] - I kinda of know what you mean yes I added a key but I don't know how to "add the public key", here is the tab I was using to try and update OO ([http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml](http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml)).

---

### Post by x33a on 2009-06-11
```
gksudo gedit /etc/apt/sources.list
```

put # before the last line the ppa one, and save the file.

then run
```
sudo aptitude update
```

see if the error goes away.

---

### Post by adrian4design on 2009-06-11
> **x33a said:**
> ```
gksudo gedit /etc/apt/sources.list
```put # before the last line the ppa one, and save the file.

then run
```
sudo aptitude update
```see if the error goes away.
Doesn't seem to have worked, here is my terminal output!

adrian@adrian-desktop:~$ gksudo gedit /etc/apt/sources.list

adrian@adrian-desktop:~$ 
adrian@adrian-desktop:~$ sudo aptitude update
E: Type ‘echo’ is not known on line 1 in source list /etc/apt/sources.list.d/ppa.list
E: Type ‘echo’ is not known on line 1 in source list /etc/apt/sources.list.d/ppa.list
E: The list of sources could not be read.
E: Type ‘echo’ is not known on line 1 in source list /etc/apt/sources.list.d/ppa.list
E: The list of sources could not be read.
E: Type ‘echo’ is not known on line 1 in source list /etc/apt/sources.list.d/ppa.list
E: Couldn't read list of package sources
adrian@adrian-desktop:~$

---

### Post by x33a on 2009-06-11
hi, your screenshot isn't uploaded correctly.

anyway, try this:

```


sudo apt-get -f install
```

---

### Post by adrian4design on 2009-06-11
> **x33a said:**
> hi, your screenshot isn't uploaded correctly.

anyway, try this:

```


sudo apt-get -f install
```
adrian@adrian-desktop:~$ gksudo gedit /etc/apt/sources.list

adrian@adrian-desktop:~$ 
adrian@adrian-desktop:~$ sudo aptitude update
E: Type &#8216;echo&#8217; is not known on line 1 in source list /etc/apt/sources.list.d/ppa.list
E: Type &#8216;echo&#8217; is not known on line 1 in source list /etc/apt/sources.list.d/ppa.list
E: The list of sources could not be read.
E: Type &#8216;echo&#8217; is not known on line 1 in source list /etc/apt/sources.list.d/ppa.list
E: The list of sources could not be read.
E: Type &#8216;echo&#8217; is not known on line 1 in source list /etc/apt/sources.list.d/ppa.list
E: Couldn't read list of package sources
adrian@adrian-desktop:~$ sudo apt-get -f install
E: Type &#8216;echo&#8217; is not known on line 1 in source list /etc/apt/sources.list.d/ppa.list
E: The list of sources could not be read.
adrian@adrian-desktop:~$ 

I sussed the screenshot thing, I have to upload it I can't paste into the editor can I?


anyway sorry for the delays, I love the theory and the software of unix/opensource just wish I was better at it!!!!!

---

### Post by Soul-Sing on 2009-06-11
Maybe you could check this howto: [http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml](http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml)

You do have the proper ppa: deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) jaunty main

---

### Post by Soul-Sing on 2009-06-11
> **adrian4design said:**
> adrian@adrian-desktop:~$ gksudo gedit /etc/apt/sources.list

adrian@adrian-desktop:~$ 
adrian@adrian-desktop:~$ sudo aptitude update
E: Type ‘echo’ is not known on line 1 in source list /etc/apt/sources.list.d/ppa.list
E: Type ‘echo’ is not known on line 1 in source list /etc/apt/sources.list.d/ppa.list
E: The list of sources could not be read.
E: Type ‘echo’ is not known on line 1 in source list /etc/apt/sources.list.d/ppa.list
E: The list of sources could not be read.
E: Type ‘echo’ is not known on line 1 in source list /etc/apt/sources.list.d/ppa.list
E: Couldn't read list of package sources
adrian@adrian-desktop:~$ sudo apt-get -f install
E: Type ‘echo’ is not known on line 1 in source list /etc/apt/sources.list.d/ppa.list
E: The list of sources could not be read.
adrian@adrian-desktop:~$ 

I sussed the screenshot thing, I have to upload it I can't paste into the editor can I?


anyway sorry for the delays, I love the theory and the software of unix/opensource just wish I was better at it!!!!!

Do you have a sources.list.d next to a sources.list?

---

### Post by adrian4design on 2009-06-11
adrian@adrian-desktop:~$ gksudo gedit /etc/apt/sources.list

adrian@adrian-desktop:~$ 
adrian@adrian-desktop:~$ sudo aptitude update
E: Type &#8216;echo&#8217; is not known on line 1 in source list /etc/apt/sources.list.d/ppa.list
E: Type &#8216;echo&#8217; is not known on line 1 in source list /etc/apt/sources.list.d/ppa.list
E: The list of sources could not be read.
E: Type &#8216;echo&#8217; is not known on line 1 in source list /etc/apt/sources.list.d/ppa.list
E: The list of sources could not be read.
E: Type &#8216;echo&#8217; is not known on line 1 in source list /etc/apt/sources.list.d/ppa.list
E: Couldn't read list of package sources
adrian@adrian-desktop:~$ sudo apt-get -f install
E: Type &#8216;echo&#8217; is not known on line 1 in source list /etc/apt/sources.list.d/ppa.list
E: The list of sources could not be read.
adrian@adrian-desktop:~$ sudo apt-get -f install
E: Type &#8216;echo&#8217; is not known on line 1 in source list /etc/apt/sources.list.d/ppa.list
E: The list of sources could not be read.
adrian@adrian-desktop:~$ 

Still not havin it!!

Thanks for your time, could any of this be related to the fact I have a disk that, as of today when this message started, I can't mount?

I was under pressure to finish the report the other day, gave up and resorted to my XP laptop and have not used that PC after that shutdown I just switched the PC on today and that is what I got!!!!!

Thinking about it it's dual booting and I booted windows first today with no problems then rebooted to Ubuntu to fix this OO issue!

---

### Post by adrian4design on 2009-06-11
leoquant I am a little new to Ubuntu/unix, am I safe to upload my source list file?

---

### Post by Soul-Sing on 2009-06-11
> **adrian4design said:**
> leoquant I am a little new to Ubuntu/unix, am I safe to upload my source list file?

I think your sources.list is ok. Somehow the first ppa ¨line" in sources.list.d is "wrong"/causing trouble....We are warm solving this thing....

---

### Post by theozzlives on 2009-06-11
> **adrian4design said:**
> leoquant I am a little new to Ubuntu/unix, am I safe to upload my source list file?

If you're using UNIX you got problems, Ubuntu is Linux. I'd try to put a # in front of the first line that doesn't have one, save, exit and ```
sudo apt-get update
```

---

### Post by x33a on 2009-06-11
hi post the output of
```
gedit /etc/apt/sources.list.d/ppa.list
```

---

### Post by adrian4design on 2009-06-11
I am working on terminology - I like to try and sound like I know what I mean!!

txt from source list as follows:

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security multiverse
#deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) jaunty main

result of last command from

---

### Post by theozzlives on 2009-06-11
> **adrian4design said:**
> I am working on terminology - I like to try and sound like I know what I mean!!

No harm done, did you comment out line one and run update? What was the output?

---

### Post by adrian4design on 2009-06-11
adrian@adrian-desktop:~$ /etc/apt/sources.list.d/ppa.list
bash: /etc/apt/sources.list.d/ppa.list: Permission denied
adrian@adrian-desktop:~$ su
Password: 
root@adrian-desktop:/home/adrian# sudo sh ./oooupgrade.sh && rm ./oooupgrade.sh 
#PPA openoffice-pkgs
deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) jaunty main
gpg: requesting key 247D1CFF from hkp server keyserver.ubuntu.com
gpg: key 247D1CFF: "Launchpad PPA for OpenOffice.org Scribblers" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
OK
E: Type &#8216;echo&#8217; is not known on line 1 in source list /etc/apt/sources.list.d/ppa.list
E: Type &#8216;echo&#8217; is not known on line 1 in source list /etc/apt/sources.list.d/ppa.list
E: Type &#8216;echo&#8217; is not known on line 1 in source list /etc/apt/sources.list.d/ppa.list
E: The list of sources could not be read.
Segmentation fault
E: Type &#8216;echo&#8217; is not known on line 1 in source list /etc/apt/sources.list.d/ppa.list
E: Type &#8216;echo&#8217; is not known on line 1 in source list /etc/apt/sources.list.d/ppa.list
E: The list of sources could not be read.
E: Type &#8216;echo&#8217; is not known on line 1 in source list /etc/apt/sources.list.d/ppa.list
E: The list of sources could not be read.
root@adrian-desktop:/home/adrian#

---

### Post by adrian4design on 2009-06-11
x33a,

Output from your code:

/etc/apt/sources.list.d/ppa.list

Result:

root@adrian-desktop:/home/adrian# /etc/apt/sources.list.d/ppa.list
bash: /etc/apt/sources.list.d/ppa.list: Permission denied
root@adrian-desktop:/home/adrian#

---

### Post by adrian4design on 2009-06-11
theozzlives,

output from your code:

root@adrian-desktop:/home/adrian# sudo apt-get update
E: Type &#8216;echo&#8217; is not known on line 1 in source list /etc/apt/sources.list.d/ppa.list
root@adrian-desktop:/home/adrian# 

I have tried adding a # on the last line as someone said to(see post of list on page 2 of thread).

---

### Post by theozzlives on 2009-06-11
> **adrian4design said:**
> x33a,

Output from your code:

/etc/apt/sources.list.d/ppa.list

Result:

root@adrian-desktop:/home/adrian# /etc/apt/sources.list.d/ppa.list
bash: /etc/apt/sources.list.d/ppa.list: Permission denied
root@adrian-desktop:/home/adrian#

K, from the begining... type```
sudo gedit /etc/apt/sources.list.d/ppa.list
```, find the first line that dosent have a "#" in front of it (this is line 1). Put a # in front of it. save and exit, type ```
sudo apt-get update
```. Tell us what happened.

---

### Post by adrian4design on 2009-06-11
it has opened the editor with an error saying check my location "sources.list.d is a directory0", any idea?

---

### Post by theozzlives on 2009-06-11
> **adrian4design said:**
> it has opened the editor with an error saying check my location "sources.list.d is a directory0", any idea?

I edited my post, I forgot ppa.list

---

### Post by adrian4design on 2009-06-11
> **theozzlives said:**
> I edited my post, I forgot ppa.list
E: Malformed line 2 in source list /etc/apt/sources.list.d/ppa.list (dist parse)
root@adrian-desktop:/home/adrian# 

That was a different file to the one I opened before now, below is the txt copied from that file including my change:

#echo "#PPA openoffice-pkgs
deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) jaunty main" | sudo tee -a /etc/apt/sources.list.d/ppa.list




echo -e echo #PPA openoffice-pkgs
deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) jaunty main
echo "#PPA openoffice-pkgs
deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) $(lsb_release -sc) main" | sudo tee -a /etc/apt/sources.list.d/ppa.list
#PPA openoffice-pkgs
echo -e echo #PPA openoffice-pkgs
deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) jaunty main
#PPA openoffice-pkgs
deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) jaunty main
#PPA openoffice-pkgs
deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) jaunty main

---

### Post by theozzlives on 2009-06-11
> **adrian4design said:**
> E: Malformed line 2 in source list /etc/apt/sources.list.d/ppa.list (dist parse)
root@adrian-desktop:/home/adrian# 

That was a different file to the one I opened before now, below is the txt copied from that file including my change:

#echo "#PPA openoffice-pkgs
deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) jaunty main" | sudo tee -a /etc/apt/sources.list.d/ppa.list




echo -e echo #PPA openoffice-pkgs
deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) jaunty main
echo "#PPA openoffice-pkgs
deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) $(lsb_release -sc) main" | sudo tee -a /etc/apt/sources.list.d/ppa.list
#PPA openoffice-pkgs
echo -e echo #PPA openoffice-pkgs
deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) jaunty main
#PPA openoffice-pkgs
deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) jaunty main
#PPA openoffice-pkgs
deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) jaunty main

K, do that for all the lines that say echo and then update...

---

### Post by adrian4design on 2009-06-11
> **theozzlives said:**
> K, do that for all the lines that say echo and then update...
File now looks like this:

#echo "#PPA openoffice-pkgs
deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) jaunty main" | sudo tee -a /etc/apt/sources.list.d/ppa.list




#echo -e echo #PPA openoffice-pkgs
deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) jaunty main
#echo "#PPA openoffice-pkgs
deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) $(lsb_release -sc) main" | sudo tee -a /etc/apt/sources.list.d/ppa.list
#PPA openoffice-pkgs
#echo -e echo #PPA openoffice-pkgs
deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) jaunty main
#PPA openoffice-pkgs
deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) jaunty main
#PPA openoffice-pkgs
deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) jaunty main

terminal:
root@adrian-desktop:/home/adrian# sudo gedit /etc/apt/sources.list.d/ppa.list
root@adrian-desktop:/home/adrian# sudo apt-get update
E: Malformed line 2 in source list /etc/apt/sources.list.d/ppa.list (dist parse)

---

### Post by theozzlives on 2009-06-11
```
sudo apt-get update
```

---

### Post by x33a on 2009-06-11
hi i know you must be really getting tired, so i suggest you delete this file for now, if you really don't want oo 3.1 for now. we'll fix that later.

for now
```
sudo rm /etc/apt/sources.list.d/ppa.list
```

then
```
sudo aptitude update
```

---

### Post by adrian4design on 2009-06-11
this is wahat I get from your command theozzzlives.

E: Malformed line 2 in source list /etc/apt/sources.list.d/ppa.list (dist parse)

---

### Post by adrian4design on 2009-06-11
x33a,

That seems to be working to do something..

Thats great the updater is now running but I have something broken:

secure shell client, an rlogin/rsh/rcp replacement

This is the portable version of OpenSSH, a free implementation of
the Secure Shell protocol as specified by the IETF secsh working
group.

thanks for all your help.

Will the add remove tab in the launch menu pick up OO 3.1

---

### Post by theozzlives on 2009-06-11
try```
sudo dpkg --configure -a
``` and take out the line causing the problem on sources.list

---

### Post by theozzlives on 2009-06-11
All I did for 3.1 was```
sudo apt-get dist-upgrade
```the splash stayed the same but if I go to about, it's 3.1

---

### Post by adrian4design on 2009-06-11
theozzlives,

are you referring to my comment on the broken item?

x33a & ozz,

it sounds important to me and I seem to have the options to remove, mark for complete removal and reinstall, what do you recommend?

---

### Post by x33a on 2009-06-11
try complete removal, that will remove the configuration files as well, and when you install it again, there won't be any pending problems.

---

### Post by adrian4design on 2009-06-11
Do you have any idea what it is or what I did?

I gotta learn!!!

Thanks everyone for yor time.

---

### Post by theozzlives on 2009-06-11
> **x33a said:**
> try complete removal, that will remove the configuration files as well, and when you install it again, there won't be any pending problems.

you'll wind up with 3.0 again

---

### Post by x33a on 2009-06-11
> **theozzlives said:**
> you'll wind up with 3.0 again

yes, but i was thinking a reinstall will be a better option to fix broken stuff.

---

### Post by theozzlives on 2009-06-11
> **x33a said:**
> yes, but i was thinking a reinstall will be a better option to fix broken stuff.

I'd just fix it, of course that's what I do :-) it is hard to troubleshoot when you aren't in front of the computer.

---

### Post by adrian4design on 2009-06-11
Hey guys thanks for all that help ealier, sorry I up and dissapeared my baby daughter decided I had to go play with her!!!!!

Anyways, I have now got rid of all those issues from before, now I have found these forums I have a couple of things I would still like a hand with if anyone has the patience?
I hope I am in the right place to ask these things?

Synaptic PK manager is showing lots of updates, some 481, what does that mean do I install them all?

it says at the bottom: 26900 listed, o broken 481 to install...

Do I need to do this regularly? Do they build up if not checked?  I thought that was what the update manager did?

Update manager doesn't show anything!!!
How do I install OO 3.1 now? OO and OOCalc still show in Launch menu but none of the other suites.
How do I sync evolution calender with googlecal?
Why can I as of today no longer mount a disk, I tried to edit a config file to auto mount two disks and I think that could be it?


Any help with any of these is really appreciated, I don't know anyone who has or can use any Linux distro's. All the techs and geeks I know think I am mad and it's too much agro to migrate, more fool them I say!!!

Thanks again love this distro and forum and all the opensource support, stick it gatesy!!!!

---

### Post by x33a on 2009-06-11
hi adrian,

i would suggest that you create different threads for different problems. but, first try searching the forums or google for a solution, and post only if you can't find a solution to your problem.

---

### Post by colau on 2009-06-11
@adrian4design
Post a new thread with different question.

---

### Post by Soul-Sing on 2009-06-12
> **colau said:**
> @adrian4design
post a new thread with different question.
+1

---

