---
title: "Single home partition, access with 10.04 and 11.04 multiple distriutions."
date: 2011-04-26
forum: Desktop Environments
---

### Post by IPEX-731BA5DD06 on 2011-04-26
Senario. I've set up a separate Data partition, [Creating a separate home partition in Ubuntu during installation]("http://www.psychocats.net/ubuntu/installseparatehome")

Now I wish, if I'm able too, to access this partition of Data with both my 10.04 LTS edition and the new 11.04 Edition of Ubuntu.

I tried once, using the methods above, to gain access to that partition, but it just denied me access to the 11.04 installation.

I edited the Fstab file in \media\ubuntu 11.04\etc\fstab, and changed back to regain access.* Mount ubuntu 11.04 first to access it*

Am I able to configure my system, that both distributions, can access the same \Data partition.

If so How would I go about it.

I have 2 separate login names for the 2 distributions, but I want to access the same \Data partition, folders,  using either one. Same programs, games, and e-mail accounts.

Also how would I set up Evolution, so that both operating systems use the same e-mail database, saving me from having mail in both, and no idea of where any of it is.

I've read numerous posting on this, but either they don't apply, are just too technical, or only relate to 8.04 at best.

---

### Post by pauljwells on 2011-04-26
I have a similar arrangement, except running 10.10 and 11.04. I have a different username set up on each system so there are two folders showing in /home

Both users are number 1000 so the permissions allow me to read and write on both despite the different usernames (look in the users item in system settings for the user number, 1000 is default for the first user)

I find it best to set it up this way because there may be different config files in one release that do not work with the other - applets in panels for example.

I haven't tried this, but for things like evolution databases, there will be a .evolution directory or similar (I use Thunderbird so I don't know for sure) What you could try is to set up evolution on one release and then make a HARD unix link to the files in .evolution directory in the other home folder.

[http://en.wikipedia.org/wiki/Hard_link]("http://en.wikipedia.org/wiki/Hard_link")

I think the code would be something like:

ln /home/user_on_10_04/.evolution/file /home/user_on_11.04/.evolution/file

This would OVERWRITE whatever is in the second directory with a hard link to the first one.

Like I say, this is just a guess, I haven't tried it...

In Nautilus, select 'view hidden files' to see all the config directories

---

### Post by oldfred on 2011-04-26
I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

The actual user settings are small. My /home is 1GB with about 3/4 of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root). 
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the  /data partition.

Shared /data -see post #4 oldfred
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

Opposing viewpoint on separate data partitions - post14 srs5694:
[http://ubuntuforums.org/showthread.php?t=1738065](http://ubuntuforums.org/showthread.php?t=1738065)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

Another way to share:
kansasnoob's sharing and Morbius1 use of bindfs
[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)
HowTo: Create shared directory for local users (with bindfs).
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)

---

### Post by IPEX-731BA5DD06 on 2011-04-30
Further update of all this, I've gotten the 11.04 Desktop to boot, the old default desktop, no unity and DON'T UPDATE THE DRIVERS TO 173.14.22 

Tried linking this install to home, NO NO NO NO

Tried a fix I saw of 

chown -R * username:username * /home/*username*

chmod 644 /home/*username*/.dmrc
chmod 644 /home/*username*/.ICEauthority

either permission denied, no user or when it was accepted one time, didn't load it.

Any other suggestions please ):P

---

### Post by oldfred on 2011-04-30
I thought the 173 series drivers were for the very old nVidia cards. The recommended one worked just find for me.

If you did not select your /home partition as part of the install you have to do the same commands as the move /home instructions, except you can skip the first few that copy your home to a separate partition.

Three similar sets of instruction, the only real difference is which command is used to copy:
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership
To move /home uses rsync  (create mount may be missing)
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

You run the commands to update ownership/permissions after you have your old /home correctly mounted as your new /home.
Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

---

### Post by IPEX-731BA5DD06 on 2011-06-15
So simple the answer, just like I like it. Only took me 1 month of thinking about doing it before I actually tried it.

Scenario:

 2 Operating distributions, with which I wish to use the same data partition and programs (read games)

Separate home partition installed, can be either done at installation, (simpler) or via this method detailed [COLOR=Lime][ Here ]("http://www.psychocats.net/ubuntu/separatehome")[/COLOR]

Distributions used:

Ubuntu 10.04.2 LTS Edition (me likes)
Ubuntu 11.04 Short term (Me liking very much)

So how do I do this.

Solution:

Assumptions: you've installed the 1st operating system and set up a separate home partition, upon which you've stored you games, e-mail, etc as per instruction above or just through home.

1. Install 2nd operating system, in this case it was 11.04 O O

2. At stage of installing 3rd partition for the new operating system, Tag you EXISTING home partition as home for the new installation. (/home) [B][U]DO NOT FORMAT THIS PARTITION ](*,) [-X
[/U][/B]
3. _**USE the same desktop name**_   :shock: This is very important, it will _**AUTOMATICALLY ASSIGN**_ A different UUID number for the user, I've got 1000, and 1001 for my 2

4. Install the operating system.

All things being correct, it should now boot up you new operating system, using you existing desktop, wall paper, browser defaults, e-mail settings.

If it doesn't, look for the obvious;
Differing desktop names, Fred =/ fred
You didn't assign home on the partitioning stage. (/HOME)
You versions of Ubuntu mightn't support this simple methodology.


*Gratuitous Praise* :mrgreen: Ubuntu is actually a very user friendly operating system. It offers, unbelievably, simple GUI solutions. 

People are very helpful here, Thanks to all who've given solutions ):P. But really, NOW, with 11.04, its quite simple, straight forward, and easy. Just how I like it.

---

