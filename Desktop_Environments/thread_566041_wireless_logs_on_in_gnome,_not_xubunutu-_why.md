---
title: "wireless logs on in gnome, not xubunutu- why?"
date: 2007-10-03
forum: Desktop Environments
---

### Post by neatokino on 2007-10-03
I have Feisty Ubuntu (Gnome), Kubuntu, and Xubuntu loaded on my laptop (12" PowerBook G4, 1st generation).   Gnome works pretty well, and it (usually) audomatically finds my wifi and connects on startup (usually but not always asks for my keyring manager password).  I prefer Xubuntu, however, and would like to make it my default session.

If I log on with Gnome, then log out and log back in with Kubuntu or Xubuntu, the wireless connection works fine in Kubuntu and Xubuntu.

If I log on with Kubuntu or Xubuntu from start up, the wifi does not connect.  If I open the network manager, it shows my wifi setup - password and everything, but for some reason, no attempt is made to connect to it.

Is there a way to make the computer connect to my wifi upon startup in Xubuntu and Kubuntu?  I'd quite like to make Xubuntu my default operating system, but I certainly don't want to have to log in and out of Gnome just to get the wifi working.

What's up with that keyring manager, anyway?  I don't feel a need to enter a password to access my wifi every time I turn the computer on.

Any thoughts?

---

### Post by 5-HT on 2007-10-03
> **neatokino said:**
> 
Is there a way to make the computer connect to my wifi upon startup in Xubuntu and Kubuntu?  I'd quite like to make Xubuntu my default operating system, but I certainly don't want to have to log in and out of Gnome just to get the wifi working.

A trivial fix: just have nm-applet autostart in XFCE or KDE as it does in Gnome.
> **neatokino said:**
> 

What's up with that keyring manager, anyway?  I don't feel a need to enter a password to access my wifi every time I turn the computer on. 
Nothing's wrong with it. You may not feel a need to enter a password everytime you connect, but other people in other situations might and the default is that of security. You can always peel back any layers you do not want to use.
It's a really simple fix to prevent the need to enter your password upon every connection [http://ubuntuforums.org/showpost.php?p=2884458&postcount=2](http://ubuntuforums.org/showpost.php?p=2884458&postcount=2)


Cheers,

---

### Post by neatokino on 2007-10-03
Thank you thank you thank you!  Now, because I'm still new to all this, how exactly do I add the nm-applet to startup?

TIA

---

### Post by 5-HT on 2007-10-03
> **neatokino said:**
> Thank you thank you thank you!  Now, because I'm still new to all this, how exactly do I add the nm-applet to startup?

TIA

Sorry, it's been a while since I've last used XFCE, but I believe that it has its own 'startup applications' box somewhere in the preferences. That would be the easiest way to do it, and hopefully someone else running Xubuntu can confirm exactly where the option is in the menu. 

If not, you can always add a file containing 'nm-applet &' to ~/Desktop/Autostart/ and that'll do the trick.

cheers,

---

### Post by neatokino on 2007-10-04
Thank you!

---

