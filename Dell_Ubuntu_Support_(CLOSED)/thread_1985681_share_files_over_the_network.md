---
title: "share files over the network"
date: 2012-05-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by disabled_biscarri on 2012-05-23
after the installation of CAELinux2011 on a dell workstation, I don't manage to connect other computer file systems to share information over the network

at System/Preferences/Personal File Sharing, the option "Share Files over the network" gives the message "This feature cannot be enabled because the required packages are not installed on your system"

does enyone know what to do? which packages should I download ans install? and where to find them?

thank you in advance

Lluis

---

### Post by roelforg on 2012-05-23
Is caelinux ubuntu based?
If not, this should be moved to "Other OS/distro talk"

Does it say what packages it's missing or is there some sort of "more information" button that'll tell you which ones are missing?

---

### Post by disabled_biscarri on 2012-05-23
hi roelforg,

caelinux is a distribution of several CAE open-source applications (finite element analysis and this kind of stuff) and includes ubuntu as OS

first you download caelinux imagefile and burn a DVD, then you boot your machine from that DVD and it starts with the ubuntu included in it

you can run the CAE apps in that way or, for better performance, you make the permanent installation in your hard drive; then you run your computer with the new ubuntu installation

after doing that, I'm working normally with everything except in sharing files over ny network

thanky for your advice

Lluís

(I don't understand what you mean by "PM you")

---

### Post by roelforg on 2012-05-23
> **biscarri said:**
> hi roelforg,

caelinux is a distribution of several CAE open-source applications (finite element analysis and this kind of stuff) and includes ubuntu as OS

first you download caelinux imagefile and burn a DVD, then you boot your machine from that DVD and it starts with the ubuntu included in it

you can run the CAE apps in that way or, for better performance, you make the permanent installation in your hard drive; then you run your computer with the new ubuntu installation

after doing that, I'm working normally with everything except in sharing files over ny network

thanky for your advice

Lluís

(I don't understand what you mean by "PM you")

Some threads go unnoticed by everyone, i'm always prepared to try to help the ones that nobody else helps.

Tried figuring out what it says is missing (like i asked you to do because there's always a message saying what's missing somewhere but i don't know your de so i can't give exact instructions until we have those package-names)?

---

### Post by disabled_biscarri on 2012-05-23
> **roelforg said:**
> Some threads go unnoticed by everyone, i'm always prepared to try to help the ones that nobody else helps.

Tried figuring out what it says is missing (like i asked you to do because there's always a message saying what's missing somewhere but i don't know your de so i can't give exact instructions until we have those package-names)?

I've understood that what is missing in the system is something like "gnome-user-share" package

is that saying something to you?

:)

---

### Post by jmore9 on 2012-05-23
This looks to be a self supporting distro to me :

question: What is CAELinux ?

Answer: CAELinux is a Linux distribution intended to provide a fully functionnal & preconfigured CAE workstation based on Open Source CAD/FEA/CFD softwares. It exists now in two versions: a liveDVD version that can also be installed on hard disk and a Virtual Machine version (VMWare) that is intended to be used from a guest operating system (for example: Windows). CAELinux and most of the included packages are distributed under GPL licence and thus are free to use, even for commercial applications. 

I would be looking on the forum or faq for this distro - no telling what dependies are needed.

---

### Post by pablo180 on 2012-05-25
What version of Ubuntu are you using? I remember a similar message years ago when setting up file sharing, it meant that I had to install Samba and/or NFS - you should be able to do this via Synaptic.

---

### Post by disabled_biscarri on 2012-11-25
sorry Pablo180 for this late answer

I'm using Ubuntu release 10.04 (lucid)
Kernel Linux 2.6.32-43-generic
GNOME 2.30.2

I have this computer conected through ethernet network with a mac (OS X version 10.8.2)
from the mac I see the files in the Ubuntu machine and can copy them to the mac
but In the Ubuntu computer I see the files in the mac but I can't copy them backd
error message: function not implemented
so I guess something is missing in the ubuntu installation...

thank you very much for your cooperation
best regards
Lluis

---

