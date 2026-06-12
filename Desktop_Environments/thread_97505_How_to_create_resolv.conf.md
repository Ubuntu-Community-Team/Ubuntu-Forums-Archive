---
title: "How to create resolv.conf"
date: 2005-12-01
forum: Desktop Environments
---

### Post by sprucemoose on 2005-12-01
Hi everyone!
I've installed Breezy Badger 5.10 having moved from Xandros and everything's looking very nice apart from me not being able to get online using dial-up.
I know from previous experience that I have to create resolv.conf in /etc but, having opened kate to create it I, am unable to save it.  In Xandros I was asked for the root password before it would save but this option doesn't appear when using KUbuntu.  I have changed the root password and tried logging in as root at the login screen but is says that root isn't allowed to log in.  I am unsure how you would create it using the command line.

How do I create it?

I'm online at the moment using Damn small linux.

Also, how do I run alsaconf in KUbuntu?  I get an error message (alsa doesn't seem to exist) when I type sudo alsaconf.

Many thanks in advance.

---

### Post by GeneralZod on 2005-12-01
Welcome to Kubuntu!

Try:

```

kdesu kwrite /etc/resolv.conf

```

instead.  The password will be your usual user password.

Ubuntu uses "sudo" instead of the usual user/ root separation; see [here](https://wiki.ubuntu.com/RootSudo) for more details!

---

### Post by sprucemoose on 2005-12-01
Thanks for that, however I'm back to using DSL.

KPPP will dial etc. however, now the ppd daemon dies unexpectedly when it should be connecting.
I tried using sudo kppp, pppconfig and then pon tiscali, sudo pppconfig and then sudo pon tiscali but all to no avail.  I keep getting something along the lines of unable to find any suitable secret password remote system unable to authenticate itself.  I also tried sudo pppd and then advanced options and allowing a normal user, but no luck.  Also tried removing the lock file option on the modem config.

A pain the arse as I keep having to shutdown and boot DSL to get here and then shutdown and boot KUbuntu to try again. 
I'm using a serial modem, not that it should give me any problems.

THanks again.

Any ideas?  I seem to remember having this problem with Xandros but can't remember how I solved it.

---

### Post by GeneralZod on 2005-12-01
[QUOTE=sprucemoose]
Any ideas?  I seem to remember having this problem with Xandros but can't remember how I solved it.[/QUOTE]

You need to set the "noauth" flag; try this:

[http://ubuntuforums.org/showthread.php?t=81216&highlight=noauth](http://ubuntuforums.org/showthread.php?t=81216&highlight=noauth)

---

### Post by sprucemoose on 2005-12-01
Aaah, nice one General.  That seems to ring a bell.  I'll let you know one way or the other.
Many thanks for your help.  Much appreciated.

---

### Post by sprucemoose on 2005-12-01
All done and dusted.
Thanks again.

---

### Post by GeneralZod on 2005-12-01
[QUOTE=sprucemoose]All done and dusted.
Thanks again.[/QUOTE]

Glad you got it working; no probs :)

---

