---
title: "GNOME desktop problem"
date: 2005-01-19
forum: Desktop Environments
---

### Post by Error1312 on 2005-01-19
Hi all.

I'm having quite a serious GNOME issue. Yesterday, for some unknown reason nautilus crashed and with it GNOME.
So I reboot my comp, go back to GNOME, but the desktop itself (the place where you put the icons and where you set your wallpaper) doesn't react in any way. The color is brown and even if I right-click on it, nothing happens. I can't set a wallpaper, not even with the tools in the GNOME menu. 
Also, the transparency, which I set in the upper bar is gone. The icons in the bar itself are still there. Now, reconfiguring all my changes and wallpapers is no problem in itself, the problem is I simply can't do this because the desktop itself doesn't function anymore.

So basically, most of my settings and changes are simply gone (except for the log in -and splash screen) and the desktop itself seems totally broken.

I tried apt-get install gnome to reïnstall GNOME, but this didn't work either.

Is there someone who can help me?

---

### Post by ralph_ubuntu on 2005-01-19
Sounds like nautilus isn't starting, as nautilus is responsible for drawing the desktop.
You could as a first step try to simply fire up a terminal and start nautilus from there. If nautilus starts your problem should be solved, if it doesn't maybe you at least get some kind of error message.

Good luck!

---

### Post by Error1312 on 2005-01-19
Thx, ralph_ubuntu.

Your solution partly worked. I can start nautilus from a terminal as root, and then the desktop functions again. But whenever I close it, it's the same as before. And I can only run it as root. As a normal user, nothing happens when I enter the command.

Maybe nautilus is broken at a particular user level. I have no idea.
I tried reïnstalling it, but this has no effect.

---

### Post by ralph_ubuntu on 2005-01-19
My guess would be that some nautilus config file got borked when it crashed, removing this file should probably solve the problem, the problem is that I have no idea what config file could be the problem.

You could try to move the gnome config files out of the way one by one and see if that helps, for example mv .gconf2 .gconf2_bak.

Also, did you already try to start gnome in failsafe mode? In my experience this sometimes helps to solve these kind of problems.
And you should probably also take a look around the forum as I'm sure there are a lot of threads dealing with this problem and maybe you'll find a solution there.

Good luck!

---

### Post by Error1312 on 2005-01-19
Thx ralph_ubuntu. It works!! :grin: 

I used Synaptic to reïnstall every gnome package that was selected, rebooted, and now it works. 

Only one small problem left though. In the previous sessions, I clicked on several icons (like Nautilus) trying to get them to work, which they didn't at that time. Now, when gnome starts up, it shows me all those windows. Approximately, 5 times nautilus, 3 times the Firefox profile editor (no idea why) and stuff like that.

I suppose there is a script or an option somewhere in which I can change this, but what script can that be (if it is a script)? I already disabled 'automatically save session', but this doesn't change anything.

---

### Post by ralph_ubuntu on 2005-01-19
Reenable "automatically save session", close all the annyoing apps and log out of gnome.

---

### Post by Error1312 on 2005-01-19
Thx, I'll try it out, but first I'm gonna enjoy a working GNOME again.

---

### Post by Buffalo Soldier on 2005-01-19
[QUOTE=Error1312]I suppose there is a script or an option somewhere in which I can change this, but what script can that be (if it is a script)? I already disabled 'automatically save session', but this doesn't change anything.[/QUOTE]

First, close all applications.

Then click "Computer" at the top taskbar  -> click "Log Out" -> mark the checkbox "Save current setup" -> choose "Log out" -> click "OK"

After that login back into your desktop. You should have a nice clean desktop without any applications window running.

But before you logout / shutdown / reboot the next time, un-mark the checkbox "Save current setup".

---

### Post by Error1312 on 2005-01-19
Thx guys. It all runs smooth now. :)

---

