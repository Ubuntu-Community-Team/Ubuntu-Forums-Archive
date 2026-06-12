---
title: "VMware Installation on Ubuntu"
date: 2009-01-10
forum: Desktop Environments
---

### Post by vinu.upadhya on 2009-01-10
Can anyone tell me how to install VMware software on Ubuntu? I already have this software for windows XP, Can I use the same to install it on Ubuntu?...........

---

### Post by Hooya on 2009-01-10
It's not exactly the same, but you probably should try

$sudo aptitude install virtualbox

Virtualbox is pretty much the same thing from what I hear.

---

### Post by Speed Demon on 2009-01-10
> **Hooya said:**
> It's not exactly the same, but you probably should try

$sudo aptitude install virtualbox

Virtualbox is pretty much the same thing from what I hear.
I second this... Virtual Box is great :popcorn:

---

### Post by Hooya on 2009-01-11
Just to add to this, today I actually finally got rid of my Vista partition completely.  I only needed Windows for about 4 programs, all of which are relatively low resourse use.  I rarely need them, so rebooting to use them is a pain.

So I did an nLite install of XP into a VirtualBox.  Wow.  Easy as pie.  Works great, seamless integration.  Typical performance hit of a virtual machine, but super easy to deal with.

---

### Post by mtbsoft on 2009-01-11
If you require VMWare specifically (say, to use images accessed from Windows as well), you cannot use the Windows installer but will need to download the Linux equivalent from the VMWare site.  You didn't indicate which product you need - Player and Server are both free but if you use Workstation you will require to purchase another license for the Linux version.

I use both Workstation and Player across both platforms and you can happily use your existing Windows images with the Linux software - any other questions, just ask.

---

### Post by adamlau on 2009-01-11
You are likely referring to VMware Wokstation for Linux. I prefer VMware to VirtualBox OSE (the crippled version available in the repositories) for virtualization on Ubuntu. Ensure that /tmp is not mounted with noexec, the installation should run w/o issue once downloaded and executed. Through not as seamless as VirtualBox on OpenSolaris, VMware on Ubuntu works mostly as advertised.

---

