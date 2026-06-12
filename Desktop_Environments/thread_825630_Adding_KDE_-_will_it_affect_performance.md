---
title: "Adding KDE - will it affect performance?"
date: 2008-06-11
forum: Desktop Environments
---

### Post by anton on 2008-06-11
Here's a quick question from a new Linux/Ubuntu convert:

Will my system take a performance hit if I add KDE to my current Gnome setup?  Or is it better to have a separate Kubuntu installation?

---

### Post by vishzilla on 2008-06-11
You can add packages to your will. After installation, select KDE from the GDM session

---

### Post by anton on 2008-06-11
> **vishzilla said:**
> You can add packages to your will. After installation, select KDE from the GDM session

I realize that there's no problem adding the KDE packages. What I'm asking is if it will affect performance in any way --  e.g. will Ubuntu take longer to boot up because of all the extra installed packages?

---

### Post by vishzilla on 2008-06-11
> **anton said:**
> I realize that there's no problem adding the KDE packages. What I'm asking is if it will affect performance in any way --  e.g. will Ubuntu take longer to boot up because of all the extra installed packages?

It depends on the memory you have, how much is your memory?

---

### Post by vanadium on 2008-06-11
This will not affect performance in any way. You will only use some more disk space.

---

### Post by anton on 2008-06-11
> **vishzilla said:**
> it Depends On The Memory You Have, How Much Is Your Memory?

1gb

---

### Post by anton on 2008-06-11
> **vanadium said:**
> This will not affect performance in any way. You will only use some more disk space.

Thanks, I'm gonna give it a try.  Some people complain that it clutters up the menu's, but I guess it's a simple matter to remove the unwanted items?

---

### Post by snkiz on 2008-06-11
I've done this before and my box isn't very powerful the answer is a little more complex than that. using Kde apps in gnome does effect performance as the kde runtime liabries need to be loaded, same with running gnome apps in kde. those files are normally loaded by Gdm (or Kdm) So your boot time to the login so be the same just getting to your desktop will be a little slower. I have read posts that tell you how to start Kdm in another console never tried it though

---

### Post by vanadium on 2008-06-11
I do not see why the gnome desktop would load slower if you have also KDE installed on disk. Only when you start a KDE app under gnome will it tend to load somewhat slower than if you launch it from a KDE session. The same applies if you do not have KDE desktop installed at all.

---

