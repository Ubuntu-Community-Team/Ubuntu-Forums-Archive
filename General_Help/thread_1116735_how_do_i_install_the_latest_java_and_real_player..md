---
title: "how do i install the latest java and real player."
date: 2009-04-05
forum: General Help
---

### Post by tanveerahmed2k8 on 2009-04-05
well im on linux ubuntu 8.10 and i want to know how to install the latest java
but i dont understand the terminal stuff..
and when i go to the sun java site i downloaded a java for linux but when i double click it, it says 
Could not display "/home/tanveer/Desktop/jre-6u13-linux-i586-rpm.bin".
There is no application installed for this file type

ALso when i downloaded real player 11 gold from the firefox site and double clicked it, it said 
Could not display "/home/tanveer/Desktop/RealPlayer11GOLD.bin".
There is no application installed for this file type.
someone please help me , im a windows person and dont understand none of this terminal and sudo stuff.

---

### Post by JAlexoid on 2009-04-05
As for Java, you don't need to do the installs/upgrades/updates manually. Just open Add/Remove Programs and search for Java. Select and install the one that is found.

You need to run those .bin files.
To do that first of all, you need to set the "Allow executing file as program".
To do that, you need to Right click the file and open the "Properties" window.
At the bottom of the Permissions tab, you will se a checkbox.
Check it and click Close.

Then you can double click the file and it should display a dialog asking what to do with that file.
You will still need to Run in terminal.


* I expect you are using Gnome, the default one in Ubuntu, not Kubuntu and not Xubuntu

---

### Post by albinootje on 2009-04-05
> **tanveerahmed2k8 said:**
> well im on linux ubuntu 8.10 and i want to know how to install the latest java

Do you need the full Java or do you need the Java plugin for Firefox ?
And are you using the 32- or 64-bit Ubuntu installation ?
The package "ubuntu-restricted-extras" will install Java, Acrobat Reader and Skype for you.
The package "sun-java6-plugin" will install the Java plugin on 32-bit Ubuntu.

Please read this for installing software in Ubuntu :
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
Using add/remove or Synaptic Package Manager is *the* way to make installing software in Ubuntu easy and much less painfull for beginners than randomly searching the internet and download .tar.gz files.
>  ALso when i downloaded real player 11 gold from the firefox site and double clicked it, it said 
Could not display "/home/tanveer/Desktop/RealPlayer11GOLD.bin".


There is a deb package for RealPlayer mentioned here :
[http://ubuntuexperiment.wordpress.com/2008/11/10/installing-realplayer-on-ubuntu-810/](http://ubuntuexperiment.wordpress.com/2008/11/10/installing-realplayer-on-ubuntu-810/)
It should be a matter of downloading the deb package and, after downloading, double click on it.

---

### Post by wpshooter on 2009-04-05
> **tanveerahmed2k8 said:**
> well im on linux ubuntu 8.10 and i want to know how to install the latest java
but i dont understand the terminal stuff..
and when i go to the sun java site i downloaded a java for linux but when i double click it, it says 
Could not display "/home/tanveer/Desktop/jre-6u13-linux-i586-rpm.bin".
There is no application installed for this file type

ALso when i downloaded real player 11 gold from the firefox site and double clicked it, it said 
Could not display "/home/tanveer/Desktop/RealPlayer11GOLD.bin".
There is no application installed for this file type.
someone please help me , im a windows person and dont understand none of this terminal and sudo stuff.

Are you really sure that you want to install RealPlayer in the first place ?  I have found that installing RealPlayer in Ubuntu can be problematic, i.e. cause more problems than it solves !!!

---

### Post by albinootje on 2009-04-05
> **wpshooter said:**
> Are you really sure that you want to install RealPlayer in the first place ?  I have found that installing RealPlayer in Ubuntu can be problematic, i.e. cause more problems than it solves !!!

What do you mean by that ?
I don't like RealPlayer at all myself, but if people want it, there's not an easy all-in-one-app which can replace it.
Besides that, RealPlayer comes as a deb package too now, and version 11 is out (From oct.2008).

---

### Post by albinootje on 2009-04-05
[Edited this, because I forgot I had a media addon for Firefox installed which made totem pop up too]

For the OP, I recommend installing this package, in case you haven't :
```

sudo apt-get install ubuntu-restricted-extras

```
and take a look at Medibuntu :
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
and then install the "w32codecs" package.

And.. I prefer the gecko-mediaplayer over the totem plugin.

---

### Post by oldos2er on 2009-04-05
> **tanveerahmed2k8 said:**
> well im on linux ubuntu 8.10 and i want to know how to install the latest java
but i dont understand the terminal stuff..
and when i go to the sun java site i downloaded a java for linux but when i double click it, it says 
Could not display "/home/tanveer/Desktop/jre-6u13-linux-i586-rpm.bin".
There is no application installed for this file type

ALso when i downloaded real player 11 gold from the firefox site and double clicked it, it said 
Could not display "/home/tanveer/Desktop/RealPlayer11GOLD.bin".
There is no application installed for this file type.
someone please help me , im a windows person and dont understand none of this terminal and sudo stuff.

 For Realplayer, open a terminal and run these commands one at a time:
```
cd Desktop
chmod a+x RealPlayer11GOLD.bin
sudo ./RealPlayer11GOLD.bin
```
 This will install Realplayer in /opt , and should create a menu entry in Applications, Sound & Video.

 For Java, unless you absolutely need the latest version, stick to the repositories. See [http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html)

---

### Post by tanveerahmed2k8 on 2009-04-07
i have now got real player working and java installed, thanks people! !

---

### Post by Benbow on 2009-04-07
Many thanks also from me from me, I had been having a load of problems which this thread covered including receiving BBC radio in France with iplayer. (I use Jaunty)

I am now a very happy bunny, thankyou, thankyou, THANKYOU!!:p

---

