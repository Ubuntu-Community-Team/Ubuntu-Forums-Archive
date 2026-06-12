---
title: "CAQDAS, CMS, &amp; translation Packages"
date: 2006-08-02
forum: Desktop Environments
---

### Post by MishMich on 2006-08-02
Hi,

I have been searching on the web for something that will run on Ubuntu along the lines of NVivo.  I have tried NVivo, Nu*dist & Atlas.ti on XP/2000, but none of these work under Linux.  I have found a reference to something called QDA that runs under Ruby for RedHat & Debian ports, but nothing for Ubuntu itself.  I am new to Linux, and of two minds whether to look at trying it out.

So far, I have not had much luck with getting any multi-lingual translation software working on Ubuntu, and those that are out there seem poorly documented in English.  They install either Spanish or German Dictionaries, the German one says it can't find the Dictionary file, the Spanish one doesn't make it clear how to install other dictionaries (such as French).  They both seem to offer simple word or phrase translation; I am looking to get whole pages translated into English, then tidy them up by hand.  I don't want to get too tied up in the technicalities, as I know I will end up sucked into it for days.

I wasted a lot of time with failing to get Dreamwever Studio 8 running under Wine, only to find it doesn't.  Because of this I have not managed to find something I like as good as EndNote (but not properly explored Pybliographic yet).  I quite like the Project Management & OpenOffice Word Processor.  I am concerned about spending a lot of time trying to get something else working that doesn't seem well supported/documented for Ubuntu - or that entails using compilers, etc.

I wondered if anybody else has had any success with getting some sort of qualitative/textual analysis software running under Ubuntu; also, any advice on a good language translation tool would be appreciated (I administer a website that runs in all the main Western European languages).

I have started looking around for a Content Management System as well, and so far investigated Joomla & Xoops.  Neither seem to quite offer what I am looking for.  I wondered if anybody else has any suggestions for a Linux based CMS to run on Ubuntu.

After 2 weeks, I would dearly love to get to a point where I could leave Windows behind, and start making my own contributions to this community.

Mish

---

### Post by az on 2006-08-02
> **MishMich said:**
> I have started looking around for a Content Management System as well, and so far investigated Joomla & Xoops.  Neither seem to quite offer what I am looking for.  I wondered if anybody else has any suggestions for a Linux based CMS to run on Ubuntu.

[https://help.ubuntu.com/community/Drupal](https://help.ubuntu.com/community/Drupal)

---

### Post by MishMich on 2006-08-02
Thanks again, Azz.  I will check this out.

Mish

---

### Post by batido on 2007-05-13
I too would like to find a Qualitative Data Analysis Software package for Ubuntu.  Right now I use a qualitative software package called Weft QDA for the PC (the version for linux was just too difficult for me to install, I am a newbie).  I opened WEFT QDA for the PC in Ubuntu using WINE.  For those of you who don´t know, WINE is a WINdows Emulator that allows you (to varying degrees) to use a windows based program in a linux operating system.  I had Ubuntu 6.10 (edgy eft) and I had no problems installing WINE.  Though now I think that WINE comes pre-installed on Ubuntu 7.04 (fiesty fawn).


There are some problems with Weft QDA.  But it works pretty well under WINE.  I also should add that it is better than nothing.  Weft QDA is freeware.  I can´t afford programs like Nvivo, ethnograph, or atlas.ti.

If anyone finds any qualitative software alternative to Weft QDA for Ubuntu please post (or email me).  I check this thread often.

---

### Post by jalvesaq on 2007-10-21
> **batido said:**
> I opened WEFT QDA for the PC in Ubuntu using WINE.

Weft QDA can be installed on Ubuntu following these instructions:

[http://analyses.ishs.ulg.ac.be/logiciels/weft-qda.installation.debian.en.html](http://analyses.ishs.ulg.ac.be/logiciels/weft-qda.installation.debian.en.html)

For these instructions, I can add some notes:

1) The symbol "#" means that a command must be executed by root. On Ubuntu, we have to use "sudo". For example, the first command becomes:
```
sudo apt-get install ruby libzlib-ruby irb
```

2) Ubuntu 7.10 already has the package **rubygems**, and, thus, probably we can replace the steps that describe the installation of rubygems with:
```
sudo apt-get install rubygems
```

4) In my system (Gutsy amd64), weft-qda was not installed at /usr/bin, and the command to open it is:
```
ruby /var/lib/gems/1.8/bin/weft-qda.rb
```

5) We have to resize weft-qda windows when they are opened for the first time because they are too small to show all buttons and other widgets.

---

