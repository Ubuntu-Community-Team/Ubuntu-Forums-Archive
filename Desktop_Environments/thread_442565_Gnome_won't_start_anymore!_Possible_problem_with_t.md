---
title: "Gnome won't start anymore! Possible problem with theme-manager"
date: 2007-05-13
forum: Desktop Environments
---

### Post by zooounds on 2007-05-13
Hi!

I was playing around in gnome-theme-manger and noticed that some themes didn't work as I kept my /home från my old installation and it seems like some things is cached. Theme manager crashed and not I cant log in at all.


Please. I'm panicing.

Is there any log where I can se why gnoem hangs when starting?

Is there any way to wipe any customisation for themes?

---

### Post by floke on 2007-05-13
Can you log in in failsafe gnome, or to the terminal?

---

### Post by zooounds on 2007-05-13
> **Steve.K said:**
> Can you log in in failsafe gnome, or to the terminal?

Terminal works. Failsafe gnome just hangs.
Other users can log in but it seems lika an awful lot of job replaicing my user.
I have tried moving away any .gnome2* directory but it won't work anyway.

Oh I HATE Feisty. Nothing but problem since the upgrade ...

---

### Post by floke on 2007-05-13
Ok, here's a crude way of restarting your gnome settings. Warning - all your settings (but not your data; files etc.) will be lost (but they look gone anyway). You need to delete the following from your user account

.gconf
.gconfd
.gnome
.gnome2
.gnome2_private

for good measure you could destroy the .xauthority and .ICEauthority files

when you restart, gnome will recreate them as defaults

This 'should' do it.

Good luck (and consider this an unwanted, enforced, but ultimately character-building learning experience :) )

---

### Post by zooounds on 2007-05-27
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/control-center/+bug/114647](https://bugs.launchpad.net/ubuntu/+source/control-center/+bug/114647) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				The last comment solved my problem.

If I start theme-manager I have themes in the list that I don't have installed (anymore). How do I remove them? It's the reason it crashes and destroy my account settings.

---

