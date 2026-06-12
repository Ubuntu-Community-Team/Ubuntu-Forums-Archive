---
title: "Issue with starting Unity: No panel or WM"
date: 2014-10-09
forum: Desktop Environments
---

### Post by Q-collective on 2014-10-09
Hi all,

I'm running 14.04 and all of a sudden Unity is no longer  starting after a reboot. That is, I don't see the panel appearing and  the window manager doesn't start. What does start is the filemanager (I  see the folders and files on the desktop appearing and I can open the  folders).

I've isolated the issue towards a systemwide issue as I  created a test user (in the console tty, via the adduser command),  which has the exact same behaviour. So removing local files in my home  directory will not resolve the issue.

Some basic information about my system:
- It has 8GB RAM and a recent i7 CPU
- It has a GTX 770 graphics card, these are using the recent Nvidia drivers (version 340.46, released 30 September 2014).

Please request more info as needed.

---

### Post by grahammechanical on 2014-10-09
You can reset Compiz with this

```
dconf reset -f /org/compiz/
```

and restart Unity with this

```
setsid unity
```

Regards.

---

### Post by Q-collective on 2014-10-09
Thank you for your prompt reply.

Given that haven't used the *sudo* command, I presume you've intended me to run this as a user, resetting account-specific settings. As noted in the OP, the issue is systemwide though, so resetting account-specific settings is a fruitless endeavour.

I did run your suggested commands though, as I could open a terminal via the file manager. But running them both with or without sudo doesn't resolve the issue.

---

### Post by Q-collective on 2014-10-09
The issue is resolved: I reinstalled the Nvidia drivers, apparently there was an issue there, somewhere.

Note for others, facing perhaps similar issues: I did install the proprietary Nvidia drivers manually, I did *not* use any PPA or the packages in the system, due to their age.

---

### Post by grahammechanical on 2014-10-09
> [COLOR=#000000]But running them both with or without sudo doesn't resolve the issue.[/COLOR]

Then it is not a problem with Compiz, the compositor/window manager and it is not a problem with Unity. Process of elimination. What else is system wide? Not themes. Not wallpapers. The Nautilus file manager is integrated into the desktop. I was not aware that we could use Nautilus to open a terminal. Have you added some kind of extension or plugin?

Regards.

---

