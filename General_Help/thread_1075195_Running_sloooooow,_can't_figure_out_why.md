---
title: "Running sloooooow, can't figure out why"
date: 2009-02-20
forum: General Help
---

### Post by BrentNewland on 2009-02-20
I've had my system installed for about a year and a half. At first it was really responsive, very fast and snappy (even before upgrading to 1GB RAM) but now it all runs very slow. I can't for the life of me figure out what would be causing this problem. I've tried running BUM and removing some packages, but it doesn't seem to help much.

I've attached three pictures, top, top2, top3, showing my usage before and after running bum and some other tweaks and after letting it run with firefox for a while. top was run with cumulative time on and sorted by total time. the biggest hog seems to be gnome-session and gconfd-2.

System is an Athlon XP 2800+ @ 2GHz (and don't tell me it's too slow) with 1GB DDR1 RAM. Version is 8.10 (upgraded since 7.04)


Any advice? The CPU usage seems inordinately high.

---

### Post by PointyWombat on 2009-02-20
> **BrentNewland said:**
> I've had my system installed for about a year and a half. At first it was really responsive, very fast and snappy (even before upgrading to 1GB RAM) but now it all runs very slow. I can't for the life of me figure out what would be causing this problem. I've tried running BUM and removing some packages, but it doesn't seem to help much.

I've attached three pictures, top, top2, top3, showing my usage before and after running bum and some other tweaks and after letting it run with firefox for a while. top was run with cumulative time on and sorted by total time. the biggest hog seems to be gnome-session and gconfd-2.

System is an Athlon XP 2800+ @ 2GHz (and don't tell me it's too slow) with 1GB DDR1 RAM. Version is 8.10 (upgraded since 7.04)


Any advice? The CPU usage seems inordinately high.

It does seem that gnome is the problem. I would create another user account and logout and login as that user and view stats again. I suspect it's something in your user account config (gconf or otherwise) that's causing it. Creating a new user to test this is easy enough and will help narrow down the problem. Also try logging out completely and ctrl-alt-F1 login at a console and see what stats you get.. The box should be mostly idle.

Just a thought..

---

### Post by BrentNewland on 2009-02-20
I'll give that a shot in a bit, but I have deleted my gnome and gconf folders in my home directory a few times to reset all the settings and it didn't help much.

---

### Post by PointyWombat on 2009-02-20
> **BrentNewland said:**
> I'll give that a shot in a bit, but I have deleted my gnome and gconf folders in my home directory a few times to reset all the settings and it didn't help much.

Hmm.. with that said, i'm wondering about the stats while only at console.. ctrl-alt-F1 login...

---

### Post by BrentNewland on 2009-02-21
Turns out that was the issue. I copied the important parts of my profile to a new one and all is finally good.

---

