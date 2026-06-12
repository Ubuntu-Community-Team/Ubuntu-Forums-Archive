---
title: "Repositorys....HELP!!!!"
date: 2006-03-03
forum: Desktop Environments
---

### Post by PaintballMan10988 on 2006-03-03
So I was told to update my repository , and i followed these directions. 

Synaptic Package Manager 
To enable the extra Universe and Multiverse repositories 
1.Settings -> Repositories 
2.Click the Settings button 
3.Tick Show disabled software sources 
4.On the Repositories dialog box click Add. There are three separate repositories; Breezy Badger, Security Updates and Updates. Select each repository and check Officially supported, Restricted copyright, Community maintained (Universe) and Non-free (Multiverse). Ensure you click OK between each repository to save your changes 
5.You should now see checkboxes next to each repository, scroll through the list and ensure they are all checked 
To add backports and PLF (new versions of many applications. Unsupported. May contain illegal packages. Use at own risk.) 
1.Settings -> Repositories 
2.Click on Add and then Custom 
3.Paste the following five lines into the box and Click Add Repository, one line at a time: 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras main restricted universe multiverse
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free 
To refresh the list of known packages (equivalent to apt-get update) 


After this, it started telling me this, 

E: Type 'breezy-backports' is not known on line 36 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.


Now it wont let me add any new repositories, or anything.

Help???


Thanks so much,

Mike

---

### Post by souteneur3190 on 2006-03-03
go to syntaptic and press reload

---

### Post by PaintballMan10988 on 2006-03-03
When i hit reload it says...


The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

????

Total Ubuntu newbie......


Mike

---

### Post by TristanMike on 2006-03-03
Would you be so kind as to post your sources.list here? You can use ```
gedit /etc/apt/sources.list
``` and we can see where the problem may lie.

---

### Post by PaintballMan10988 on 2006-03-03
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe main restricted multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
breezy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
breezy-backports main restricted universe multiverse

deb [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras main restricted universe multiverse
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free

---

### Post by Ramses de Norre on 2006-03-03
This is weird.. all those repo's seem to work in firefox..
Could you post the output of sudo apt-get update? That usually gives more detailled error messages.

---

### Post by PaintballMan10988 on 2006-03-03
That gave me this...


mike@Typhoon:~$ sudo apt-get update
E: Type 'breezy-backports' is not known on line 36 in source list /etc/apt/sources.list
mike@Typhoon:~$



I have no idea what i am doing.  Thanks to everyone for the help,

Mike

---

### Post by Ramses de Norre on 2006-03-03
Change this: ```
deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe
breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu
breezy-backports main restricted universe multiverse
```
to this: ```
deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
```

---

### Post by PaintballMan10988 on 2006-03-03
I...uh...

How?

lol, sorry for my total newbie'ness

Thanks again,

Mike

---

### Post by Ramses de Norre on 2006-03-03
Do ```
sudo gedit /etc/apt/sources.list
``` in terminal.

Then search the lines I gave you (it's line 36 and following like the error messages said) and change them like I did (just make one line of them).
I think that should fix it ;)

---

### Post by PaintballMan10988 on 2006-03-03
Ok, that fixed it.  Thanks!!!

Still cant play yahoo pool! Any ideas, it says i need the java runtime enviroment.

I really want to play pool! 

All help is greatly apreciated,

Mike

---

### Post by Ramses de Norre on 2006-03-03
[http://ubuntuforums.org/showthread.php?t=76754]("http://ubuntuforums.org/showthread.php?t=76754")
(Beware: the installer on the site is a newer version so change the version  number in all the commands!)

---

### Post by PaintballMan10988 on 2006-03-03
I have the file DL'ed to my desktop, but i dont know whatthis means...

After downloading, cd to where you downloaded the file and run:


cd? Wha?

Lol, thanks again for the help.


Mike

---

### Post by Ramses de Norre on 2006-03-03
cd stands for change directory, so they mean you need to set your current directory to the one you downloaded the file to.
To do so: type cd path_to_directory.
eg. cd ~/Desktop will make your current directory to /home/username/Desktop.
(~ stands for /home/username/ and is typed quikly in terminal with page down).

---

### Post by PaintballMan10988 on 2006-03-03
It all works! OMG thank you sooooo much.  You have been very helpfull, YES!  Now its time for yahoo pool.....
Thanks again,

Mike

---

