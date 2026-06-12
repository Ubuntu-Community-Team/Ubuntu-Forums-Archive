---
title: "Root Password"
date: 2008-12-11
forum: General Help
---

### Post by brucey1st on 2008-12-11
Hi guys ive got wubi installed with nps ...

I am a q3 user for many yrs, and a friend who uses a different distro, was trying to walk me through on amsn on how to install Quake3 native ...

Everything went well untill it asked me for the root password?

Can someone tell me how to enable this please?

Cheers Brucey

---

### Post by Jammanuser on 2008-12-11
> **brucey1st said:**
> Hi guys ive got wubi installed with nps ...

I am a q3 user for many yrs, and a friend who uses a different distro, was trying to walk me through on amsn on how to install Quake3 native ...

Everything went well untill it asked me for the root password?

Can someone tell me how to enable this please?

Cheers Brucey

WHAT!? u mean u typed it, and forgot what the password was? :D

To fix this, see: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Hope this helps! ):P

Cheers! :popcorn:

-jammanuser

:guitar:

---

### Post by brucey1st on 2008-12-11
Hi thanx for the reply, but im looking for the "root password" that wubi doesnt give me when i install ...

I know ubuntu gives me this option if your doing a full install, but in wubi it doesnt?

This pc is my main machine, and i need xp on as well

Brucey

---

### Post by aysiu on 2008-12-11
There is no root password.

Read more here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by brucey1st on 2008-12-11
Hi thanx very much for the reply, just to clarify in wubi theres no root password?

But, i installed ubuntu full install on a old p4 pc, and it gave me this option? (Not Wubi)

Is this correct?

Cheers Brucey

---

### Post by aysiu on 2008-12-11
There's no root password in Ubuntu, Wubi-installed or otherwise.

Linux Mint (which is based on Ubuntu) gives you the option (at the end of the installation process) to use a traditional root password authentication instead of *sudo*. Vanilla Ubuntu does not.

---

### Post by brucey1st on 2008-12-11
Ah bugger, what a shame lol ubuntu is my fav distro, but so is Quake3 ...

Never mind

thanx for the reply

Brucey

---

### Post by Jammanuser on 2008-12-11
> **brucey1st said:**
> Hi thanx for the reply, but im looking for the "root password" that wubi doesnt give me when i install ...

I know ubuntu gives me this option if your doing a full install, but in wubi it doesnt?

This pc is my main machine, and i need xp on as well

Brucey

Theoretically, the user password that u give at the beginning of install of Wubi could be called the "root password" when one is operating as root user. However, like the other guy said, there is no **real** root password on Ubuntu...sometimes Ubuntu will ask for ur sudo password, though, which is really ur user password that will enable root (or administrative, if u want to go by Windows terms!) capabilities when u type it! ;)

Cheers! ):P

-jammanuser

:guitar:

---

### Post by Orlsend on 2008-12-12
You can log in, with the recovery mode which gives you root privileges.

---

### Post by Scribblah on 2008-12-14
I hope appropriate to pile on here with my own case. Forgotten password but I cannot, for the life of me, get to the recovery console option. I'm using 8.04 for PPC (2002 iBook). Pressing escape at boot (I've tried to do it at all sorts of stages) I can only get to "boot: _" with a line noting I can "enter "help" to get some basic usage information. It's also tells me I'm using Yaboot 1.3.13. Typing help first reports "...no such file..." but a second time and I get a message about how to boot a kernel image not defined in yaboot.  

I don't have data on the machine so I considered just rebuilding it but for some reason I'm getting a ram disk error when booting to the cd. Rather just get back into this one since I did some config work, but at this point trying to get this up an running for a 7 year old Christmas gift. Any assist appreciated.

---

### Post by Scribblah on 2008-12-14
Never mind. I learned how to get to the recovery console by typing Linux single after the "boot:" prompt. Then when that process starts, I hit ESC and then I get the recovery console. But as I learned [here]("https://bugs.launchpad.net/ubuntu/+bug/203206") after trying every imaginable combination, there is now way to select other than the first option. The arrow keys aren't mapped.

I'm going to just focus on the ramdisk error and see if I can start over. Frustratingly maddening not to remember the password in addition to all these other hiccups. To think this gift - very nice for being a gift no doubt - was purchased for about the same price as a new 10" netbook... ahhhg.

---

### Post by used2bnewb on 2008-12-15
```
sudo passwd 
```

Followed by your root password

---

