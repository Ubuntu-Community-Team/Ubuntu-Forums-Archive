---
title: "Gnome Login Looping"
date: 2005-12-22
forum: Desktop Environments
---

### Post by SteveHil on 2005-12-22
I'm very new to Linux and completely stumped. I've just upgraded from Hoary to Breezy, but I must have done it wrong because I can't get into the GUI. This is bad for me as the command line interface is very unfamiliar.

I get a loging dialogue with the message "The configuration file contains an invalid command line for the login dialog. So running the default command. Please fix your configuration"

(Which configuration file is it talking about?)

I can then type in my userid, and the password screen comes up. But as soon as I type ANYTHING into the password field - any character at all - don't even have to press 'enter', the screen momentarily drops back into a terminal screen, then before I can do anything it goes back to the GUI login with the original error message.

After doing this a few times it does eventually give up and stay in terminal mode. 


Reading through some of the threads here I have tried:

dpkg-reconfigure gdm
dpkg-reconfigure gnome

no luck, so tried reinstalling gnome
apt-get remove gnome
apt-get install gnome

also apt-get install xubuntu-desktop

i've even tried dpkg-reconfigure -a 

These commands all seem to work OK, but I still end up with the looping gui login screen that I can't get past. 


If I knew which configuration file it was talking about, and what the invalid command is, I might stand a chance.

Steve

---

### Post by Ampersand on 2005-12-22
You might have some luck with
```
sudo apt-get remove gnome --purge
sudo apt-get install gnome

```

to remove the configuration files as well, since these seem to be causing problems.

---

### Post by SteveHil on 2005-12-25
Thanks

That --purge did the trick.


Steve

---

### Post by Neobuntu on 2006-05-07
[QUOTE=SteveHil]Thanks

That --purge did the trick.


Steve[/QUOTE]

Nope, didn't work for me. Why is it looping and how do I start to fix this?

---

