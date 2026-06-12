---
title: "Open terminal at a certain position"
date: 2022-07-03
forum: Desktop Environments
---

### Post by mozdog04 on 2022-07-03
Is there a way to set the size and location of the terminal that opens when I log in? I've  currently got the terminal added to the  GUI start up list.

I would like to have it open at a certain position (and size) on the desktop when the system boots if this is possible.

Using Xfce

---

### Post by yetimon_64 on 2022-07-03
"devilspie2" is one program/application you should research as it may be useful for this. A description for it is in the next code box and is taken from the terminal command "apt-cache show devilspie2"...
```
Description-en: Lua-based window matching utility
 Devilspie2 is a window matching utility, allowing the user to perform
 scripted actions on windows as they are created. For example, you can
 script a terminal program to always be positioned at a specific screen
 position, or automatically position a window on a specific workspace...
```

Note: I am also on Xfce, specifically Xubuntu 22.04, and use devilpie2 quite extensively for controlling window positions and/or sizes. Once installed and set to run at each start-up a daemon monitors windows for matching to any rules you implement.

---

### Post by mozdog04 on 2022-07-04
Awesome, thanks

---

### Post by vanadium on 2022-07-04
+1 for devilspie2 as a general tool to control the size and position of windows, but in this case, you can just get away with the "--geometry" option of xfce4-terminal to control size and position of the launched instance.

---

### Post by TheFu on 2022-07-04
> **mozdog04 said:**
> Is there a way to set the size and location of the terminal that opens when I log in? I've  currently got the terminal added to the  GUI start up list.

I would like to have it open at a certain position (and size) on the desktop when the system boots if this is possible.

Using Xfce

I use an xterm and like all X/Windows client programs, it accepts geometry options. For example:
```
$ xterm -geometry 80x25+980-72 $XTERM_OPTS -e ssh -X romulus &
```

Many other programs that we don't normally consider as X/Clients also support specific size and placement parameters:
```
/usr/bin/firejail     --private     /usr/bin/chromium-browser \
   --window-position="97,0" \
   --window-size="1683,1153"

```
The manpage for each program _should_ clearly say all the parameters supported.  My understanding is that Xfce doesn't support Wayland, so all your GUI programs are X/clients by definition.

---

### Post by mozdog04 on 2022-07-05
This worked perfectly, Thank you

---

