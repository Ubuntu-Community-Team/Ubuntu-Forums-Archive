---
title: "Need a little help...."
date: 2009-02-24
forum: General Help
---

### Post by zeroemissions on 2009-02-24
Hey!

I have decided to try out linux and have around 15mins experience with xubuntu. I have had a look around these forums trying to find solutions to my problems but I'm struggling a bit. I'm fairly savvy with windows but that doesn't seem to be helping me much. I just need a little help to get on my feet :)

I would like to get my video drivers installed, I downloaded the latest ati drivers for my HD4870, which is the 
'ati-driver-installer-9.2-x86.x86_64.run' 
file but I don't know what to do with it. It is just opens a text window with a bunch of code in it. Have I go the right version of the drivers?

Second is installing open office. I have read the sticky on this but i can't find the files it refers to. The file I downloaded is
'OOo_3.0.1_LinuxIntel_install_wJRE_en-US.tar.gz' 
again, is this the right version?

Apologies for my stupid questions...

---

### Post by metalhead0010 on 2009-02-24
I'm not sure about the drivers but the tar.gz is like a zip file.  First unzip it using ark or whatever archiver came with xubuntu then compile it.  To compile it open your terminal emulator type
 cd [wherever you unzipped it]
Press enter and type
 ./configure 
Now type
 make
Press enter and type
Make install
Hope that helps, I can't give you a full tutorial right now.

---

### Post by mb_webguy on 2009-02-24
First, in reference to your video card.  You need to right-click the file and click Properties.  Go to the Permissions tab and check the box next to "Allow this file to run as a program".  Now you can double-click the file to run it.

As for OpenOffice, there's a better way to install it, though I'm going to have to tell you how to do it in the terminal since I'm not familiar enough with Xubuntu to tell you how to do it the graphical way.  Keep in mind that there is an easier way to do this, but this is the version that will work no matter which version of Ubuntu (e.g. Ubuntu, Kubuntu, or Xubuntu) you're using.

Open a terminal and type "sudo nano /etc/apt/sources.list".  Paste the following line at the end of the file.```
deb http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu intrepid main
```Btw, if you're not running 8.10 (Intrepid Ibex), you should change "intrepid" to whatever version of Xubuntu you're using.  When you're done, save and exit.

Now type "sudo apt-get update".  You're probably going to get an error message about missing GPG keys, and it will give you a number for the missing key.  Copy and paste the following commands, replacing "*number*" with the number in the error message.```
gpg --keyserver keyserver.ubuntu.com --recv *number*
gpg --export --armor *number* | sudo apt-key add -
```
After you've run these commands, type "sudo apt-get update" again.  This time it shouldn't give you any errors.  Now type "sudo apt-get install openoffice" to install OpenOffice 3.

This may seem like a complicated way to do this, but doing so will allow you to automatically get updates for OpenOffice as they are released, which you wouldn't get otherwise.

---

### Post by Wayne_V on 2009-02-24
a .run file is typically a shell archive.   try just "sudo sh <file>.run"

But I think you are going about things the hard way.   Take a look at /etc/apt/sources.list.  Uncomment the restricted, universe & multiverse entries -- it should look something like this (maybe xubuntu vs ubunt):
> #deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
#
# Google repository
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

# Google testing repository
deb [http://dl.google.com/linux/deb](http://dl.google.com/linux/deb) testing non-free
#
deb [http://ppa.launchpad.net/synce/ubuntu](http://ppa.launchpad.net/synce/ubuntu) intrepid main


Then you can just do:

sudo apt-get update
sudo apt-cache search openoffice
sudo apt-get install openoffice.org

to handle proprietary drivers:

apt-get install jockey-gtk

then:

sudo jockey-gtk

out of curiosity, why xubuntu vs gnome (ubuntu) or KDE (kubuntu) ?

---

### Post by konqueror7 on 2009-02-24
have tried first using *ubuntu native ati driver, its in System > Administration > Hardware...another method would be installing envy from the repos, this will automatically detect and install your video drivers...if you still want to run your downloaded file...type in the terminal,
```
cd <directory downloaded>
```
then,
```
chmod +x ati-driver-installer-9.2-x86.x86_64.run
```
then,
```
sudo sh ati-driver-installer-9.2-x86.x86_64.run
```

or just follow this guide on [ATI and Ubuntu]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")...

as for your openoffice, you've downloaded a different file, [this]("http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=3.0.1") is the file used in the guide...

---

### Post by zeroemissions on 2009-02-24
thanks for the replies guys! cheers!!

---

### Post by zeroemissions on 2009-02-24
> **Wayne_V said:**
> 

out of curiosity, why xubuntu vs gnome (ubuntu) or KDE (kubuntu) ?

I know nothing! HAHA, just experimenting. So what i'm using isn't a release right?

I think I have A LOT of reading to do!

---

### Post by mb_webguy on 2009-02-24
> **zeroemissions said:**
> I know nothing! HAHA, just experimenting. So what i'm using isn't a release right?

I think I have A LOT of reading to do!

What you have is fine.  It's just that Ubuntu is the main "flavor" of... well, Ubuntu.  Kubuntu and Xubuntu use different desktop environments and default applications.  Gnome (Ubuntu) and KDE (Kubuntu) are full-featured desktop environments, where Xfce (Xubuntu) is a more lightweight desktop environment better suited for systems with limited system resources.

Since Ubuntu, Xubuntu, and Kubuntu are all different flavors of the same distribution, however, you can easily switch from one desktop environment to another, or even have multiple installed at once.  If you ever want to try out Gnome, simply install the ubuntu-desktop package in Synaptic Package Manager.  Likewise, to try out KDE, install the kubuntu-desktop package.  Then at the login screen you can click the Options button and Select Session to choose which desktop environment you want to use.

---

### Post by Nano_ext3 on 2009-02-24
First, please be more helpful with your topics.

Seconds, here is the guide I followed works PERFECTLY!

[http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04](http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04)

---

### Post by zeroemissions on 2009-02-24
This place is full of helpful people!

Thanks for the tips, I am now installing the ubuntu package.

I will try to get openoffice going after that is done. I think it'll be easier that way.

All the advise is much appreciated, many thanks.

One other thing, perhaps for any Australians out there. Is the data Ubuntu downloads (updates and the like) through pipe or waix?

---

### Post by mb_webguy on 2009-02-24
If you're trying out Gnome, the installation of OpenOffice 3 will be much easier.  Just open System->Administration->Software Sources, go to the Third-Party Software tab, click Add, and paste the following line in the box.```
deb http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu intrepid main
```

Now right-click and download [this file]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x60D11217247D1CFF") to your computer.  Back in Software Sources, go to the Authentication tab, click Import Key File, and locate the file you just downloaded.

Now exit Software Sources (and update your software sources when it asks).  The Update Manager should now pop up telling you that some updates are available, which should include OpenOffice.  If not, just open up Synaptic Package Manager and install it from there.

---

