---
title: "apt-get gone crazy ??"
date: 2005-07-06
forum: Desktop Environments
---

### Post by Hoekstone on 2005-07-06
Hello guys,

I have a problem with apt-get. When I want to install a .deb package it almost always has some dependencies. So I use apt-get install to install the packages needed. But it always tells me to use apt-get -f install without specifying a package. So I do that, and the right packages are shown to be installed, but it wants to uninstall a CRAZY ammount of packes, which isn't necessary. (like openoffice, libxml, libjpeg ... ) So I cancel, and have to search and download all the deb packages.... Also it ALWAYs gives the warning that I have to use apt-get -f install. So I can't use apt anymore  :mad: 

Can you help me?

---

### Post by angkor on 2005-07-06
Could you post your /etc/apt/sources.list?

---

### Post by reuben on 2005-07-06
You probably have too high a version of some vital package, and it's trying to roll that package back. Try doing apt-get update / apt-get upgrade to bring everything to the most recent versions, and then make your changes again. Also, use synaptic rather than apt-get, since it gives you more information more quickly about how the dependencies are calculated.

---

### Post by Hoekstone on 2005-07-08
this is my sources.list file:
------------------------------------------------------------------------------------------------------------------------------
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

# Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted


deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

deb [http://people.debian.org/~akumria/woody](http://people.debian.org/~akumria/woody) ./

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

# Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted


deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

deb [http://people.debian.org/~akumria/woody](http://people.debian.org/~akumria/woody) ./
----------------------------------------------------------------------------------------------------------------------

I used apt-get update an upgrade, but without result.

---

### Post by angkor on 2005-07-08
I'm no expert but I don't think it's wise adding Debian woody repos to your apt sources.list. Maybe you should try without em.

---

### Post by Hoekstone on 2005-07-09
I deleted the last line of my sources.list file and saved it. Then I did sudo apt-get update. But the problem still persists.

---

### Post by Hoekstone on 2005-07-09
Is there a way to just clear apt-get ??

---

### Post by crashtest on 2005-07-09
[QUOTE=Hoekstone]Is there a way to just clear apt-get ??[/QUOTE]

From the apt-get man page:

clean  clean clears out  the  local  repository  of  retrieved  package
              files.   It   removes   everything   but   the  lock  file  from
              /var/cache/apt/archives/  and  /var/cache/apt/archives/partial/.
              When  APT is used as a dselect(8) method, clean is run automati&#8208;
              cally. Those who do not use dselect  will  likely  want  to  run
              apt-get clean from time to time to free up disk space.

       autoclean
              Like  clean,  autoclean  clears  out the local repository of re&#8208;
              trieved package files. The difference is that  it  only  removes
              package  files that can no longer be downloaded, and are largely
              useless. This allows a cache to be maintained over a long period
              without  it  growing  out  of  control. The configuration option
              APT::Clean-Installed will prevent installed packages from  being
              erased if it is set to off.

By the way, I'm not sure this will help your particular problem.

---

### Post by Pippen101 on 2005-07-09
I just had the same problem but I used Synaptic. 

Was trying to install the newest verison of bzflag which wasnt in my repos.

This is what I did:

1.) So I downloaded the .deb package

2.) dpkg bzflag.deb -> wouldnt config the package

3.) Ran Synaptic-> told me there were broken pacakages

4.) Told Synaptic to fix packages

Then when I went to exit it asked my to apply all the changes. I took a look and it wanted to remove OO 2.0 and a whole bunch of stuff

Hope this helps others to try and solve this problem.

---

### Post by der_joachim on 2005-07-10
[QUOTE=Hoekstone]I deleted the last line of my sources.list file and saved it. Then I did sudo apt-get update. But the problem still persists.[/QUOTE]

Have you tried ```
aptitude -f install
```? This usually fixes any dependency problems. Just really really watch out: sometimes it tries to throw away healthy packages.

---

### Post by Hoekstone on 2005-07-10
I looked in Synaptic, and it told me that there were four broken packages:
- libc6-dev
- libc6-i386
- libfontconfig1-dev
- locales

that explains why it wants to remove all those healthy packages... The problem is that I don't see why he thinks these packages listed here are broken.  :-?

---

### Post by Hoekstone on 2005-07-13
Anyone ? Can anyone help me to tell apt-get that it doesn't have to uninstall all those packages ???

---

### Post by radeon4 on 2005-07-13
I am pretty new as well but looking at your source.list it looks like you have several dupliacte repositorites.   You might want to double check it delet any duplicates and then runt apt-get update one more time.  Again I am not sure it will help just a observation.

---

### Post by Hoekstone on 2005-07-13
There aren't dupliacte repositories ! Read a bit better next time.

---

### Post by crispingatiesa on 2005-07-13
[QUOTE=Hoekstone]There aren't dupliacte repositories ! Read a bit better next time.[/QUOTE]
 Yes there are, hoary universe and hoary-security universe.

---

### Post by Hoekstone on 2005-07-13
What is duplicated exactly then,. what to remove. I don't understand it. Sorry ...

---

### Post by dewey on 2005-07-13
You've duplicated all your repositories, and included debian repositories (not recommended) try using:
```
# Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```
Only, then using ```
sudo apt-get update | sudo apt-get upgrade
```
And post if the problem persists.

I'm pretty sure having the debian repo always on gave you newer package and library versions than is supported by the ubuntu distro, and it's libraries.  Mixing repositories of distros isn't officially supported.  (I do use some debian packages, but I don't keep the repo open all the time, I install the specific package I need, and comment it back off)

---

### Post by Hoekstone on 2005-07-15
Well I used your sources.list. Then I did sudo apt-get update and then apt-get upgrade. But after apt-get upgrade it only advises me to use apt-get -f install and does nothing  :roll: . Well I did that and aborted because it still wanted to delete the half of my distribution.

---

### Post by Hoekstone on 2005-07-19
Anyone ?  :roll:

---

### Post by angkor on 2005-07-19
I really don't know man, sorry. It could be that mixing repos just messed up your system a little too much...Maybe someone else comes along with a fix...good luck.

---

### Post by DonVla on 2005-07-20
hello,

i got a similar problem. i explained it in this thread:

[http://ubuntuforums.org/showthread.php?t=49862](http://ubuntuforums.org/showthread.php?t=49862)

first i thought it was a kde problem. but now i think it's a global problem; perhaps a problem with apt-get.  i tried to install aptitude and i got this 

> Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  aptitude: Depends: libapt-pkg-libc6.3-5-3.9
E: Broken packages 

people told me aptitude is better then apt-get to resolve dependencies, but i can't even install it. another suggestion was that  i've perhaps used breezy sources in my sources.list. i didn't.

i don't know what happened, and i have no clue where to start problem-finding...  :mad: 

then i tried > sudo apt-get --reinstall install apt 

but also didn't work:

> Reading package lists... Done
Building dependency tree... Done
Reinstallation of apt is not possible, it cannot be downloaded. 

????? - my internet connection is working:::

and
> sudo apt-get -f install & sudo dpkg --configure -a  
also shows no further problems, broken dependencies etc.

i have no clue .. .. ..

vlad

---

### Post by Tamir on 2005-07-20
[QUOTE=DonVla]hello,

i got a similar problem. i explained it in this thread:

[http://ubuntuforums.org/showthread.php?t=49862](http://ubuntuforums.org/showthread.php?t=49862)

first i thought it was a kde problem. but now i think it's a global problem; perhaps a problem with apt-get.  i tried to install aptitude and i got this 

 

people told me aptitude is better then apt-get to resolve dependencies, but i can't even install it. another suggestion was that  i've perhaps used breezy sources in my sources.list. i didn't.

i don't know what happened, and i have no clue where to start problem-finding...  :mad: 

then i tried  

but also didn't work:

 

????? - my internet connection is working:::

and
 
also shows no further problems, broken dependencies etc.

i have no clue .. .. ..

vlad[/QUOTE]
 try apt-get -f install

---

### Post by DonVla on 2005-07-20
> and
Quote:
sudo apt-get -f install & sudo dpkg --configure -a

also shows no further problems, broken dependencies etc. 

i did ...

---

