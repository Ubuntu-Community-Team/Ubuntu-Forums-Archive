---
title: "Restoring gnome"
date: 2008-11-11
forum: Desktop Environments
---

### Post by blackriven on 2008-11-11
A long while ago I had a gnome problem where certain parts of my GUI disappeared and I was unable to use it. You can find the original post here: [http://ubuntuforums.org/showthread.php?t=909347](http://ubuntuforums.org/showthread.php?t=909347)

I followed the steps that were suggested to me, and they didn't work. At the time I was tired of customizing Ubuntu, so I let it be, and now I want to fix it once and for all. 

My question is: how do I restore gnome, as in doing a complete reset, for my account? 

I currently have Hardy 8.04, and an HP Pavilion dv6500

---

### Post by hictio on 2008-11-11
Try this, from a console, not a gnome-terminal:

```

mv .gnome .gnome.back (ENTER)
mv .gnome2 .gnome2.back (ENTER)
mv .gconf .gconf.back (ENTER)
mv .gconfd .gconfd.back (ENTER)
mv .metacity .metacity.back (ENTER)

```

Logout, move to a Virtual Console (press Ctrl + Alt + F4, for instance), login as your user, type the above commands, logout, go back to the graphical login Virtual Console (press Ctrl + Alt + F7) login onto Gnome.
This was sort of the defacto way of going back to the default Gnome settings, you'll loose every customization you'd have done.

---

### Post by blackriven on 2008-11-11
I tried it, and now I just don't have any GUI. Also, my temp user is experiencing problems for some reason (file browser hangs and Firefox won't start up (it disappears from the bottom panel and alt+tab doesn't bring it)).

---

### Post by hictio on 2008-11-11
> **blackriven said:**
> I tried it, and now I just don't have any GUI. Also, my temp user is experiencing problems for some reason (file browser hangs and Firefox won't start up (it disappears from the bottom panel and alt+tab doesn't bring it)).

Do you have Compiz enabled?

---

### Post by blackriven on 2008-11-11
Yes.

---

### Post by blackriven on 2008-11-11
Um.. the 'yes' was in response to the above question.

---

