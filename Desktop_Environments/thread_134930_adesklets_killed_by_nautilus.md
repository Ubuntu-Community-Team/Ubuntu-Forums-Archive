---
title: "adesklets killed by nautilus"
date: 2006-02-22
forum: Desktop Environments
---

### Post by guano on 2006-02-22
So, I give up on Gnome and I am using OpenBox now. I liked it, and found adesklets to give some eye candy, llike calendar and battery stats. I really want to make this machine light, so I'm not using gdesklets, I don't want to use much gnome resources.
The thing is that when I start Nautilus (nautilus --no-dekstop), all adesklets are killed!
 - I know I just said I don't want to use gnome resources, and then said I use Nautilus. Ok, but IMO it is the best file manager (better than Konqueror, Thunar, Rox and xffm).

I really have no idea will it kills the desklets! Can someone point me a direction?

---

### Post by Xian on 2006-02-23
[QUOTE=guano]I know I just said I don't want to use gnome resources, and then said I use Nautilus. Ok, but IMO it is the best file manager (better than Konqueror, Thunar, Rox and xffm).

I really have no idea will it kills the desklets! Can someone point me a direction?[/QUOTE]

I've seen this in every distro I've ever tried and I've never been able to nail down the issue. My advice would be to contact the developer. Also, I would get rid of Nautilus and try something like xfe or pcmanfm instead. That in and of itself would solve your problem. I know you like Naughty, but xfe is great once you get used to the environment.

---

### Post by guano on 2006-02-23
Hey Xian, thanks for the tip about pcmanfm! I just compiled it (no debs... at least no wroking ones in Breezy) and it's really good!

---

### Post by syfou on 2006-02-23
This issue [has been fixed](http://adesklets.sourceforge.net/forum/viewtopic.php?t=237) in adesklets code base a few months back... I know [Dapper](http://packages.ubuntu.com/dapper/x11/adesklets) includes a much more recent version than [Breezy](http://packages.ubuntu.com/breezy/x11/adesklets) in universe, that doesn't display this problematic behavior.

---

