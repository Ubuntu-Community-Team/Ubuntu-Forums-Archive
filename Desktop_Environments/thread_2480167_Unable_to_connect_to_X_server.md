---
title: "Unable to connect to X server"
date: 2022-10-21
forum: Desktop Environments
---

### Post by hakelm on 2022-10-21
I am running this little script at reboot;

```
#!/bin/bash
#/usr/bin/xinput set-button-map 9 1 2 3 4 5 6 7 8 9 10 11 12 
 /usr/bin/xinput set-button-map 9 1 2 3 4 5 6 7 0 0 10 11 12
#1=leftbtn, 2 middle, 3 right, 4 wheel forw, 5 wheel backw, 8 last wnd, 9 next wnd

```


But instead of the desired effect i.e. disabling two annoying mousebuttons, I get a dead.letter in my home directory stating:

"Unable to connect to X server"

so I have to start the script manually as a normal user when the X11 is up and running.
Thanks for any tip on how to solve this little problem.
H

---

### Post by TheFu on 2022-10-21
So ... the script you want to run requires an X/Session which cannot happen until a user logs in on the console.  Not at reboot.

X11 has a number of files that get run automatically at login.  Any of those can be used or you can just put the script into the autorun-at-login for your DE.  So, which DE are you using, if any?   I know that openbox, a WM, will look in the  ~/.config/openbox/autostart file to run at GUI session startup.

BTW, if you are using Wayland, not X11, as the display server, it won't work.  X11 has different methods than Wayland.

---

### Post by hakelm on 2022-10-22
Thanks, clarified what I didn't grasp.
The easiest way to accomplish this seems to be putting a link to the script in Startup Applications.
H

---

