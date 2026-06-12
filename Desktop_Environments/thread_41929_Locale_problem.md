---
title: "Locale problem"
date: 2005-06-15
forum: Desktop Environments
---

### Post by Jonathan2007 on 2005-06-15
I have posted about this problem earlier but it got only one response. Here is a shorter version.

Some time a while ago I upgraded to libc6 to version 2.3.2.ds1-21 because some package depended upon it. When I did this it must have automatically removed the locales package without me knowing.

Now when I try to install stuff it gives me a bunch of locale errors. If I try to reinstall the locales package it says it depends upon glibc-2.3.2.ds1-20ubuntu13 (which I have found out is a virtual package of libc6 2.3.2.ds1-20ubuntu13). But I don't have libc6 2.3.2.ds1-20ubuntu13 I have the 21 version so I can't reinstall locales.

I am sure others have run into this. If anyone can help or knows anything about thsi please post.

---

### Post by sethmahoney on 2005-06-15
Have you added any repositories since you first installed Ubuntu?

---

### Post by Jonathan2007 on 2005-06-15
Yep I added the all the ones that UbuntuGuide.org suggested. I have also added some to get the latest version of aMule installed.

P.S. Thanks for the reply.  ;-)

---

### Post by btdown on 2005-06-15
I have the EXACT same problem because of the amule upgrade. The "Can't set locale "" messages are really annoying. I'm looking for a fix as well.
BT

---

### Post by Knome_fan on 2005-06-15
Generally, it isn't a good idea to install a different version of libc, as this will inevitably break things. 

So the best thing to do imho would be to get rid of the new version and install the normal hoary version again.

About the packages that need the newer libc, most of the time recompiling these packages (for example using dpkg-buildpkg) is a better idea and won't break things. And you can of course always ask the backports guys if they can backport the package you want/absolutely need.

Edit:
I just checked and there is a newer version of amule in backports (2.0 I think). So if that's the version you want, using the one from backports should be the easiest solution.

---

### Post by Jonathan2007 on 2005-06-15
[QUOTE=btdown]I have the EXACT same problem because of the amule upgrade. The "Can't set locale "" messages are really annoying. I'm looking for a fix as well.
BT[/QUOTE]
Yeah that is the message I get. But I also get errors when i try to install things using apt-get and KPackage.

[QUOTE=Knome_fan]Generally, it isn't a good idea to install a different version of libc, as this will inevitably break things. 

So the best thing to do imho would be to get rid of the new version and install the normal hoary version again.

About the packages that need the newer libc, most of the time recompiling these packages (for example using dpkg-buildpkg) is a better idea and won't break things. And you can of course always ask the backports guys if they can backport the package you want/absolutely need.

Edit:
I just checked and there is a newer version of amule in backports (2.0 I think). So if that's the version you want, using the one from backports should be the easiest solution.[/QUOTE]
Ok. Thanks for the answer. You are awesome. I will uninstall version libc6 21 and put 20 back and then use the backported aMule version. Thanks again.

EDIT: Woah!!! I won't uninstall libc6 as that seems like it will take a crapload of packages away (and I want those). So I will probably just try to install libc6 20 over the 21 and hopefully that will work.

---

### Post by Knome_fan on 2005-06-15
[QUOTE=Jonathan2007]
EDIT: Woah!!! I won't uninstall libc6 as that seems like it will take a crapload of packages away (and I want those). So I will probably just try to install libc6 20 over the 21 and hopefully that will work.[/QUOTE]

Ooops, my bad. You are of course right, uninstalling it is a bad idea, I meant downgrading to the hoary version.

---

### Post by Jonathan2007 on 2005-06-15
[QUOTE=Knome_fan]Ooops, my bad. You are of course right, uninstalling it is a bad idea, I meant downgrading to the hoary version.[/QUOTE]
Good thing I caught that. Haha. Anywho I can't seem to find the deb for libc6 2.3.2.ds1-20ubuntu13. Could someone post a link to it? And then I just use sudo dpkg -i package_name.deb right? Thanks for all your help.

---

### Post by Knome_fan on 2005-06-15
I think the easiest way would be to use synaptic, search for libc6, click on the *evil* libc6, then choose package (I think it should be package, I'm on a german system here), choose force version from the menu and then choose the hoary version.

This should also give you a good warning about potential problems.

---

### Post by Jonathan2007 on 2005-06-15
I tried to force the backported package but it said it couldn't fetch [http://backports.ubuntuforums.org/backports/dists/hoary-backports/universe/binary-i386/amule_2.0.0-1~5.04ubp1_i386.deb](http://backports.ubuntuforums.org/backports/dists/hoary-backports/universe/binary-i386/amule_2.0.0-1~5.04ubp1_i386.deb). When I type that url in on FireFox it wants a username and password?

---

### Post by Knome_fan on 2005-06-15
Ah, the problem is, that you still have the old url for the backport repository. This doesn't work anymore, as only mirrors work now.

Get rid of the old backport entries in /etc/apt/sources.list and add the following lines:
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted

---

### Post by Jonathan2007 on 2005-06-15
Well I tried those new repositories and they worked. I got aMule and Locales both installed fine. But when I first edited my sources.list and then refreshed the package info in Synaptic I got a crapload of errors coming from Synaptic about those new backport repositories. Is that ok? Maybe you need to see the rest of my sources.list. Here it is.

```
deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted 


deb http://us.archive.ubuntu.com/ubuntu/ hoary main restricted 
deb-src http://us.archive.ubuntu.com/ubuntu/ hoary main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hoary-updates main restricted 
deb-src http://us.archive.ubuntu.com/ubuntu/ hoary-updates main restricted 

 ## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu/ hoary main restricted 
deb-src http://us.archive.ubuntu.com/ubuntu/ hoary main restricted 

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hoary-updates main restricted 
deb-src http://us.archive.ubuntu.com/ubuntu/ hoary-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hoary universe 
deb-src http://us.archive.ubuntu.com/ubuntu/ hoary universe 

deb http://security.ubuntu.com/ubuntu/ hoary-security main restricted 
deb-src http://security.ubuntu.com/ubuntu/ hoary-security main restricted 

deb http://security.ubuntu.com/ubuntu/ hoary-security universe 
deb-src http://security.ubuntu.com/ubuntu/ hoary-security universe 

deb http://archive.ubuntu.com/ubuntu/ hoary multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ hoary multiverse 

deb ftp://ftp.nerim.net/debian-marillat/ stable main 
deb ftp://ftp.nerim.net/debian-marillat/ unstable main 
deb ftp://ftp.nerim.net/debian-marillat/ testing main 

deb ftp://ftp2.caliu.info/backports/ hoary-backports main universe multiverse restricted
deb ftp://ftp2.caliu.info/backports/ hoary-extras main universe multiverse restricted

deb http://kubuntu.org/hoary-kde341/ hoary-updates main 
```

---

### Post by Knome_fan on 2005-06-15
What errors did you get exactly?

If you just edited your source.list and then started synaptic it will complain about not being able to use the new repositories (or something like that). However, that's no problem and after refreshing once this message should be gone.

Edit: Oh, and you might consider commenting out the marillat repositories, as they are known to cause problems right now.

---

### Post by Jonathan2007 on 2005-06-15
[QUOTE=Knome_fan]What errors did you get exactly?

If you just edited your source.list and then started synaptic it will complain about not being able to use the new repositories (or something like that). However, that's no problem and after refreshing once this message should be gone.

Edit: Oh, and you might consider commenting out the marillat repositories, as they are known to cause problems right now.[/QUOTE]
 OK. Yea I will try refreshing them again later and hopefully I won't get all those errors. Thanks for all your time and help. You have made me stay with Kubuntu.

---

