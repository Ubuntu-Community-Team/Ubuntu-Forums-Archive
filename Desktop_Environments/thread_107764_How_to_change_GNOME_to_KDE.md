---
title: "How to change GNOME to KDE"
date: 2005-12-23
forum: Desktop Environments
---

### Post by MagiSu on 2005-12-23
Well,hello to everyone.
It seems I should first find documents from the web before I ask, but you see, I'm Chinese and cannot read English very well.
I am a newbie to Linux,especially to Ubuntu. I tried some Chinese-Based Linux such as RedFlag(a Linux from CAS), but it is too difficult to working between RPM packages. So I changed to debian-based Ubuntu. Now the problem is I had got used to KDE, but my ubuntu is gnome-preinstalled. I want to change it to KDE. Then, How to Do that?

Thanks a lot.

---

### Post by Freddy on 2005-12-23
Either download the Kubuntu .iso from [www.kubuntu.org/](www.kubuntu.org/) or you can allways get it through apt-get. 
```
sudo apt-get update
sudo apt-get install kubuntu-desktop
```
/// Freddan

---

### Post by MagiSu on 2005-12-23
thank you a lot!!!!!

---

### Post by ubuntu27 on 2005-12-23
Hey MagiSu :)
I wanted to tell you that your english isn't bad at all. ;) 
in fact, it's almost perfect :D

---

### Post by Freddy on 2005-12-23
No problemos, my friend.   /// Freddan

---

### Post by rubengs on 2005-12-24
In addition you can chose kdm over gdm as session manager, this gives more functionality to kde, if you didn't do it when you ran the "**sudo apt-get install kubuntu-desktop**" command you can change the session manager to kdm with: 
[B]
sudo dpkg-reconfigure kdm [/B]

---

### Post by stevenvh on 2005-12-26
Hi,
I'm absolutely new to Linux and Ubuntu, so please bear with me.

I'm trying to install KDE, following the instructions I found on madpenguin.org [http://www.madpenguin.org/cms/?m=show&id=5668]("http://www.madpenguin.org/cms/?m=show&id=5668").
So, and after I found about sudo... :rolleyes: :

> 
steven@ubuntu:~$ gedit /etc/apt/sources.list
steven@ubuntu:~$ sudo apt-get update
Password:
Get:1 [http://kubuntu.org](http://kubuntu.org) breezy Release.gpg [189B]
Hit [http://kubuntu.org](http://kubuntu.org) breezy Release
Hit [http://kubuntu.org](http://kubuntu.org) breezy/main Packages
Fetched 1B in 0s (2B/s)
Reading package lists... Done
steven@ubuntu:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
steven@ubuntu:~$


Thing is that restarting Xserver doesn't make things look different. What's this "Fetched 1B" in the above log anyway? And shouldn't the lines I added to sources.list 

> 
# Ubuntu 5.10 KDE 3.5 Repository
deb [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main


have been commented out afterwards?
What am I doing wrong here?
TIA for any help!

---

### Post by Lord Illidan on 2005-12-27
The dist-upgrade won't work if you haven't had KDE installed.. i.e., how can you upgrade KDE if it hasn't been installed?

Now, all you have to do is type

```
sudo apt-get install kubuntu-desktop
```

As for the commenting out, well no, it will not be commented automatically, to the best of my knowledge...who told you that?

---

### Post by angrykeyboarder on 2005-12-29
[quote=rubengs]In addition you can chose kdm over gdm as session manager, this gives more functionality to kde, if you didn't do it when you ran the "**sudo apt-get install kubuntu-desktop**" command you can change the session manager to kdm with: 
[B]
sudo dpkg-reconfigure kdm [/B][/quote] 
And then KDM starts beautifuly, it just **[won't let you log in]("http://lists.ubuntu.com/archives/kubuntu-users/2005-December/003034.html")**....

---

### Post by veloct on 2005-12-30
how about uninstalling gdm completely and then try again

```
 sudo dpkg-reconfigure kdm
```

Worth a shot?

---

### Post by angrykeyboarder on 2006-01-01
[quote=veloct]how about uninstalling gdm completely and then try again

```
 sudo dpkg-reconfigure kdm
``` 
Worth a shot?[/quote]

I've tried that as well and KDM still won't let me log in.

---

### Post by jetpeach on 2006-01-16
One note to those considering this from my experience: I think, when possible, it is better to use a full install from the Kubuntu CD if you really plan on using KDE more than Gnome.  The reasons, I've found, are various configuration issues.  For example, in Firefox, flash sound works in Gnome but not in KDE for me.  It's got to do with defaults sound/ALSA configuration stuff which are different kde/gnome, and (if you search threads around) can involve quite a lot of configuration to fix.  Another example is my ipod mounting, which works great in Gnome but it appears the configuration is not set up properly for KDE, I believe because competing mounting programs are installed from gnome/kde.  And there are other such examples - Basically I wish it was as simple as, "just choose your window environment" but from my experience, when you choose Ubuntu or Kubuntu a lot of other settings are configured and some programs will work better in one envirnoment than the other.
Just my 2 cents, though others my disagree and had better experiences switching between the two...
jet

---

