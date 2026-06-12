---
title: "New debian user"
date: 2008-12-31
forum: Debian
---

### Post by Dr Small on 2008-12-31
I'm a long time Ubuntu user and ArchLinux user, moving my server to Debian (here soon). My server currently runs Ubuntu 7.04, but the repositories have been dropped and I can't install software anymore.

Instead of installing Hardy or Ibex, I've decided to install Debian for a first time. On a spare box, I have ran the installer (netinst) several times. It seems like using 'expert' mode is what I want, because I can choose whether to install with a root user or sudo. (I want to use sudo).

Once I get it installed on my server, I'll have to get Wireless configured (temporarily, for installing SSH) and then I'll be reconfiguring networking for a static IP on ethernet.

Is there any recommended guides I should read first before moving on? Any other unforeseen precautions I should be aware of? I've installed Ubuntu many times via the alternate CD for a command line installation, and Debian didn't look much different than that.

Dr Small

---

### Post by Bachstelze on 2008-12-31
> **Dr Small said:**
> 
It seems like using 'expert' mode is what I want, because I can choose whether to install with a root user or sudo. (I want to use sudo).

There's no need to run the installer in expert mode just for [font="monospace"]sudo[/font]. Just install your system normally, it is very easy to configure [font="monospace"]sudo[/font] afterwards (and disable the root account if you want, though I personally prefer to keep it, just in case I would need it for some reason).

There's nothing particular to know before installing Debian. Just keep the usual stuff in mind (most importantly, think before you do something and ask when you're in doubt) and you will be fine.

---

### Post by Dr Small on 2008-12-31
Thanks, I'll do that. Arch didn't come with sudo either, and I had to manually install it. I just guessed it would be different to setup, but even if it is (which it probably isn't), it will be a learning expirience for me :D

I don't mind getting on a console, rolling up my sleeves and getting them dirty :)

Thanks for replying.

---

### Post by albinootje on 2008-12-31
> **Dr Small said:**
>  Is there any recommended guides I should read first before moving on? Any other unforeseen precautions I should be aware of? I've installed Ubuntu many times via the alternate CD for a command line installation, and Debian didn't look much different than that.

I think it's good to know that Ubuntu has been *completely* re-designed to be used with sudo.
That's not the case with Debian.
This means for example that after installing sudo, you will need to do :
```

visudo

```
as root. 

If you prefer the Ubuntu way of using sudo, use this line :
```

%admin ALL=(ALL) ALL

```
And add your own username to the admin group.
You can of course also use : 
```

yourusername ALL=(ALL) ALL

```
And I haven't tried this, but I can imagine that if you decide to disable the root password in Debian, after enabling sudo properly, that the recovery mode works different than in Ubuntu.
It might still ask for your root password, whereas Ubuntu would give you this menu with "drop to root shell prompt" without a need for a password.

---

### Post by polmir on 2009-01-01
[http://www.debian.org/doc/index.en.html]("http://www.debian.org/doc/index.en.html")

[http://www.debian.org/doc/user-manuals.en.html]("http://www.debian.org/doc/user-manuals.en.html")

	
During the installation in expert mode, you can choose to use sudo.

Select a minimum installation CD NetInstall Lenny.

[http://cdimage.debian.org/cdimage/daily-builds/daily/current/i386/iso-cd/]("http://cdimage.debian.org/cdimage/daily-builds/daily/current/i386/iso-cd/")

---

### Post by albinootje on 2009-01-01
> **polmir said:**
> 

Select a minimum installation CD NetInstall Lenny.

[http://cdimage.debian.org/cdimage/daily-builds/daily/current/i386/iso-cd/]("http://cdimage.debian.org/cdimage/daily-builds/daily/current/i386/iso-cd/")

Interesting. Thanks for this link.

---

### Post by hyperyoda on 2009-01-18
Hi Dr. Small,

This is zu22 from grubbn. I sent you a friend request. I run Debian lenny on my server and it pwns. Very stable.

Zach

---

### Post by notwen on 2009-01-20
I've been running Debian for my server for as long as I can remember, currently running Etch, only started using Ubuntu for my daily usage PCs/laptops.  I doubt you'll run into any issues, but when in doubt don't hesitate to post. =]

---

### Post by Bachstelze on 2009-01-20
Sid for ever. :o

---

### Post by linkmaster03 on 2009-01-20
Debian is pretty easy to install. I never encountered any problems. Personally after that it just feels like Ubuntu without the bloat.

---

