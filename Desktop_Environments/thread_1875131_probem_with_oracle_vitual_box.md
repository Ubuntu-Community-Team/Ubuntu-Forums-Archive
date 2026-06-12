---
title: "probem with oracle vitual box"
date: 2011-11-04
forum: Desktop Environments
---

### Post by forsubhi on 2011-11-04
I installed oracle vitual box  from software center then i got this message 

{
Failed to open a session for the virtual machine windows xp.

Failed to load VMMR0.r0 (VERR_SUPLIB_OWNER_NOT_ROOT).

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: Console
Interface: IConsole {1968b7d3-e3bf-4ceb-99e0-cb7c913317bb}
}

can somesone help me please ....

---

### Post by typhoon_tip on 2011-11-04
What version of Ubuntu and how many bits ? And what are you trying to do ? Create a new VM or opening an existing one ?

Anyway, it is a bad idea to use VB from rep, it's very dated.

Use this way:
[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

Before starting anything, uninstall completely the current Virtual Box in your system (including configuration files, this will not delete existing hard drives anyway). Best way to do this is by using Synaptic. Open Synaptic, search Virtual Box, tick and choose "Completely uninstall including config files".

**Reboot the system after uninstall** (Kernel module is still loaded !).

Let's then add the source:
```
wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
```

Let's update the list:
```
sudo apt-get update
```

After update is done, let's install VB:
```
sudo apt-get install virtualbox-4.1
```

At start, it will ask you to download and install extensions to use USB and so on. In case it doesn't download, this is the extension plugin (universal):
[http://download.virtualbox.org/virtualbox/4.1.4/Oracle_VM_VirtualBox_Extension_Pack-4.1.4-74291.vbox-extpack](http://download.virtualbox.org/virtualbox/4.1.4/Oracle_VM_VirtualBox_Extension_Pack-4.1.4-74291.vbox-extpack)

If you have troubles with USB (passing devices to your VM), then do the following:
- Open "Users and Groups" settings
- Click on "Manage Groups" and enter your password
- Make sure that your user account belong to the group "vboxusers" (ticked)

Happy VBoxing :P:P

---

### Post by forsubhi on 2011-11-04
I do what you say but when I executed 
sudo apt-get update
I had 

W: Failed to fetch [http://download.virtualbox.org/virtualbox/debian/dists/oneiric/Release](http://download.virtualbox.org/virtualbox/debian/dists/oneiric/Release)  Unable to find expected entry 'contrib/source/Sources' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.

I skiped this step but I still have the same error

---

### Post by haqking on 2011-11-04
download the deb from oracle along with extensions pack.

[http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html](http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html)

---

### Post by CharlesA on 2011-11-04
> **forsubhi said:**
> I installed oracle vitual box  from software center then i got this message 

{
Failed to open a session for the virtual machine windows xp.

Failed to load VMMR0.r0 (VERR_SUPLIB_OWNER_NOT_ROOT).

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: Console
Interface: IConsole {1968b7d3-e3bf-4ceb-99e0-cb7c913317bb}
}

can somesone help me please ....

That points to a permission problem. Did you change permissions recently?

See here: [https://forums.virtualbox.org/viewtopic.php?f=7&t=39179](https://forums.virtualbox.org/viewtopic.php?f=7&t=39179)

---

### Post by forsubhi on 2011-11-04
thank for all 
typhoon_tip
haqking

CharlesA (this solve my problem)

i changed the owner of /usr and /usr/lib from subhi to root 


thank you very very much I spent two day searching about the problem 
thanks
:D:D:D:D

---

### Post by typhoon_tip on 2011-11-05
> **forsubhi said:**
> I do what you say but when I executed 
sudo apt-get update
I had 

W: Failed to fetch [http://download.virtualbox.org/virtualbox/debian/dists/oneiric/Release](http://download.virtualbox.org/virtualbox/debian/dists/oneiric/Release)  Unable to find expected entry 'contrib/source/Sources' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.

I skiped this step but I still have the same error

Oh yes, you need to untick the "sources" source in software sources... (seems a joke...)

Seems that folder is not available since 11.04 came along, and it only download the debians.

haqking: yes you can download the debian manually, but without the ppa, you don't have the update when it comes. I prefer to use the ppa ;)

---

### Post by haqking on 2011-11-05
> **typhoon_tip said:**
> Oh yes, you need to untick the "sources" source in software sources... (seems a joke...)

Seems that folder is not available since 11.04 came along, and it only download the debians.

haqking: yes you can download the debian manually, but without the ppa, you don't have the update when it comes. I prefer to use the ppa ;)

yeah i know, i dont like the PPA for VBox, only my personal experience.

I always use the .deb.  But yes it is often preferrable to use the PPA

---

### Post by CharlesA on 2011-11-05
> **haqking said:**
> yeah i know, i dont like the PPA for VBox, only my personal experience.

I always use the .deb.  But yes it is often preferrable to use the PPA
I use the repo cuz I am lazy. :p

The deb works fine too.

---

### Post by typhoon_tip on 2011-11-05
> **CharlesA said:**
> I use the repo cuz **I am lazy**. :p

The deb works fine too.

Most of the time me too. To remain on topic, just upgraded VBox with update manager :P

---

### Post by CharlesA on 2011-11-05
> **typhoon_tip said:**
> Most of the time me too. To remain on topic, just upgraded VBox with update manager :P
To which version? I checked apt-get yesterday but I didn't have an update yet. :p

EDIT: Nevermind,looks like it was released yesterday. Updating now.

---

