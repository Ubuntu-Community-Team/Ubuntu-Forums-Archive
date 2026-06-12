---
title: "monitor auto turn off"
date: 2006-09-26
forum: Desktop Environments
---

### Post by Green_Star on 2006-09-26
It is really annoying me, my monitor automatically turns off after 15mins of idle system. once i move my mouse or press any key on my keyboard again my screens comes up. i want to turn this feature off, how can i do that? I tried all places but i didnt find that option.

thanks in advance.

---

### Post by Kateikyoushi on 2006-09-26
You can change it in power management.
System >> Preferences >> Power Management.

Then change put display to sleep.

---

### Post by Green_Star on 2006-09-26
I tried that already, that was set to an hour, but still it is going off after 15mins or some thing near to that time. Any way thanks for your help.

---

### Post by orb9220 on 2006-09-26
Ok this is how I fixed mine from other posts I read:
In a term type xset -q to see settings for x
xset -dpms will turn off dpms

Now go to screensaver and set for 1 min then go to monitor and set for 2 mins.

Wait for screensaver to kick in move mouse then go ahead and disable screensaver. Then wait for monitor to kick out at 2 mins then move mouse and change to never.

Now in sessions make sure you have save sessions on exit checked. And reboot.

Wierd I know but worked for me. Now my monitors are always on.
Also check your bios settings which can overide your gnome settings.

Hope this helps.

---

### Post by pistcivet on 2006-09-26
Here's how I fixed that problem.
Add this section to /etc/X11/xorg.conf
```
Section	"ServerFlags"
	Option "blank time" "0"
	Option "standby time" "0"
	Option "suspend time" "0"
	Option "off time" "0"
EndSection
```
Restart the X-server for changes to take effect.
Saw this tip on these very forums.

---

### Post by Green_Star on 2006-09-27
**pistcivet**,
Your suggession worked.. thanks for your help.

---

