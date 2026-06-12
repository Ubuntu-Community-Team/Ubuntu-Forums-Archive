---
title: "Don't have a desktop anymore …"
date: 2011-05-02
forum: Desktop Environments
---

### Post by cousteau on 2011-05-02
Dear friends,

I guess I messed around with Unity on Ubuntu 11 a bit too much without knowing too much about it. ;)
Here's what's been happening: I chose the 'cube' setting in CCSM, but after switching to it, Unity crashed. So I rebooted and X11 started, but no Unity. Which means no window borders or anything.

Any idea how I could set it up again? I disabled the login-screen, as I'm the only user, so I guess I have no chance to simply choose Gnome for example to boot into a full-featured desktop.

Any ideas? Thanks so much.

tr

---

### Post by garvinrick4 on 2011-05-02
In Unity if you can get to a terminal ctrl/alt/t and then type in ccsm
should open and be able to check mark Ubuntu Unity plugin.

Did you disable login screen so this does not even work.
```
sudo gnome-session-save --kill
```
Usually opens login screen from terminal when in a bind.

---

### Post by cousteau on 2011-05-02
> **garvinrick4 said:**
> In Unity if you can get to a terminal ctrl/alt/t and then type in ccsm
should open and be able to check mark Ubuntu Unity plugin.

Hmmm. Problem is, Unity doesn't boot anymore. So I can't open a terminal from within Unity.

Thanks for trying to help.

---

### Post by garvinrick4 on 2011-05-02
The login screen when you click on your name at the bottom gives you a button to go back to
unity called ubuntu. If you completely disabled login screen can you not enable it in ubuntu classic the same place you disabled it?

---

### Post by cousteau on 2011-05-02
> **garvinrick4 said:**
> The login screen when you click on your name at the bottom gives you a button to go back to
unity called ubuntu. If you completely disabled login screen can you not enable it in ubuntu classic the same place you disabled it?

I did have the same idea. Is there a way to boot in Ubuntu Classic without having a login screen? Otherwise I have no idea to access the settings dialogue.

---

### Post by Krytarik on 2011-05-02
Create a launcher at your Unity desktop for the command "ccsm", launch it, make sure "Desktop Cube" and "Rotate Cube" are enabled, then re-enable the "Ubuntu Unity Plugin" and the "Window Decoration" plugin, and probably more.

Greetings.

---

### Post by cousteau on 2011-05-02
> **Krytarik said:**
> Create a launcher at your Unity desktop for the command "ccsm", launch it, make sure "Desktop Cube" and "Rotate Cube" are enabled, then re-enable the "Ubuntu Unity Plugin" and the "Window Decoration" plugin, and probably more.

This solved the problem. Thanks. :D

---

