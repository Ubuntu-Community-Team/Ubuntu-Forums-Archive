---
title: "Switching back from KDE To Gnome"
date: 2007-03-24
forum: Desktop Environments
---

### Post by nathanhillinbl on 2007-03-24
Ok, about a week ago, i decided to switch to KDE from Gnome, just to try it out. To tell you the truth, i dont really like it, but i absolutely love all the apps that you can install extra with it. How do you uninstall kde but keep all the apps? I know you have to keep the libs, but i'm not sure exactly what i can remove.

---

### Post by FXWGBill on 2007-03-24
You can keep all the apps and stuff but I think ya have to also keep most of the KDE setup, in order to do so.   I just keep em both on here as each has it's own merits...

---

### Post by WiseElben on 2007-03-24
You can delete kde-base (I think that's what it's called) and it should keep all your KDE applications. Even if you do accidentally delete kde-desktop, you can install the KDE apps on Gnome with no problems. You might even want to keep KDE but just use Gnome. You can switch desktop environments (KDE, Gnome, etc) at your login screen.

---

### Post by Pikestaff on 2007-03-24
If you end up having problems with running KDE apps in Gnome (it seems to happen occasionally) and you're feeling adventurous, there's a pretty good guide to get KDE to look [nearly identical to Gnome]("http://www.mutube.com/mu/kubuntu-like-you-ubuntu/").  Obviously there would still be some differences but if you're running a lot of KDE apps it might be something to look into... though I'd recommend trying what everyone else said, first.

---

### Post by rsnow on 2007-03-24
> **FXWGBill said:**
> You can keep all the apps and stuff but I think ya have to also keep most of the KDE setup, in order to do so.   I just keep em both on here as each has it's own merits...

I am new and still learning Gnome but have been wondering if it was possible to have both Gnome and KDE on the same computer and how does one set that up?

---

### Post by tubasoldier on 2007-03-25
> **rsnow said:**
> I am new and still learning Gnome but have been wondering if it was possible to have both Gnome and KDE on the same computer and how does one set that up?

Yes, you can. You can easily run both. When the login screen pops up you just click on sessions and the select the session you want. Either Gnome or KDE. kde-base is much better and easier to clean up than kubuntu-desktop. Good Luck.

---

### Post by FXWGBill on 2007-03-25
Actually there are several different desktops that you can play with.  Just do a search for 'desktop' in synaptic and see what all comes up.  some of them are pretty slick

---

### Post by aysiu on 2007-03-25
Why remove KDE at all? Surely you can't be *that* low on hard drive space. Just don't log into KDE. Use Gnome.

---

### Post by patrickfromspain on 2007-03-25
I use gnome, but there are 3 apps I can't live without: k3b, amarok and kaffeine. And I just use them. If I won't use kde, uninstall it (will quite difficult if you didn't use aptitude..) and the install the apps you want.

---

### Post by rsnow on 2007-03-25
> **tubasoldier said:**
> Yes, you can. You can easily run both. When the login screen pops up you just click on sessions and the select the session you want. Either Gnome or KDE. kde-base is much better and easier to clean up than kubuntu-desktop. Good Luck.

O.K. Thanks, I'll give it a try.

---

### Post by nathanhillinbl on 2007-03-31
The KDE login screen, splash screen, and some icons (such as the logout) are still there when i selected gnome as default, how do i revert those to the gnome standard?

---

### Post by aysiu on 2007-03-31
Log out.

Press Control-Alt-F1

Log in.

Type ```
sudo /etc/init.d/kdm stop
sudo nano -B /etc/X11/default-display-manager
``` Change the line from ```
/usr/bin/kdm
``` to ```
/usr/sbin/gdm
``` Then save (Control-X, Y, Enter) and ```
sudo /etc/init.d/gdm restart
```

---

### Post by Akrash on 2007-04-11
I have both Gnome and Kde. But when I log into kde the main bar at the bottom will not load/show. What should I do? I can do commands but I'm a noob with CLI.

---

### Post by aysiu on 2007-04-11
> **Akrash said:**
> I have both Gnome and Kde. But when I log into kde the main bar at the bottom will not load/show. What should I do? I can do commands but I'm a noob with CLI.
Press Alt-F2 and type ```
kicker
```

---

### Post by anshuljain on 2007-04-12
I just decided to ditch KDE for Gnome (Kubuntu -> Ubuntu). I really love KDE's look and the apps that come with it, particularly Amarok and K3B. But the instability is just too much to bear. Adept keeps crashing, its replacement KPackage is no better. Firefox is verry slow. Beryl slows down the interface and there is no proper Compiz support for KDE. 

Oh well...not everything is perfect..:)

---

### Post by KeeperOS on 2007-04-21
Wow, I decided to give Kubuntu another chance and what do you know, I stumbled on this thread... I loved (read:**loved**) that Kubuntu to Ubuntu tutorial!
Not to mention that either the latest KDE or my latest snooping around showed that I can now make all GNOME based appz look good under KDE!
I just did the tutorial, DLed Firefox and synaptic and now I'm one happy mother :twisted:

---

### Post by jimbojambo on 2007-04-22
aysiu, I'm not the original poster, but I was in the same situation. I had Ubuntu, installed kubuntu-desktop, didn't like it, and wanted to switch back. I followed your directions, but ... gnome just isn't the same.

I'm using Feisty Fawn, and the nice default system fonts have all been replaced with pre-Feisty ones, by the looks of it. Also, my window title bars are thicker, and the min/max/close widgets are bigger. When I restart/boot up Ubuntu, it still shows the Kubuntu graphic (with the scroll bar beneath). My usual resolution is 1680x1050, but when I get to the login screen, it's reset to 1024x768, and I have to set it back to max once Gnome finished loading.

Blarg.

Any ideas? Thanks. :)

---

### Post by orb9220 on 2007-04-22
jimbojambo you may want to make your own thread. Since aysiu posted that a week ago and may not see it.

aysiu is a really helpful person with much info to offer.

---

### Post by jimbojambo on 2007-04-22
You know, I have a feeling fixing this might take a lot of work. I think I'll just do a fresh install of Feisty over the existing install. It's not a big deal. I just installed Feisty yesterday, so I didn't get too far into personalization.

---

