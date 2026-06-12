---
title: "GNOME in Kubuntu"
date: 2006-06-02
forum: Desktop Environments
---

### Post by guice on 2006-06-02
Is there any known stability issues in running GNOME in Kubuntu? 

I've followed [Psychocats's guide](http://www.psychocats.net/ubuntu/gnome.html) to get GNOME loaded on Kubuntu so I can check it out, but I'm having some problems.

For starters, the desktop isn't stable. I can change themes and cause problems with programs starting up. I've been able to cause GNOME programs to crash upon initial window drawing. I've got my GNOME desktop in an infinite crash loop just by using gdm instead of kdm. I've gotten the Clock Applet to fail to load multiple times just by switching to the Glade theme.

At one point I had the desktop locked up so much, I don't know what was wrong...I logged in via my windows box using ssh and did a pkill -u on my user account. My SSH session died, and something else died, but not all my processes. What ever it was, it "freed up" GNOME and every single application and window I tried to open up opened up! I had a desktop full of junk...

All in all, it just didn't feel any bit stable using it. 

I've been playing with it's stability on and off for a bit and I think i got it working now. The final ditch attempt was the removal of all .g* from my home directory. Even seems to be working with gdm now, which is interesting.

Anyway, I'm curious of any user experiences with it. I understand there is no difference in the base OS, but I'm thinking maybe there's some conflicts with kubuntu-desktop and ubuntu-desktop.

(PS: Anybody know a nice GNOME version of yakuake? It's so nice being able to use F12 in KDE to pop open a terminal window. Everything but the transparency works in GNOME. I liked the transparency. ^_^)

---

### Post by mocha on 2006-09-10
I'm having exactly these same problems after installing Gnome after Kubuntu.  Did you ever find a fix?

---

### Post by chavo on 2006-09-10
I came up with a fix for this but I'm not sure who to submit it too. I'm not really a coder but I hacked the gtk-qt engine to work differently and nor cause this problem. My code works but it's ugly. I'm sure if I could talk to the right person and explain to them what I did, they could code it up the right way.

Basically what happens is the gtk-qt engine writes a .gtkrc-2.0 file in your home dir. Then adds a line to your .bashrc to set GTK2_RC_FILES=~/.gtkrc-2.0.

Now this isn't a problem if you don't log into gnome. But when you do it is referencing the .gtkrc-2.0 file and trying to use the gtk-qt engine. The engine wasn't designed to be used under gnome and is causing these crashes.

A workaround is to remove the file before you log into gnome.
The way I fixed it was to have it write out ~/.gtkrc-qt instead of .gtkrc-2.0 and instead of .bashrc I used a script in ~/.kde/env to set the variable. This way it is not set when you log in to any other desktop.

---

### Post by mocha on 2006-09-10
Did you file any bug reports on this, or is it not considered a bug?

---

### Post by chavo on 2006-09-11
That's one problem it was filed as a bug but they closed it. Well it's obviously not fixed. I can't follow up on it right now as I'm having major problems with my computer hardware. I'm running off the Mandriva 2007 RC live CD right now. I think my motherboard is toast and can't access my drives.

---

