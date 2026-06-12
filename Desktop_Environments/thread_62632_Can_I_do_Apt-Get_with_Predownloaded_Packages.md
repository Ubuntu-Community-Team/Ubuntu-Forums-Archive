---
title: "Can I do Apt-Get with Predownloaded Packages?"
date: 2005-09-05
forum: Desktop Environments
---

### Post by sandmanfvr on 2005-09-05
Ok, I am dialup and some packages are like 30 megs.  Can I download these packages at work (I am a Sytem Admin and have high speed at work) and then bring them home and do apt-get to install them?  I want to install wine, but that is alot and other things I want to install are bigger.  I did wait 45 minutes for the w32 codecs, but I was just wondering if there was another way around this.  Thanks.

---

### Post by cwaldbieser on 2005-09-05
[QUOTE=sandmanfvr]Ok, I am dialup and some packages are like 30 megs.  Can I download these packages at work (I am a Sytem Admin and have high speed at work) and then bring them home and do apt-get to install them?  I want to install wine, but that is alot and other things I want to install are bigger.  I did wait 45 minutes for the w32 codecs, but I was just wondering if there was another way around this.  Thanks.[/QUOTE]
I think you have to use the "dpkg" command for installing local .deb files.

---

### Post by mcmuffy on 2005-09-05
sudo dpkg -i filename.deb

---

### Post by Hairy_Palms on 2005-09-05
the way to do it is make a local repository 
[http://www.ubuntuforums.org/showthread.php?t=42862](http://www.ubuntuforums.org/showthread.php?t=42862) shows you how

---

### Post by braveerudite on 2005-09-05
[QUOTE=mcmuffy]sudo dpkg -i filename.deb[/QUOTE]

I had the same question.  

1.  If I use the "dpkg -i filename.deb" method will it also show me the dependencies needed for proper install? and will they be downloaded automaticly if needed any?

2. Do I have to place the pakage I want to install in an specific folder on the file system before installation?

3. If I type "dpk -i filename.deb"  don't I also need to type the path name were the pakage is store on my computer so it can find it and install it?  or will it find it no matter where is store?

I'll be greatful to know this mysteries.

---

### Post by az on 2005-09-05
[QUOTE=braveerudite]I had the same question.  

1.  If I use the "dpkg -i filename.deb" method will it also show me the dependencies needed for proper install? and will they be downloaded automaticly if needed any?

2. Do I have to place the pakage I want to install in an specific folder on the file system before installation?

3. If I type "dpk -i filename.deb"  don't I also need to type the path name were the pakage is store on my computer so it can find it and install it?  or will it find it no matter where is store?

I'll be greatful to know this mysteries.[/QUOTE]

1- No, it won't.  It will leave the package uninstalled, but if you do
sudo apt-get -f install, it will then use apt to fetch any dependancies and install them, then finish installing the deb you downloaded.  If the dependancies are not in the apt repositories, then it will just remove the uninstallable package.

2- No.

3-  dpkg -i whatever.deb will try to install "whatever.deb" in the current directory.  If is cannot find it there it will give you and error.  You can also do

sudo dpkg -i /home/elmo/Desktop/download/whatever.deb

Use tab completion when you type at the console.

type dpkg -i /h (and then hit tab, it will complete the /home part.  Keep hitting tab and you will get the hang of it.

---

### Post by braveerudite on 2005-09-05
[QUOTE=azz]1- No, it won't.  It will leave the package uninstalled, but if you do
sudo apt-get -f install, it will then use apt to fetch any dependancies and install them, then finish installing the deb you downloaded.  If the dependancies are not in the apt repositories, then it will just remove the uninstallable package.
[/QUOTE]

1. You said to use "-f " when installing the pakage that way it would look for the dependencies needed.  But how would that line look like???

Is it something like this?:

apt-get -f -i dpk filename.deb


2. Is there a command to see all the pakages install?

---

### Post by doclivingston on 2005-09-05
[QUOTE=braveerudite]1. You said to use "-f " when installing the pakage that way it would look for the dependencies needed.  But how would that line look like???

Is it something like this?:

apt-get -f -i dpk filename.deb[/QUOTE]

```
sudo dpkg -i filename.deb
sudo apt-get -f
```

The "apt-get -f" asks apt to fix the current packes; which installs any required dependencies, or uninstalls the package if the dependencies can't be satisfied.

---

