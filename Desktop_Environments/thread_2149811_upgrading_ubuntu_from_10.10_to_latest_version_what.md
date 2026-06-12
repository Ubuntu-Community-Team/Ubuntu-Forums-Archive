---
title: "upgrading ubuntu from 10.10 to latest version? what should i do?"
date: 2013-05-30
forum: Desktop Environments
---

### Post by adeee on 2013-05-30
Title says it all.I have ubuntu 10.10 version and i want to upgrade to latest one.i start the update manager but it show me toupgrade to 11.04. and i want 12.04 or above. I am downloading ISO image of 13.04 version. and i will burn it. but is thier any way instead of fresh install i may upgrade the ubuntu from the cd. if i install it will lose my software and all the data. so plz siuggest me what should i do?Thanxs

---

### Post by ajgreeny on 2013-05-30
In theory you could update one version at a time, but that would involve five separate upgrade procedures, each with a possibility of problems and each involving a big download of packages and several hours of work on your part to check things out after each upgrade.

I think you will simply have to accept that it is quicker in the long run to clean install to whichever version you want, and go from there.  Make sure everything is backed up, and consider a separate /home partition when you install this time, as it makes these updates of the OS a lot easier.
[Separate home at install.]("http://www.psychocats.net/ubuntu/installseparatehome")

---

### Post by grahammechanical on 2013-05-30
You cannot upgrade from 10.10 to 12.04 directly. We can upgrade from one LTS release to the next - 10.04 to 12.04 .Or upgrade from one release to the next - 10.10 to 11.04 to 11.10 to 12.04. That is the path that you would have to go. You should back up all your important files anyway

Before you fresh install 13.04 or upgrade from 12.04 to 12.10 and then to 13.04, you should understand that 13.04 has only 9 months support. Anyone using 13.04 would need to upgrade to 13.10 in November of this year otherwise they will be using an End Of Life Ubuntu for 3 months until 14.04 is released.

[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

Regards.

---

### Post by adeee on 2013-05-30
> **grahammechanical said:**
> 

Before you fresh install 13.04 or upgrade from 12.04 to 12.10 and then to 13.04, you should understand that 13.04 has only 9 months support. Anyone using 13.04 would need to upgrade to 13.10 in November of this year otherwise they will be using an End Of Life Ubuntu for 3 months until 14.04 is released.

[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

Regards.

so what should i upgrade?12.04 or 13.04?

---

### Post by grahammechanical on 2013-05-30
It is your choice. We cannot make the decision for you. We try to give you sufficient information for you to understand what will happen with each option.

Many of us would not recommend upgrading but doing a fresh install of Ubuntu 12.04. It has 4 more years of support. Or you could upgrade to 14.04 in May of 2014 and get 5 years support from then on.

If you install 13.04 you will need to do 2 upgrades to get to 14.04. Our important files are at risk every time we upgrade. So, we need to make copies of those files. Which we would have to do if we did a fresh install.

Remember, upgrades are designed and tested in going from one default installation of Ubuntu to another default installation. Many people modify Ubuntu and the upgrade process is unable to work properly because of all the changes made to the operating system.

Regards.

---

### Post by kansasnoob on 2013-05-30
> **adeee said:**
> so what should i upgrade?12.04 or 13.04?

IMHO Precise (aka: 12.04.2) is the best choice because it's supported until April 2017. I've mentioned that in my Precise Classic (no effects) thread:

[http://ubuntuforums.org/showthread.php?t=1966370&page=20&p=12665934#post12665934](http://ubuntuforums.org/showthread.php?t=1966370&page=20&p=12665934#post12665934)

Also you may be able to "upgrade" using the live image:

[ATTACH=CONFIG]243282[/ATTACH]

I've personally had good luck with that option, ***if it's offered***, **[COLOR="#FF0000"]but before performing any upgrade or reinstallation you should always create a backup of any valuable data to an external source[/COLOR]**!

The data you don't backup is always the data you lose!

Note: I realize that screenshot shows upgrading from 11.10 to 12.04 but if ubiquity is working correctly you *should* be able to upgrade from any version of Ubuntu to another :)

---

### Post by adeee on 2013-05-30
i always want to backup my data but i always failed to backup the data and then its all lost. what i want to back up is [Apache, mysql, php( with configurations ) all the softwares i download(these are too many) all the upgrades i download, all the browser sessions.  ] they are all lost and every time when i reinstall the ubuntu i will start as a  newbie to ubuntu. obviously i have additional space for my  personal files  and movies. which is not under the ubuntu installation.so
[COLOR=#FF0000]Can any body tell me what is the best procedure of backing up the files? and where should i take or store the "Back up files"? and how to apply the backup files so that in one click i will get all the softwares and updates back...[/COLOR]

thank you very much for your kind support. i am happy you help me.

---

### Post by mansonfan78 on 2013-05-30
You could try installing Mint Backup in Ubuntu.  This site tells you how: [http://www.webupd8.org/2010/07/install-mintbackup-linux-mint-backup.html](http://www.webupd8.org/2010/07/install-mintbackup-linux-mint-backup.html)  and use it to backup your files and software selection (ideally to an external drive).  You would then install the new version of Ubuntu and install Mint Backup in it and then restore everything.  Just make sure you know beforehand how to install Mint Backup in BOTH versions of Ubuntu before starting.

---

