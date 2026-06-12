---
title: "trying to install gnome classic on ubuntu 12.10"
date: 2015-03-30
forum: Desktop Environments
---

### Post by rafael18 on 2015-03-30
Hi. My problem is I can not install gnome classic. I am using a version 12.10 of ubuntu. I can not upgrade to new version because the sound does not work in my laptop with new ubuntu  ( I have tried followind with SoundTroubleshooting but it did not work) so I had to go back to Ubuntu 12.10 using the 
repositories  old-releases.ubuntu.com/ubuntu/ quantal. I can update and upgrade with apt. I can install other programs, but when I want to install gnome classic desktop (I do not like Unity) the system gives me this result:

```
bitacovir@bitacovir-Satellite-Pro-A120:~$ sudo apt-get install gnome-session-fallback
[sudo] password for bitacovir: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnome-session-fallback : Depends: gnome-session-common (= 3.6.0-0ubuntu1) but 3.6.0-0ubuntu1.1 is to be installed
                          Recommends: cups-pk-helper but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

I am not very good with linux so I do not know hot to proceed.

---

### Post by v3.xx on 2015-03-30
Hi rafael18

Getting support on something no longer supported is rough.

12.04 is supported till April 2017, why not use it?

A sound problem is normally not a show stopper.  Do you know what package is breaking the sound?

If you like the old desktop look, I would also suggest taking a look at Mate 14.04.  It has ties to the old gnome and just may work for you.
[http://ubuntuportal.com/2014/11/ubuntu-mate-14-04-lts.html](http://ubuntuportal.com/2014/11/ubuntu-mate-14-04-lts.html)

---

### Post by gakon77 on 2015-03-30
Hello rafael18, 

can I suggest to install different distro more suitable for an old PC? I run [LXLE 12.04.5]("http://lxle.net/") in my old Toshiba Satellite and works like a charm. 

It's based in LTS Ubuntu with a few tweaks like a kernel for non-PAE bios and a lighter desktop, it is not gnome but it's worth a try. However, if the LXLE desktop environment doesn't suit you, probably you may be able to install another desktop environment of your choice from the repository on top of the basic installation.

Cheers!

---

### Post by rafael18 on 2015-04-01
Thanks for your suggestions. I did not know that 12.04 is still supported. So I installed this version and everything is more simple and working. The main problem is not the desktop, it is the version of ubuntu. After 12.10 the software (module) does not detect the sound card, any more. I tried to fix it following the instructions in ubuntu forums but the module never works in this version. It has been a waste of time moving to new version of ubuntu, trying to resolve sound problem, moving back to ubuntu 12.10 and now installing ubuntu 12.04. 
Thanks a lot. :)

---

### Post by Bucky Ball on 2015-04-01
12.10 is not a new version, it is an unsupported old version. LTS = long term support release. 12.04 LTS and 14.04 LTS are currently supported (2017 and 2019 respectively) and 14.10 is supported for about another five months. 

If you have low specs, and as suggested, try a lighter version of 14.04 LTS, Lubuntu or Xubuntu perhaps. Also, you say 'sound doesn't work' which gives us little info to go on. I'd say install a supported release and then, if sound is still not working, post a new thread outlining what you have tried and how the sound is not working. Hopefully we can help more with more info.

---

### Post by v3.xx on 2015-04-01
Ok, that will buy you some time.  Know about this?

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=toshiba+satellite+sound&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=toshiba+satellite+sound&sa=Search&cof=FORID:9)

don't forget

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

