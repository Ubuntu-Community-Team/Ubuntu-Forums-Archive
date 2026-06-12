---
title: "Steam You are missing the following 32-bit libraries: libc.so.6"
date: 2016-03-14
forum: Gaming &amp; Leisure
---

### Post by names_are_useless on 2016-03-14
Steam (Linux version) has been working fine for me since I installed it months ago. Unfortunately, I opened it this morning and the automatic update started. Before it finished, my laptop froze up ... nothing unfroze it. I decided to do a hard restart, and once it did and I tried opening Steam again, I have received a popup message:

```
Error: You are missing the following 32-bit libraries, and Steam may not run:
libc.so.6
```

I have tried removing it from the Software Manager and installing it again: same error

I have tried purging and reinstalling steam from terminal:
```
sudo apt-get purge steam
sudo apt-get install steam
```
and still same error.

I have tried reinstalling libc files: ```
sudo apt-get install '^libc6.*'
``` and I get a whole bunch of packages of ```
... is already the newest version.
``` and it ends with ```
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
```

I've tried installing the latest i386 for libc6: ```
sudo apt-get install libc6-i386
``` but I'm told its already the newest version.

I have already tried the steps in this thread: [http://ubuntuforums.org/showthread.php?t=2242632&highlight=libc.so.6](http://ubuntuforums.org/showthread.php?t=2242632&highlight=libc.so.6)

As well as the steps in this stickied thread: [http://ubuntuforums.org/showthread.php?t=2233005](http://ubuntuforums.org/showthread.php?t=2233005)

None of these have solved the problem. Anyone have a solution?

---

### Post by MikeCyber on 2016-03-15
There are two steam packages. One from synaptic and the other download from steam. I would remove all, including in your home the hidden steam folder. 
cd ~
rm -rf .steam
Than try the other one.

---

### Post by names_are_useless on 2016-03-18
> **MikeCyber said:**
> There are two steam packages. One from  synaptic and the other download from steam. I would remove all,  including in your home the hidden steam folder. 
cd ~
rm -rf .steam
Than try the other one.
So I followed that command, and removed 'steam:i386" and "steam-launcher" in Synaptic. Then I did a "sudo apt-get install steam" to reinstall it.

Yes! Steam came up and is working again! Thank you so much! :D

---

### Post by bobby26 on 2016-03-26
Sorry, but I have only had ubuntu for a week and I was wondering if you could explain what you typed into the terminal in more specific terms because i dont understand what to put. Thanks in advance

---

### Post by MikeCyber on 2016-03-27
Easiest you can install via synaptic.
To clean a failed previous attempt, remove also the hidden directory .steam in your home. Only use root when needed.

---

### Post by bobby26 on 2016-03-27
> **MikeCyber said:**
> Easiest you can install via synaptic.
To clean a failed previous attempt, remove also the hidden directory .steam in your home. Only use root when needed.

ok, i tried to install via synaptic and it was not there. I also tried to install it through the terminal but it says that "Package steam-launcher is not available", any thoughts?

---

### Post by oscarivera9 on 2016-04-17
> **bobby26 said:**
> ok, i tried to install via synaptic and it was not there. I also tried to install it through the terminal but it says that "Package steam-launcher is not available", any thoughts?
What version of Ubuntu are you running?  Ubuntu 14.04, Ubuntu 15.10, Ubuntu 16.04, etc.
Some versions may not support Steam out of the box and you may need to add the ppa.

---

### Post by MikeCyber on 2016-04-20
Download from steam. ppa are often outdated.

---

### Post by oscarivera9 on 2016-04-24
> **MikeCyber said:**
> Download from steam. ppa are often outdated.
You are 100% correct about download from Steam instead of ppa.

However, the reason I made that suggestion is that a couple of months after 15.10 had been released, it was impossible for me to install through either Steam or Ubuntu Software Center without running into problems.  The installation would finish seemingly normal but then Steam wouldn't run at all so I had to uninstall and then re-install using a ppa, then tweak a few items (such as unneeded broken dependencies) in order for Steam to work.  So after running into problem after problem, I decided to keep using 14.04.

I'm currently running 14.04 which works perfectly but before I upgrade to 16.04 I'd like to get some positive feedback about Steam installing and working well in 16.04 without any extra effort needed.

---

### Post by samue2 on 2016-04-28
I have downgraded to 14.04 simply to avoid the teething issues with 16.04- also, i love the purge command. It makes me feel like im ending society

---

