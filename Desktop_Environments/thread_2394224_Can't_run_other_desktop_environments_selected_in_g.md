---
title: "Can't run other desktop environments selected in gdm3 - always runs gnome3"
date: 2018-06-14
forum: Desktop Environments
---

### Post by dbsoundman on 2018-06-14
Hi all, let me try to explain this problem a bit...

So I wanted to try some alternative desktop environments (display managers?) in my Ubuntu 18.04 machine here, so I installed i3 and openbox. After a reboot, I could click the gear icon in the gdm3 logon screen and select these environments, but once I'm logged in, the environment always looks like the same gnome3: icons on the left-hand side in a vertical bar, same look and feel as gnome3. I would definitely think that at least i3 would have shown a noticeable change, but even when I select openbox, it looks almost exactly the same as when I select i3 or "Ubuntu", which is the default.

I know that I have some existing graphics driver issues (occasionally I have to try multiple times to log in via gdm3 by hitting Ctrl-Alt-F4 and Ctrl-Alt-F1 because I get stuck in a blank purple screen), but I always manage to get logged in eventually. Could this be related or am I doing something else wrong?

Thanks,

---

### Post by cruzer001 on 2018-06-14
If you will post the install commands that you used (i3 and openbox), I will give it a run and post my results.

---

### Post by ajgreeny on 2018-06-14
The two packages you installed are window-managers, not alternative desktop environments and I suspect that they are just replacing whatever is the usual WM of the new gnome desktop of Ubuntu, but still leaving you with the same gnome desktop running on top of new WM.

I do not know enough about the basics of changing sessions or the defaults of logging in with gdm3, used by Ubuntu when running gnome so will have to leave this to others to assist further, but it may be something in the configuration of gdm3 that always takes you to the gnome desktop.

---

### Post by again? on 2018-06-15
GNOME Shell is tightly integrated with Mutter (window manager)... so in effect if you are seeing the 
gnome-shell interface you are not running an alternative window manager.
To check your current environment, run...
```
env
```

I installed openbox and i3 and both sessions load not showing the gnome-shell interface.
[LIST]
[*]i3 seems to funtion ok
[*]openbox has graphics issues
[/LIST]

If I install the **openbox-gnome-session** package and attempt to login to the GNOME/Openbox session
I get kicked back to the greeter

If I switch display managers (login screen) to lightdm, the openbox and i3 sessions both work
while the GNOME/Openbox session still kicks me back to the greeter.
To switch display managers...
```
sudo apt install --no-install-recommends lightdm lightdm-gtk-greeter lightdm-gtk-greeter-settings
```
If during install you do not get the dialog to choose a display manager, run
```
sudo dpkg-reconfigure gdm3
```
Select lightdm. 
Reboot and at the greeter select your session in the top panel.

---

