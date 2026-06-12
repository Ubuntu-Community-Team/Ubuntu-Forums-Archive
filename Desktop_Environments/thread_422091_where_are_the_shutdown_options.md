---
title: "where are the shutdown options"
date: 2007-04-24
forum: Desktop Environments
---

### Post by glaeven on 2007-04-24
so, i'm using feisty now, and i have finally got it customized to my likings (almost, but its good enough).

then pops up a little issue i would have never thought about.

i shut my computer down when i'm not using it. i only use it at nights when i'm in my room, so its a waste to leave it on. now, the problem is shutting it down. when i go to Settings-->Quit. it doesnt give me the options menu i'm used to. it logs me out (i'm the only user). this makes shutting down a little complicated and takes much longer than needed.

is this a bug, or a new "feature"? :confused:

---

### Post by fearevilleet on 2007-04-24
you can just run the command 

```
sudo shutdown -r now
```

which will shutdown the system.

If you want a button that says shutdown you will need to log out of your account and you should see a shutdown button when you are asked to select a user.

---

### Post by Lokken on 2007-04-24
I think "shutdown -r now" reboots the system. "shutdown -h now" halts the system.

Lokken

---

### Post by phidia on 2007-04-24
Are you using the final release? 
My feisty install has the box with the Logout, shutdown, restart, hibernate , etc  icons, and that box pops up from selecting System>Quit

---

### Post by sblanzio on 2007-04-25
> **Lokken said:**
> I think "shutdown -r now" reboots the system. "shutdown -h now" halts the system.

Lokken

sure! however, i don't think this is a good solution.

if you do a console shutdown that kills the X server and most of the times this one doesn't save the session properly.

we should have a window-like query who asks what to do before logging out! (I guess kde owns that!)

bye

---

### Post by Tmi on 2007-04-25
I have the same "problem" (I keep my computer on so it's not really an issue for me). I have a log out button but no shut down button. If I want to turn my computer off I need to log out and the chose shut down in the login manager.

---

### Post by ronacc on 2007-04-25
this has been going on for awhile with feisty , various buttons dissapear form the actions menu then show up again , try running update manager to makesure you are uptodat , also in the top bar go to system>administration>login window>local and in the menu bar section make sure that show_action menu is checked. I don't know if there is a permenant fix for this yet.

---

### Post by siya_kh1983 on 2007-04-25
You can push the power btn on ur notebook or pc... the window that appear must have shutdown option.. if not re again...

---

### Post by Neo0351 on 2007-04-25
> **ronacc said:**
> this has been going on for awhile with feisty , various buttons dissapear form the actions menu then show up again , try running update manager to makesure you are uptodat , also in the top bar go to system>administration>login window>local and in the menu bar section make sure that show_action menu is checked. I don't know if there is a permenant fix for this yet.

thanks, i just started having the same problem this morning and this fixed it

---

### Post by glaeven on 2007-04-25
> **ronacc said:**
> this has been going on for awhile with feisty , various buttons dissapear form the actions menu then show up again , try running update manager to makesure you are uptodat , also in the top bar go to system>administration>login window>local and in the menu bar section make sure that show_action menu is checked. I don't know if there is a permenant fix for this yet.

i just got my wireless and and a panel update came. i'll see if that worked.

---

