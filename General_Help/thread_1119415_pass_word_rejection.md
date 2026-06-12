---
title: "pass word rejection"
date: 2009-04-07
forum: General Help
---

### Post by tukatz on 2009-04-07
Hi, I recently attempted to install Ubuntu 8.04 on a Dell 5100 and have run into a problem. I have the same O/S on an ACER 5100, and have installed it as a dual boot along with Vista with no problem, and later, formatted the same unit & now run U 8.04 by it's self. When I 1st installed U 8.04 on the ACER, a partition was automatically created on my HD for Ubuntu, I'm guessing Vista did that, as I understand Linux cannot create partitions according to what I read. Here is my current dilemma: I attempted to install U 8.04 as a dual boot along side or within XP Home on a Dell 5100, with 1.5 Gb RAM, & 114Gb free space on the HD. Ubuntu appears to have installed, but upon startup or re-boot, it rejects the password as either being the wrong password, or being in the wrong case. I tried numerous times to boot up, even re-installing & changing the password, but always with the same results. I'm wondering if I have to manually create a partition to correct that, or if there is another problem. Does XP Home not create partitions automatically in dual boot situations? I checked the control panel, and U 8.04 is definitely there, but seems inaccessible. Puzzled in PG, Tukatz.

---

### Post by dcstar on 2009-04-08
> **tukatz said:**
> Hi, I recently attempted to install Ubuntu 8.04 on a Dell 5100 and have run into a problem. I have the same O/S on an ACER 5100, and have installed it as a dual boot along with Vista with no problem, and later, formatted the same unit & now run U 8.04 by it's self. When I 1st installed U 8.04 on the ACER, a partition was automatically created on my HD for Ubuntu, I'm guessing Vista did that, **as I understand Linux cannot create partitions according to what I read.**
.........

I have no idea what your read, but Linux can create partitions - just like every single other O/S.

---

### Post by leonardo_neo on 2009-04-08
Well, I guess you have very wrong ideas about dual boot. 

Read this link on how to install Ubuntu.......

[https://help.ubuntu.com/8.04/switching/installing.html]("https://help.ubuntu.com/8.04/switching/installing.html")

What password you are entering? Silly to ask, but are you entering your 'root' password, or your windows password??

---

### Post by tukatz on 2009-04-08
> **leonardo_neo said:**
> Well, I guess you have very wrong ideas about dual boot. 

Read this link on how to install Ubuntu.......

[https://help.ubuntu.com/8.04/switching/installing.html]("https://help.ubuntu.com/8.04/switching/installing.html")

What password you are entering? Silly to ask, but are you entering your 'root' password, or your windows password??
Hi Leonardo, during the installation process of Ubuntu, you are asked to provide a password in order to boot up. I used a simple 2 letter password in lower case, and later tried a name, also in lower case. At bootup, the system rejected the password in both cases. Incidentally, the password had nothing to do with XP. I had no problem with this on the ACER, which I am using here, but on the DELL, it won't recognise the password. I have a suspicion the problem arises with the partition thing, but I'm not sure. Seems to me I read somewhere in the "how to install Ubuntu" link that Linux doesn't partition your HD, (at least not automatically)
I was hoping someone could help me with this so I don't have to spend hours upon hours banging my head on the computer. Any suggestions would be greatfully accepted. Tukatz

---

### Post by tukatz on 2009-04-08
> **tukatz said:**
> Hi Leonardo, during the installation process of Ubuntu, you are asked to provide a password in order to boot up. I used a simple 2 letter password in lower case, and later tried a name, also in lower case. At bootup, the system rejected the password in both cases. Incidentally, the password had nothing to do with XP. I had no problem with this on the ACER, which I am using here, but on the DELL, it won't recognise the password. I have a suspicion the problem arises with the partition thing, but I'm not sure. Seems to me I read somewhere in the "how to install Ubuntu" link that Linux doesn't partition your HD, (at least not automatically)
I was hoping someone could help me with this so I don't have to spend hours upon hours banging my head on the computer. Any suggestions would be greatfully accepted. Tukatz
Hello again Leonardo, I miss-read the link about partitioning, it states "linux does not re-name drives... I may have found the answer to my boot up problem there, but I'm still puzzled. When I installed U 8.04 on my ACER, I remember a portion of the install process dealing with partitioning to which I simply ckicked "OK" & proceeded. This was alongside Vista. However, on the Dell, which has XP, I never got the same opportunity. Not being a huge techie, I'm guessing maybe it's how XP is written? If that's not it, I'm still up the creek so to speak. Tukatz

---

### Post by leonardo_neo on 2009-04-09
> **tukatz said:**
> Hello again Leonardo, I miss-read the link about partitioning, it states "linux does not re-name drives... I may have found the answer to my boot up problem there, but I'm still puzzled. When I installed U 8.04 on my ACER, I remember a portion of the install process dealing with partitioning to which I simply ckicked "OK" & proceeded. This was alongside Vista. However, on the Dell, which has XP, I never got the same opportunity. Not being a huge techie, I'm guessing maybe it's how XP is written? If that's not it, I'm still up the creek so to speak. Tukatz


Well that is how you Install Ubuntu. When you go with installation process, it asks for you language preference, then you time zone setting, the comes the partition thing. It can't bypass this step. In this step you have 3 choices to make. First, you let it go automatically (which I believe you did in your previous computer), second it allows you to adjust the size of your linux partition, and the third one is 'manual' with which you choose your Linux partition size whatever way you like it to be.

Ok, so I guess you need another tutorial to have a better idea on how to install Ubuntu with Xp. Please follow this new tutorial. This teaches how to install Ubuntu with pictures. 

> [http://www.psychocats.net/ubuntu/dualboot](http://www.psychocats.net/ubuntu/dualboot)

If you can't find your password, then you should install Ubuntu again according to the tutorial mentioned above. Please spend some time studying how to partition your drivers. That way you will tend to make less errors in your next installation. (In case you have to go for that)

---

