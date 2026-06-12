---
title: "get rid of KDE?"
date: 2013-02-26
forum: Desktop Environments
---

### Post by geeve420 on 2013-02-26
I installed Kubuntu 12.04 and just couldn't get used to it and went on and downloaded and installed unity using: 

sudo apt-get install ubuntu-desktop. 

How can I get rid KDE? Do I even need to? That's all I really need to know...

Thanks

Geeve

---

### Post by oldos2er on 2013-02-26
[http://psychocats.net/ubuntu/pureubuntu](http://psychocats.net/ubuntu/pureubuntu)

---

### Post by geeve420 on 2013-02-26
Thanks oldos! When running that command should I skip 

&& sudo apt-get install ubuntu-desktop

at the end because I already have it?

Thanks again

Geeve

---

### Post by 3Miro on 2013-02-26
> **geeve420 said:**
> Thanks oldos! When running that command should I skip 

&& sudo apt-get install ubuntu-desktop

at the end because I already have it?

Thanks again

Geeve

If ubuntu-desktop is already installed, then the apt-get install command will simply exit without doing anything. I would run the command just to double-check.

---

### Post by geeve420 on 2013-02-27
Ran the code from the link and got this error:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package kubuntu-desktop is not installed, so not removed
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 default-jre : Depends: openjdk-6-jre (>= 6b23~pre11-1ubuntu1~) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
```

Did some searching, but can't find if anyone has actually solved this yet. 

ran into this: 

[http://ubuntuforums.org/showthread.php?t=2002928&page=2](http://ubuntuforums.org/showthread.php?t=2002928&page=2)


It says that Kubuntu desktop is not installed, that can't be though. When I reboot, it's the KDE login, I can also choose KDE to log in to and it works just fine....

Any ideas?

Thanks for all your help so far

---

### Post by oldos2er on 2013-02-27
kubuntu-desktop is just a [metapackage]("https://help.ubuntu.com/community/MetaPackages"); if APT says it's not installed, I'd believe it.

What does ```
ls /usr/share/xsessions/
``` say?

---

### Post by geeve420 on 2013-02-27
This is what I get back:

```
geeve@geeve-dell:~$ ls /usr/share/xsessions/
gnome-classic.desktop   gnome-shell.desktop  ubuntu.desktop
gnome.desktop           kde-plasma.desktop
gnome-fallback.desktop  ubuntu-2d.desktop
geeve@geeve-dell:~$ 

```

I ran the wall of text again and got a different error. I now am getting this now after a reboot:

```
[sudo] password for geeve: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package pinentry-gtk2 is not installed, so not removed
Package ktimetracker is not installed, so not removed
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libatk-wrapper-java : Depends: default-jre but it is not going to be installed or
                                java2-runtime
 libatk-wrapper-java-jni : Depends: default-jre but it is not going to be installed or
                                    java2-runtime
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
```


I can still log in to KDE, this is getting weird......

I just want want KDE gone LOL!

Thanks again

Geeve

---

### Post by oldos2er on 2013-02-27
The java errors don't have anything to do with KDE. Maybe if you try removing libatk-wrapper-java, assuming you don't need it, it would fix the error, but I'm not certain of that.

Try ```
sudo mv /usr/share/xsessions/kde-plasma.desktop /home/geeve/
``` which should remove the KDE option from lightdm, then reboot. If it works the way you want you can then delete the kde-plasma.desktop file.

---

### Post by geeve420 on 2013-02-27
I ran the command, rebooted and still have KDE splash and log in. I can also log in to KDE with no issue :( 

I don't know if the java wrapper is part of play on Linux for steam or not so I am I hesitant to remove it. I did make a Redo Backup last night before I started fiddling with this just in case though.

I copy and pasted the wall of command into LO writer and did a ctrl-f to look for that java wrapper. It is not part of what's is listed in that command so I don't know why it would stop the removal?! 

I may be way off base here, but is there a way to remove the held packages that it is freaking out about in the last line of the error? Maybe force it to ignore them? (I am still quite a newb, so I may just be talking out of my rear now) :)

I really appreciate your time on this! If we can't get it, I will live with having them both here and only use Ubuntu, I have just read that having them both could cause conflicts and instability. I am trying to not do a fresh install because the 5GB download of Skyrim on Steam takes literally days :(

Thanks again

Geeve

---

### Post by oldos2er on 2013-02-28
Are you using lightdm, or kdm?

---

### Post by geeve420 on 2013-02-28
Not sure, it would be whatever was installed with Kubuntu :( Sorry still real green at this....

I did however take a look at the dependecies that are attached to the java wrapper, turns out they are flash inastaller, software center, and unity greeter. I can not for the life of me get them to go through. 

I also found out that synaptic will not open unless I force it through the terminal using: ```
gksu-synaptic
```

Then when I had it open I tried to install something else and got an error saying that there is an apt-get process already running" and to run ```
sudo dpkg-configure -a
``` That then tells me to install aptitude to make it easier, well...... I can't because an apt-get is already running LOL...

Well in light of the obvious mess I have on my hands here I have decided that a fresh install of Ubuntu 12.04 is in order!!

I really appreciate you trying to help, but like I said, I think the best course of action unfortunately is to start over with the right stuff first...

Thanks Again

Geeve

---

### Post by oldos2er on 2013-02-28
Sorry you're having so many problems. Better luck next time, hopefully.

---

