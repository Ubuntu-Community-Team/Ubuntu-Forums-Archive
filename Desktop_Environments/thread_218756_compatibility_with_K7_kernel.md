---
title: "compatibility with K7 kernel?"
date: 2006-07-19
forum: Desktop Environments
---

### Post by Jhongy on 2006-07-19
Hello,

I am a complete Linux newbie.

As I am running an AthlonXP (not 64-bit), I updated the kernel to the K7 version. 

I've had no problems I can attribute to this, but I have a few newbie questions that maybe someone can help with:

- For many packages (e.g. W32codecs), I can only see .i386 .deb packages and amd64 packages. Can I assume therefore that - unless otherwise stated - the i386 packages are compatible with the k7 kernel?

- The synaptic (?) updater that automatically runs when I log in keeps suggesting that I upgrade the i386 kernel... which I'm not using. Is this normal? I upgraded the kernel before I installed all the updates suggested initially, so is this just a throw-back from first boot?

I have a whole bunch of other Newbie questions that I was wondering if someone could kindly point me in the right direction on:

Are there any resources available that explain "how" Linux keeps track of installed programs and packages? Is it done individually by the package managers, or is there a central system? I understand that Linux doesn't have a central "registry" like Windows, so was wondering how stock was kept... For example, I can run programs from the command line by simply typing there name... how does the command line know where the package is installed? Is there a PATH variable somewhere? Or some sort of SymLink?

---

### Post by Arisna on 2006-07-19
I've been running a k7 image for several weeks and have had no problems with it.  The "i386" in those packages refers to the general class of processor, not the subarchitecture, so i386 packages like w32codecs should work fine.

If you are satisfied with the linux-k7 kernel, it is safe to remove the linux-386 metapackage to prevent further upgrades.  If you wish, you can also uninstall the previous versions of linux-386 that have accumulated.  Use Synaptic for everything in this paragraph.

The way I understand it, Ubuntu keeps track of installed and available software through apt/dpkg.  Synaptic (GUI) and Aptitude (CLI) are interfaces to this system.

---

### Post by jgcamp99 on 2006-07-19
I've noticed that myself, and what you indicate makes sense for it to be backwards compatible or rather "not K7 optimized". To be honest with you, the first week I ran Ubuntu, I never went after the K7 optimized kernel, I didn't notice any difference in performance for what I did. When I finally figured it out, I downloaded and optimized for K7. To this day I simply get all the updates regardless of K7 or i386 and apply them. It's really no extra effort to update it. I could understand if I were trying to download them with 56K dialup, but broadband makes light work of it.

---

