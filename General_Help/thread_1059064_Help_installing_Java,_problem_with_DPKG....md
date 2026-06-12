---
title: "Help installing Java, problem with DPKG..."
date: 2009-02-03
forum: General Help
---

### Post by defensa24 on 2009-02-03
As the tittle says it...I need help! I tried installing java using the command "sudo apt-get install ubuntu-restricted-extras" but it says "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."
I dont know what to do...help me!

---

### Post by taurus on 2009-02-03
Just run that command from a terminal, adding a sudo in front.

```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by defensa24 on 2009-02-03
> **taurus said:**
> Just run that command from a terminal, adding a sudo in front.

```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

yupp, i did all of that and well...it seemed to have worked.
But I still go to youtube and says I need the latest Java...whats up with that?
And how do I go about downloading limewire? It freezes when installing java.

---

### Post by howefield on 2009-02-03
> **defensa24 said:**
> But I still go to youtube and says I need the latest Java...whats up with that?
And how do I go about downloading limewire? It freezes when installing java.

have you restarted your browser since installing restricted-extras ?

Limewire won't work in Ubuntu without the help of Wine, there is a linux equivalent, I think it is frostwire...  but really, I didn't think there was anyone left using those virus laden emporiums of kak.

---

### Post by defensa24 on 2009-02-03
> **howefield said:**
> have you restarted your browser since installing restricted-extras ?

Limewire won't work in Ubuntu without the help of Wine, there is a linux equivalent, I think it is frostwire...  but really, I didn't think there was anyone left using those virus laden emporiums of kak.

yess, I've restarted my browser, even my whole computer. And still nothing.
Any other advice?

---

### Post by taurus on 2009-02-03
What's the output of this command from a terminal?

```
java -version
```
When you installed ubuntu-restricted-extras package from a terminal, did you see the java license screen, asking you if you want to accept it with the <OK> At the bottom?

---

### Post by johnruben on 2009-02-03
Hi Taurus
I've been following this thread as I'm having similar issues, could you help?
When I run java-version in the terminal I get:john@john-desktop:~$ java -version
java version "1.6.0_0"
IcedTea6 1.3.1 (6b12-0ubuntu6.1) Runtime Environment (build 1.6.0_0-b12)
OpenJDK 64-Bit Server VM (build 1.6.0_0-b12, mixed mode)

What now?

Thanks, John

---

### Post by taurus on 2009-02-03
> **johnruben said:**
> Hi Taurus
I've been following this thread as I'm having similar issues, could you help?
When I run java-version in the terminal I get:john@john-desktop:~$ java -version
java version "1.6.0_0"
IcedTea6 1.3.1 (6b12-0ubuntu6.1) Runtime Environment (build 1.6.0_0-b12)
OpenJDK 64-Bit Server VM (build 1.6.0_0-b12, mixed mode)

What now?

Thanks, John

Have you installed the Sun's version?

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```
Again, when you get to the license screen, hit the Tab key to highlight the <OK> and Return key to accept it.  Once it's done, check to see if it is the default version, not the OpenJDK.

```
java -version
```

---

### Post by johnruben on 2009-02-03
I downloades this package, but I'm not sure how to unfold it?
jre-6u11-linux-i586.bin

---

### Post by taurus on 2009-02-03
> **johnruben said:**
> I downloades this package, but I'm not sure how to unfold it?
jre-6u11-linux-i586.bin

Are you sure you don't want to install the one from the repos since it does everything for you?  

But if you want to install the one that you've downloaded, then you have to move it to /opt and unpack it from there.  Then, you need to link it so the system would use the one that you just unpacked.  You also need to link the plugin to /usr/lib/mozilla/plugins so firefox would know about it.

---

### Post by johnruben on 2009-02-03
You're right the repos would be better.
I got this below?

john@john-desktop:~$ sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
[sudo] password for john: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-bin is already the newest version.
sun-java6-bin set to manually installed.
sun-java6-jre is already the newest version.
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate

---

### Post by johnruben on 2009-02-03
I got the result below, is this right to get it from the repo?

john@john-desktop:~$ sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
[sudo] password for john: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-bin is already the newest version.
sun-java6-bin set to manually installed.
sun-java6-jre is already the newest version.
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate

---

### Post by taurus on 2009-02-03
> **johnruben said:**
> I got the result below, is this right to get it from the repo?

john@john-desktop:~$ sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
[sudo] password for john: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-bin is already the newest version.
sun-java6-bin set to manually installed.
sun-java6-jre is already the newest version.
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate

Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

p.s.  You are not running feisty, are you?

---

### Post by johnruben on 2009-02-03
john@john-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# deb cdrom:[Ubuntu-Studio 8.04 _Hardy Heron_ - Beta amd64 (20080319.1)]/ hardy main multiverse restricted universe
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse

# deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy main universe
# deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy-updates main universe
# deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy-proposed main universe
# deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy-security main universe
john@john-desktop:~$

---

### Post by johnruben on 2009-02-03
> **taurus said:**
> can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

p.s.  You are not running feisty, are you?

8.10

---

### Post by taurus on 2009-02-03
What if you install the ubuntu-restricted-extras package?

```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by johnruben on 2009-02-03
What if you install the ubuntu-restricted-extras package?

I did that just before I ran the "sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin" deal? Strange?

Incidently, is there a way I can make this forum notify me as soon as you reply to this post?

---

### Post by taurus on 2009-02-03
> **johnruben said:**
> What if you install the ubuntu-restricted-extras package?

I did that just before I ran the "sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin" deal? Strange?

So you still don't have sun-java6-plugin?  Open System -> Administration -> Synaptic Package Manager -> Search and type in **sun-java6-jre** and post the screenshot of that window (display).

> Incidently, is there a way I can make this forum notify me as soon as you reply to this post?

Don't think so but I haven't looked too hard for it.  ;)

---

### Post by johnruben on 2009-02-03
It is there and seems to be installed but when I goto java.com and hit the check if I have java it syas:Sorry! We couldn't find the document requested.

The file that you requested could not be found on this server. If you provided the URL, please check to ensure that it is correct.

---

### Post by gjoellee on 2009-02-03
you should get frostwire instead of limewire. 
Downlaod a DEB here: [http://www.frostwire.com/](http://www.frostwire.com/)

sometimes frostwire works and limewire don't....(pretty wierd)

then form terminal run ```
frostwire
```

if you get eny error post the output.

---

### Post by taurus on 2009-02-03
> **johnruben said:**
> It is there and seems to be installed but when I goto java.com and hit the check if I have java it syas:Sorry! We couldn't find the document requested.

The file that you requested could not be found on this server. If you provided the URL, please check to ensure that it is correct.

Wait.  You are running the x86_64 version!

---

### Post by johnruben on 2009-02-03
T, thanks for your help so far, I'll give it another bash tomorrow

J

---

### Post by johnruben on 2009-02-03
> **taurus said:**
> Wait.  You are running the x86_64 version!

Is this the problem then do you think?

---

### Post by taurus on 2009-02-03
> **johnruben said:**
> Is this the problem then do you think?

You have to download the x86_64 version, not the one you already have, jre-6u11-linux-i586.bin.

[http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp)

---

### Post by defensa24 on 2009-02-03
hello once again...
my problem was solved by going to youtube and actually downloading the java file and opening it not saving.
now youtube works fine.

---

### Post by Awesom on 2009-02-10
> **taurus said:**
> Just run that command from a terminal, adding a sudo in front.

```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

HI I just stumbled upon this while trying to fix java aswell and I did that and it says... 
```

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
troy@TroY:~$ sudo apt-get update
Hit http://archive.ubuntu.com hardy Release.gpg
Ign http://archive.ubuntu.com hardy/main Translation-en_AU
Hit http://archive.ubuntu.com gutsy Release.gpg
Ign http://archive.ubuntu.com gutsy/universe Translation-en_AU
Hit http://archive.ubuntu.com hardy Release
Hit http://archive.ubuntu.com gutsy Release   
Hit http://archive.ubuntu.com hardy/main Packages
Hit http://archive.ubuntu.com gutsy/universe Packages
Reading package lists... Done
troy@TroY:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu-restricted-extras

```
:S All help greatly appreciated.

---

### Post by Rivindu Prasanga Perera on 2009-02-10
Java Jdk 1.6 can be installed in any ubuntu flatform without 
any trouble. Please specify the version....................:guitar:

---

### Post by Awesom on 2009-02-10
I've downloaded java 6u11 from the site and came here trying to find out how to install it but everything is totally different (I want to run frostwire and it says I need 1.5.x) and I've just come from windows but am getting the hang of this just have no idea how to install java properly.

---

