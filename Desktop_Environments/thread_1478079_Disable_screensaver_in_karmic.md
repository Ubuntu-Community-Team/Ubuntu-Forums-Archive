---
title: "Disable screensaver in karmic?"
date: 2010-05-09
forum: Desktop Environments
---

### Post by djstava on 2010-05-09
[SIZE=1]I tried a lot of methods but cannot work.

Like:

1&#12289;
[/SIZE][FONT=SimSun][SIZE=1]gconftool-2  --set  /apps/gnome-[COLOR=black]screensaver[/COLOR]**/**idle_activation_enabled  --type&#65309;bool  false[/SIZE][/FONT]
[SIZE=1]gconftool-2 --set  /apps/gnome-power-manager/ac_sleep_display --type=int 0

2&#12289;
[/SIZE][FONT=SimSun][SIZE=1]Edit  /etc/X11/xorg.conf file using the following command[/SIZE][/FONT]
 [FONT=SimSun][SIZE=1]sudo vi  /etc/X11/xorg.conf[/SIZE][/FONT]
[FONT=SimSun][SIZE=1]
[/SIZE][/FONT]
[FONT=SimSun][SIZE=1]      Section "Monitor"[/SIZE][/FONT]
[FONT=SimSun][SIZE=1]                    Identifier     "Generic Monitor"[/SIZE][/FONT]
[FONT=SimSun][SIZE=1]                    Option        "DPMS"[/SIZE][/FONT]
[FONT=SimSun][SIZE=1]       EndSection[/SIZE][/FONT]
[FONT=SimSun][SIZE=1]
[/SIZE][/FONT]
 [FONT=SimSun][SIZE=1]and add  the following lines[/SIZE][/FONT]
[FONT=SimSun][SIZE=1]
[/SIZE][/FONT]
 [FONT=SimSun][SIZE=1]Section  “ServerFlags”[/SIZE][/FONT]
 [FONT=SimSun][SIZE=1]#other  options can go here[/SIZE][/FONT]
 [FONT=SimSun][SIZE=1]Option  “BlankTime” “0&#8243;[/SIZE][/FONT]
 [FONT=SimSun][SIZE=1]Option  “StandbyTime” “0&#8243;[/SIZE][/FONT]
 [FONT=SimSun][SIZE=1]Option  “SuspendTime” “0&#8243;[/SIZE][/FONT]
 [FONT=SimSun][SIZE=1]Option  “OffTime” “0&#8243;[/SIZE][/FONT]
 [FONT=SimSun][SIZE=1]EndSection[/SIZE][/FONT]
 [FONT=SimSun][SIZE=1]Save and  exit the file[/SIZE][/FONT]

Any other useful method?
Thank you in advance.

---

### Post by drreed on 2010-05-09
> **djstava said:**
> [SIZE=1]I tried a lot of methods but cannot work.

Like:

1&#12289;
[/SIZE][FONT=SimSun][SIZE=1]gconftool-2  --set  /apps/gnome-[COLOR=black]screensaver[/COLOR]**/**idle_activation_enabled  --type&#65309;bool  false[/SIZE][/FONT]
[SIZE=1]gconftool-2 --set  /apps/gnome-power-manager/ac_sleep_display --type=int 0

2&#12289;
[/SIZE][FONT=SimSun][SIZE=1]Edit  /etc/X11/xorg.conf file using the following command[/SIZE][/FONT]
 [FONT=SimSun][SIZE=1]sudo vi  /etc/X11/xorg.conf[/SIZE][/FONT]
[FONT=SimSun][SIZE=1]
[/SIZE][/FONT]
[FONT=SimSun][SIZE=1]      Section "Monitor"[/SIZE][/FONT]
[FONT=SimSun][SIZE=1]                    Identifier     "Generic Monitor"[/SIZE][/FONT]
[FONT=SimSun][SIZE=1]                    Option        "DPMS"[/SIZE][/FONT]
[FONT=SimSun][SIZE=1]       EndSection[/SIZE][/FONT]
[FONT=SimSun][SIZE=1]
[/SIZE][/FONT]
 [FONT=SimSun][SIZE=1]and add  the following lines[/SIZE][/FONT]
[FONT=SimSun][SIZE=1]
[/SIZE][/FONT]
 [FONT=SimSun][SIZE=1]Section  “ServerFlags”[/SIZE][/FONT]
 [FONT=SimSun][SIZE=1]#other  options can go here[/SIZE][/FONT]
 [FONT=SimSun][SIZE=1]Option  “BlankTime” “0&#8243;[/SIZE][/FONT]
 [FONT=SimSun][SIZE=1]Option  “StandbyTime” “0&#8243;[/SIZE][/FONT]
 [FONT=SimSun][SIZE=1]Option  “SuspendTime” “0&#8243;[/SIZE][/FONT]
 [FONT=SimSun][SIZE=1]Option  “OffTime” “0&#8243;[/SIZE][/FONT]
 [FONT=SimSun][SIZE=1]EndSection[/SIZE][/FONT]
 [FONT=SimSun][SIZE=1]Save and  exit the file[/SIZE][/FONT]

Any other useful method?
Thank you in advance.

I opened my gui <system><preferences> menu and made changes to screensaver, powermanagement, and compiz too. They all had some setting or other that was dimming my monitor and making me log back in every time I walked out of the room, fine for an office but not needed at home.

Something in Lucid causes my screen to dim like it's about to suspend or hibernate, and then it will either brighten when I click something, or go comepletely black, then brighten. Very annoying and weird.

I turned mine off using the preferences menu

---

