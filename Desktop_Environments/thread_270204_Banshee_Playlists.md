---
title: "Banshee Playlists??"
date: 2006-10-02
forum: Desktop Environments
---

### Post by Stochastic on 2006-10-02
Hi, I'm trying to move a playlist off my account in Banshee to my roommate's account in Banshee but I can't see any way of doing this and don't know where the playlist files are stored, can anyone help? thanks.

---

### Post by aysiu on 2006-10-02
I think it's probably /home/stochastic/.gnome2/banshee/banshee.db

---

### Post by Stochastic on 2006-10-02
Hmmm, looks like it's all in one big file SQL Lite file, any reccomendations as to how to get only one of my playlists to move into my roommate's file without replacing all of her playlists and overwriting things?  I'm a complete newbie when it comes to databases, so the easiest route is best.  Thanks.

---

### Post by aysiu on 2006-10-02
No idea. Banshee doesn't offer you an export playlist or save playlist option?

---

### Post by Stochastic on 2006-10-02
> **aysiu said:**
> Banshee doesn't offer you an export playlist or save playlist option?

Nope, not that I can see.

---

### Post by aysiu on 2006-10-02
It's a feature request right now:
[http://banshee-project.org/FeatureRequest](http://banshee-project.org/FeatureRequest)

---

### Post by Stochastic on 2006-10-02
Is there any way to do this before the developers get around to it?  Maybe through an editor like OpenOffice Database?  I don't know anything about SQL Lite.

---

### Post by aysiu on 2006-10-02
> **Stochastic said:**
> Is there any way to do this before the developers get around to it?  Maybe through an editor like OpenOffice Database?  I don't know anything about SQL Lite.
Nor do I, unfortunately.

This could be kind of dangerous, but if you open in Kate (Gedit doesn't work for this, apparently), you can see the text in the SQ Lite file... copy and paste? Uh, make a backup copy first, of course.

---

