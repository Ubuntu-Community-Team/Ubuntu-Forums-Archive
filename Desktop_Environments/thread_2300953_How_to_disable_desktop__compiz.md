---
title: "How to disable desktop / compiz"
date: 2015-10-29
forum: Desktop Environments
---

### Post by ratin3 on 2015-10-29
Hello, I am setting up a ubuntu 15.04 installed settop box (Intel based) that doesnt require to run desktop/unity etc but it needs X (lightdm etc) for video windows. I used compiz config to disable all desktop related windows etc. However compiz sometimes get on the way and disbling everything including compiz is becoming a nightmare, a few times the whole system was unusable and I had to re-install everything. My question is how can I use lightDM launching X during init but disable compiz automatically when the system boots, including disabling all desktop windows, notification widgets, events etc? Like i said currently I used Compiz settings manager to disable all the stuff but that seems to be a hack, and as soon as I disable compiz with "metacity --replace", the system does something very wacky, like a background mazimized 400%, etc etc. Any effort of uninstalling unity, ubuntu-desktop etc had similar consequences. 

Basically my goal is :

launch X via lightdm (and utilize other logics like if there is no display, fall back to failsafe mode etc)
Do not launch anything on the desktop other than the theme (a background image), do not use compiz
use /etc/xdg/autostart to launch an X app and run it continuously


Thanks for any input.

Cheers 
Ratin

---

### Post by grahammechanical on 2015-10-29
I might be wrong about this but I think that the Linux kernel launches the X server and LightDM (display manager) runs on the X windowing system. Have you installed Metacity? I do not think that it is installed by default in Ubuntu 15.04. So, I guess that metacity --replace would indeed produce something wacky if metacity was not installed.

You might get what you want by installing from the minimum ISO image. You can start off with Linux and work your way up to what you want. You then get to choose what components get installed. You might prefer a desktop environment that does not use Compiz. This might be a better way of doing things than starting with a working OS and un-installing bits and pieces and then wondering why the OS is broken.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Ubuntu uses LightDM to display the greeter (login screen) and then after login is completed a window manager/compositor is used (Compiz) to run the User Interface (Unity). Some of the other family members use LightDM for the same purpose but then use a different DE and UI. I have no idea if LightDM is capable of being a window manager.

Regards.

---

### Post by ratin3 on 2015-11-04
Hi grahammechanical, Thanks for your reply. Yes I installed metacity manually. You brought up an interesting point, building up the system from a minimal distro would probably be more tuned with what I want on the system. However based on my experiences with customizing minimal ubuntu and distribute, it takes a lot of time to go thru the dependencies and setting up the repository with validation (needed to update the udeb password package with custom gpg key if I remember correctly) and since I pretty much need everything ubuntu offers minus the desktop effects and the desktop, I thought it was a quicker option for me. But i get what you are saying.

---

### Post by buzzingrobot on 2015-11-04
Unity requires Compiz -- it's implemented as a Compiz plugin -- so trying to de-Compiz Unity doesn't seem worth the effort. Even starting with a minimal image, you'll soon be installing packages with dependencies on Unity and Compiz.

Using one of the slimmer  non-Unity flavors -- LXLE or XFCE -- might be an alternative.  Different interfaces, same access to the Ubuntu repos, no Unity and no Compiz. (There are also core/minimal metapackages for LXLE and XFCE that install very little beyond what's need to get the GUI up and running. Those can be added to a minimal install.)

A good many Ubuntu packages are built against a couple of Unity libraries so it is almost impossible to prevent those libraries from being pulled in as dependencies.  In my experience, the dependency chain stops there:  You won't get Unity/Compiz deposited on the drive.

---

