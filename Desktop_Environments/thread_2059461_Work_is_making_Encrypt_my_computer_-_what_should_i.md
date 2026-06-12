---
title: "Work is making Encrypt my computer - what should i use?"
date: 2012-09-18
forum: Desktop Environments
---

### Post by beenny on 2012-09-18
Hello All,

My work is making everyone encrypt their computers. I've generally flown under the radar since I have Ubuntu on machine but I'm sure the reckoning is coming. They will be using BitLocker for Windows folks and FileVault2 for Mac folks. I have no illusion they have any idea what to do with me (and really hope they don't make switch over to one of those), but was wondering if there were a good comparable that I could sell them on? I would like to avoid having to do a re-install of my OS as that is always a pain, but if that is the only way, so be it. 

I also do use windows 7 in a virtual machine for those things you need it for, if that will impact encryption choice...

Thanks for thoughts,

bg

---

### Post by lincoln32 on 2012-09-18
while I have not used it there is a option to use full encryption during a fresh install so I assume it could be converted. but good luck :guitar:

---

### Post by orange2k on 2012-09-18
> **lincoln32 said:**
> while I have not used it there is a option to use full encryption during a fresh install so I assume it could be converted. but good luck :guitar:

I don't think there is an option for full disk encryption in the standard installation...
But there is an option for it when installing from the alternate install Ubuntu...

In the standard installation there is only an option for home folder encryption...

---

### Post by Scott Harrison on 2012-09-18
What level of encryption do they require? Do you have a copy of the security policy they are implementing? It would be easier to provide accurate advice/options if we know exactly the minimum encryption standards they require.

If it's just hard drive level encryption of personal files, just encrypting your home drive in Ubuntu should be sufficient. See here: [http://www.makeuseof.com/tag/encrypt-home-folder-ubuntu-installation-linux/](http://www.makeuseof.com/tag/encrypt-home-folder-ubuntu-installation-linux/)

For full disk encryption using Ubuntu, you will require the alternate installer: [http://www.ubuntu.com/download/desktop/alternative-downloads](http://www.ubuntu.com/download/desktop/alternative-downloads) - you can Google for a guide to the install process.

As for Windows, TrueCrypt is a FOSS app that is great for full disk encryption. Unfortunately, you can only create a TrueCrypt volume within a HDD for Linux.

---

### Post by beenny on 2012-09-18
I believe it is full disk encryption. I don't have the full policy yet - just an email announcing - will try to send out when I can. I've seen about using the alternate CD for a fresh install. I'm trying to save that as a plan B as I just get irritated by fresh installs. 

I've seen TrueCrypt, but a lot of folks have talked against it. But is that the best alternative for not doing a fresh install?

I want to have a ready answer for them when they find their way to me...

Thanks,

bg

---

### Post by ShadowVegan on 2012-09-18
If I was in your place, I would back up all files on a USB drive, make a new user account, and encrypt it on creation (if your current account is not encrypted). Otherwise you could use TrueCrypt but as far as I know, it can only do full disk encryption for Windows, so you would be limited to encrypting individual files/folders (or maybe your entire user account? not sure).

---

### Post by bob-linux-user on 2012-09-18
Ubuntu 12.10 apparently has full disk encryption if you can hold on until then. I have not used it myself so cannot make any recommendation.

[http://www.pcworld.com/article/262248/five_new_features_in_ubuntu_12_10_quantal_quetzal_beta_1.html](http://www.pcworld.com/article/262248/five_new_features_in_ubuntu_12_10_quantal_quetzal_beta_1.html)

---

### Post by beenny on 2012-09-18
Thanks for the suggestions. Holding off till 12.10 is definitely possible given the pace that things move and if not I will try offer TrueCrypt as a stalling technique...

bg

---

### Post by grahammechanical on 2012-09-19
On the principle of baffling them with science you might make use of this information:

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

Does your machine have an option to set a password in the BIOS that is needed in order to even boot?

Prove to them just how secure you can make your machine.

Regards.

---

### Post by beenny on 2012-09-19
So looks holding off till 12.10 will work - IT has me at the bottom of the list :D 

What doesn't seem clear to me from poking around if this will require a fresh install or can I just do regular updating as I typically do?

Thanks,

bg

---

