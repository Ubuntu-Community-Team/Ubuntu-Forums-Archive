---
title: "[SOLVED] how to stop the screen going to sleep"
date: 2009-01-02
forum: General Help
---

### Post by markp1989 on 2009-01-02
I am trying to set up a spare monitor 2 my server, to display news/weather info etc. 

currently running openbox, and working excellent. one complaint i have is that the screen keeps going to sleep if i dont move the mouse for a while, how do i stop this?

thanks markp1989

---

### Post by dcstar on 2009-01-02
> **markp1989 said:**
> I am trying to set up a spare monitor 2 my server, to display news/weather info etc. 

currently running openbox, and working excellent. one complaint i have is that the screen keeps going to sleep if i dont move the mouse for a while, how do i stop this?

thanks markp1989

Go into Preferences-Screen Saver.

---

### Post by markp1989 on 2009-01-02
> **dcstar said:**
> Go into Preferences-Screen Saver.

thanks ,but ,I have done a comand line install , then added openbox, so i dont have the screen saver stuff installed

---

### Post by kokkus on 2009-01-02
The screen goes to sleep because that "sleep" is a screensaver.

---

### Post by markp1989 on 2009-01-02
so your telling me i have to install the screen saver packages, to stop the screen going black when using OpenBox?

---

### Post by mc4man on 2009-01-02
Not familiar at all with your setup, you could run this and see what's available in 'apps'
```
gconf-editor
``` .
If that's a no go then on some set ups the display 'sleep' is controlled in the bios, maybe you can 'adjust' there.


If you do have a gconf and the display 'sleep' is being set off from the bios mode then you need to set in the screensaver section the 'idle delay' to a value less than the time the display is going to 'sleep' (5 is good). You then set in the power saving section 'sleep_computer_ac' to 0 (never

Power saving settings don't take effect till the computer is considered 'inactive', that's why the low value for 'idle delay'

This allows the power saving setting (never) to kick in before the display goes to sleep due to bios mode setting.

---

### Post by kerry_s on 2009-01-02
add this to your /etc/X11/xorg.conf

```

Section "ServerFlags"
        Option	"BlankTime"	"0"
        Option	"StandbyTime"	"0"
        Option	"SuspendTime"	"0"
        Option	"OffTime"	"0"
EndSection

```

---

### Post by markp1989 on 2009-01-02
> **kerry_s said:**
> add this to your /etc/X11/xorg.conf

```

Section "ServerFlags"
        Option	"BlankTime"	"0"
        Option	"StandbyTime"	"0"
        Option	"SuspendTime"	"0"
        Option	"OffTime"	"0"
EndSection

```


Thanks, that worked perfectly.

---

