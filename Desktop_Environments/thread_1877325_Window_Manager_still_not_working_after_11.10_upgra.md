---
title: "Window Manager still not working after 11.10 upgrade"
date: 2011-11-07
forum: Desktop Environments
---

### Post by BloodyIron on 2011-11-07
I've had an issue now where my XFCE environment will not load the windows properly (like the close button for example). I tried to deal with this when it was 11.04, and people said it was fixed in 11.10, so I just put up with it.

Well I'm on 11.10 now, and I don't like the new UI so I went back to XFCE and it's still ******. It's at the point where it's preventing me from actually closing applications.

Last time I tried getting compiz, or another compositing setup to work it wouldn't stick after reboot, and with the upgrade I'm not sure on the proper way to do this lately.

Any ideas?

---

### Post by drawkcab on 2011-11-07
I guess I don't really understand what the problem is exactly.  If you upgraded to 11.10 you might have carried problematic settings through the upgrade.  I would try installing xubuntu from scratch and then finding a reliable howto to help you enable compiz.

---

### Post by BloodyIron on 2011-11-11
Bump

---

### Post by jerrrys on 2011-11-11
Since you now have 11.10 installed, you could install gnome-session-fallback and give it a try.  its like gnome2

---

### Post by rburkartjo on 2011-11-13
bloody i too have the same problem. this is a work around after you log in run the compiz fusion icon. and then reload windows manager it works for me. select window manager of your choice under the options first. be nice to find a fix that will auto load the windows manager without doing this

---

### Post by BloodyIron on 2011-11-13
> **rburkartjo said:**
> bloody i too have the same problem. this is a work around after you log in run the compiz fusion icon. and then reload windows manager it works for me. select window manager of your choice under the options first. be nice to find a fix that will auto load the windows manager without doing this


This is an acceptable work around, hopefully a permanent fix can be found soon.

One thing though, VNC works way worse with a proper compiz window manager now, any idea how I can improve this?

---

### Post by BloodyIron on 2011-11-18
Bump?

---

### Post by BloodyIron on 2011-11-22
This is still a problem, has anyone found a solution?

---

### Post by BloodyIron on 2011-11-30
Okay so here is a work around that has worked for me. I'm not pleased I have to do this, but it isn't that dirty


[LIST=1]
[*]Install fusion icon with your lovely package manager ( System > Synaptic Package Manager) "fusion-icon" is the exact package
[*]Open your session settings ( Settings > Session and Start up, this is for 11.10 remember)
[*]Go to the Application Autostart tab
[*]Click add, put whatever name you want and description you want, put this into the command: ```
fusion-icon -f
```
[/LIST]
This will force compiz to initialize no matter what (so fusion-icon tells me). Currently it seems to do the trick, and you get the icon in your system tray to deal with any more issues.


Thanks for the help folks!!! :guitar:

---

