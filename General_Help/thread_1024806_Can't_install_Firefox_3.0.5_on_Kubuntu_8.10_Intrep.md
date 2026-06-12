---
title: "Can't install Firefox 3.0.5 on Kubuntu 8.10 Intrepid Ibex"
date: 2008-12-29
forum: General Help
---

### Post by zaratzara on 2008-12-29
Hello all,

First of all, I'd like to prefix this with a KDE n00b disclaimer. My knowledge of shell is also very limited.

I can't install Firefox 3.0.5 on Kubuntu 8.10 Intrepid Ibex. I downloaded the [tarball]("http://getfirefox.com/releases"), opened Adept and searched for firefox but was given no result. After unpacking the tarball, Adept still sees nothing. I decided to try running the 'firefox' shell script from bash, which returned this message: 

[FONT="Courier New"][FONT="Fixedsys"]The program 'firefox' is currently not installed.  You can install it by typing:
sudo apt-get install firefox-3.0[/FONT][/FONT]

Running [FONT="Courier New"][FONT="Fixedsys"]sudo apt-get install firefox-3.0[/FONT][/FONT] as it suggested gave me this:

[FONT="Courier New"][FONT="Fixedsys"]Reading package lists... Done                                                   
Building dependency tree                                                        
Reading state information... Done                                               
E: Couldn't find package firefox-3.0[/FONT][/FONT]

After a while of googling I learnt that, among other things, a lot of Firefox's recent update features don't gel very well with Linux so I was relieved to discover a Firefox 'manager' in the shape of [Ubuntuzilla]("http://ubuntuzilla.wiki.sourceforge.net/").

Trying to run the Ubuntuzilla debian package (ubuntuzilla-4.5.8-0ubuntu1-i386.deb) resulted in a string of unsatisfiable library dependencies, the first of which was libstc++5, which itself needed gcc-3.3-base... Ubuntuzilla then asked for libnotify-bin, which in turn asked for libnotify1... I was then asked for gdebi. gdebi says it needs gdebi-core, but after downloading and attempting to install the latest build of gdebi-core, it tells me that a newer version is already installed. This leaves me in a bit of a loop.

I have since gone back to the shell to try installing Firefox from scratch, and sudo apt-get gives me a new message now:

[FONT="Courier New"][FONT="Fixedsys"]E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
[/FONT][/FONT]
I don't understand what this means, but obviously some of the libraries are affecting the basic process here. Sadly, I don't know what else to do and am now utterly stuck.

I have found other people reporting issues with Firefox 3 under 8.10 Intrepid Ibex, but none as critical as this - most people see it in Adept after downloading and only run intro problems after installing it successfully.

It might be worth mentioning that for some reason or other my Kubuntu install did not chuck in all the bells and whistles: I've got Adept, Konqueror, Amarok, Dolphin etc. but OpenOffice, Wine, Synaptic and other fairly generic elements I would've expected aren't here.

Would appreciate any and all advice - Konqueror is killing me!

Regards,
Barney

---

### Post by oilchangeguy on 2008-12-29
you don't need to do all of this. simply click on add/remove (adept installer) should be under favorites. then click on internet, check the firefox box. and apply changes. and you're done.

---

### Post by mikewhatever on 2008-12-29
> **zaratzara said:**
> 
I can't install Firefox 3.0.5 on Kubuntu 8.10 Intrepid Ibex. I downloaded the [tarball]("http://getfirefox.com/releases"), opened Adept and searched for firefox but was given no result. After unpacking the tarball, Adept still sees nothing. I decided to try running the 'firefox' shell script from bash, which returned this message: 

[FONT="Courier New"][FONT="Fixedsys"]The program 'firefox' is currently not installed.  You can install it by typing:
sudo apt-get install firefox-3.0[/FONT][/FONT]

Running [FONT="Courier New"][FONT="Fixedsys"]sudo apt-get install firefox-3.0[/FONT][/FONT] as it suggested gave me this:

[FONT="Courier New"][FONT="Fixedsys"]Reading package lists... Done                                                   
Building dependency tree                                                        
Reading state information... Done                                               
E: Couldn't find package firefox-3.0[/FONT][/FONT]

Firefox 3.0.5 is indeed in the online Ubuntu repositories. You don't need to download tarballs from Mozilla or debs for Debian, they aren't necessarily made for Ubuntu. That leads me to a question, Is your computer online?

> After a while of googling I learnt that, among other things, a lot of Firefox's recent update features don't gel very well with Linux so I was relieved to discover a Firefox 'manager' in the shape of [Ubuntuzilla]("http://ubuntuzilla.wiki.sourceforge.net/").

Trying to run the Ubuntuzilla debian package (ubuntuzilla-4.5.8-0ubuntu1-i386.deb) resulted in a string of unsatisfiable library dependencies, the first of which was libstc++5, which itself needed gcc-3.3-base... Ubuntuzilla then asked for libnotify-bin, which in turn asked for libnotify1... I was then asked for gdebi. gdebi says it needs gdebi-core, but after downloading and attempting to install the latest build of gdebi-core, it tells me that a newer version is already installed. This leaves me in a bit of a loop.

Well, solving dependencies is nothing uncommon. Had you been connected, gdebi would have got the dependencies for you.

> I have since gone back to the shell to try installing Firefox from scratch, and sudo apt-get gives me a new message now:

[FONT="Courier New"][FONT="Fixedsys"]E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
[/FONT][/FONT]
I don't understand what this means, but obviously some of the libraries are affecting the basic process here. Sadly, I don't know what else to do and am now utterly stuck.

That means that Adept is still open while you are trying to use apt.

> I have found other people reporting issues with Firefox 3 under 8.10 Intrepid Ibex, but none as critical as this - most people see it in Adept after downloading and only run intro problems after installing it successfully.

That's not the way it works. You have to manually install whatever was downloaded manually.

> It might be worth mentioning that for some reason or other my Kubuntu install did not chuck in all the bells and whistles: I've got Adept, Konqueror, Amarok, Dolphin etc. but OpenOffice, Wine, Synaptic and other fairly generic elements I would've expected aren't here.

Not too familiar with Kubuntu, but I think wine is not among the default packages, and Synaptic is the same for Ubuntu that Adept is for Kubuntu.

---

### Post by nanotube on 2008-12-29
it looks like your repository list is not properly configured, so you are not seeing any packages. (either that or you are having problems with internet connectivity on that computer)

please post your repository list here, you should be able to find it in /etc/apt/sources.list

---

### Post by oilchangeguy on 2008-12-29
> **nanotube said:**
> it looks like your repository list is not properly configured, so you are not seeing any packages. (either that or you are having problems with internet connectivity on that computer)

please post your repository list here, you should be able to find it in /etc/apt/sources.list

not needed! firefox is there, in adept add/remove. i used it while i was running the live cd. before i installed kubuntu 8.10.

---

### Post by zaratzara on 2008-12-29
Thanks guys. I have been connected and Adept has not listed it - however I hadn't synchronized Adept's package indexer. Thanks for your patience!

---

