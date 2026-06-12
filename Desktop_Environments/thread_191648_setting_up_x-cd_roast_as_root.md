---
title: "setting up x-cd roast as root"
date: 2006-06-07
forum: Desktop Environments
---

### Post by learning curve on 2006-06-07
How do I set-up and configure x-cd roast from root?  When I open it now it gives me a warning saying no root configuration file found or not readable.  The superuser must start and configure x-cd roast first, before others can use it.

Help!!!

Learning Curve

---

### Post by arizonagroovejet on 2006-06-08
Personally I wouldn't bother. I'd just use K3B as it 'just works'.

---

### Post by oyvindaa on 2006-06-08
Can be done in two ways I think:

1. Open a terminal and type sudo -s , then your password. Next, you type xcdroast.

2. Run a command from the K-menu, just type in the command xcdroast, and tick the "Run as another user"-box below. Then type root in the username section. You can also add the root password further down.

I'm not sure whether this still applies, I remember it from a Linux book I have. It should me nearly the same procedure anyway.

---

### Post by gubemton on 2007-12-16
> **arizonagroovejet said:**
> Personally I wouldn't bother. I'd just use K3B as it 'just works'.

Thanks for the K3B tip. I couldn't get X-CD roast to work, but K3B works like a charm!

I tried Oyvindaa's tip and it didn't work for my Ubuntu 7.10 x386 install. Specifically, the "Run a command from the K-menu" confused me, as no GUI popped up and I'm not sure what the K-menu is (Kubuntu? Sorry, I'm completely green here).

Some day I'll be a command line hero, but tonight I just need to burn my 7.10 Server .iso so I can start exploring serverland.

Thanks to both posters for the tips (even though it's a year later and I doubt they will see this).

---

### Post by kcyow on 2008-03-05
Don't worry, at least I read your reply and your year late courtesy :)

This is the first post I come across regarding the aforementioned problem, the problem still persists (for me, thus far). I'll continue googling for the solution. I'm reluctant to accept k3b as the solution to the problem as k3b is sort of a KDE based application rather than a GNOME one which Ubuntu uses as default.

Cheers,
yow778

---

