---
title: "Cannot change Login Screen"
date: 2009-11-08
forum: Desktop Environments
---

### Post by vamc on 2009-11-08
I just installed Karmic after using Jaunty for a while.I am not able to change the login screen in Karmic like in jaunty.If i open the Login Screen window from System,it gives me a msg saying "when the computer starts up",leaving no scope for me to change the login screen.
Can any one help me out?:mad:

---

### Post by szerencsefia on 2009-11-08
> **vamc said:**
> I just installed Karmic after using Jaunty for a while.I am not able to change the login screen in Karmic like in jaunty.If i open the Login Screen window from System,it gives me a msg saying "when the computer starts up",leaving no scope for me to change the login screen.
Can any one help me out?:mad:
The GDM customization function is diabled in Karmic.

---

### Post by ziphi on 2009-11-08
I would like to change the login screen back to what it was on my system before the upgrade: just plain grey window on a black background, minimal options, no fancy graphics, no user list, password hidden. Is there a way to get back to that and get rid of this blueish sparkling thing?

Thanks a lot!

---

### Post by chico305 on 2009-11-16
> **vamc said:**
> I just installed Karmic after using Jaunty for a while.I am not able to change the login screen in Karmic like in jaunty.If i open the Login Screen window from System,it gives me a msg saying "when the computer starts up",leaving no scope for me to change the login screen.
Can any one help me out?:mad:

IM having the same problem u find out a way to fix it et

---

### Post by jes-13 on 2009-11-26
> **szerencsefia said:**
> The GDM customization function is diabled in Karmic.

Who's dumb idea was that??  :confused:  I had a really nice login window before I upgraded my laptop that also allowed XDMCP. That seems to be gone too.

I guess I'm going to downgrade back to 9.04 since Firefox no longer works either...  :(    I definitely won't bother upgrading any of my other systems.

---

### Post by falconindy on 2009-11-26
It's not that its disabled. It wasn't written by the folks at Gnome. Canonical's changes were made at the source level and recompiled especially for Karmic.

---

### Post by jes-13 on 2009-11-28
> **jes-13 said:**
> Who's dumb idea was that??  :confused:  I had a really nice login window before I upgraded my laptop that also allowed XDMCP. That seems to be gone too.

I guess I'm going to downgrade back to 9.04 since Firefox no longer works either...  :(    I definitely won't bother upgrading any of my other systems.

I wasn't trilled about downgrading and what *that* might break...  I found this post at ubuntu geeks forum: [[COLOR="Blue"]How to Downgrade Gnome Display Manager 2.28 to 2.20 in Ubuntu 9.10[/COLOR]]("http://www.ubuntugeek.com/how-to-downgrade-gnome-display-manager-2-28-to-2-20-in-ubuntu-9-10-karmic.html"). Seemed to do the trick for me. Gnome itself remains at 2.28, only gdm is downgraded.

---

### Post by raktarok on 2009-11-28
You can actually make some changes to the current gdm screen, like change the background, and even apply gtk themes to it. See this link for more details:
[http://www.ubuntugeek.com/how-to-setup-your-desktop-background-as-xsplash-gdm-in-ubuntu-karmic.html](http://www.ubuntugeek.com/how-to-setup-your-desktop-background-as-xsplash-gdm-in-ubuntu-karmic.html)

---

### Post by superotakuman on 2009-11-29
If you want an easier way to replace the login background with something else, just replace the image called bg_2500x1600.jpg. Rename the image replacement bg_2500x1600.jpg. It needs to be done as root, and is in the directory /usr/share/images/xsplash

---

### Post by Isengrin on 2009-11-29
> **szerencsefia said:**
> The GDM customization function is diabled in Karmic.

More accurate, it's not available in GDM 2.28

To have the GDM themes, you need to downgrade it to the direcly previous version (2.20.10) I don't know if Ubuntu has the package easily available.


A bad move from the developers, but I hope they reimplement it soon.

(Another good idea would be to try another login manager. SLIM is pretty light, altough there are not that many themes (still, making your own is easier than with GDM)).

---

