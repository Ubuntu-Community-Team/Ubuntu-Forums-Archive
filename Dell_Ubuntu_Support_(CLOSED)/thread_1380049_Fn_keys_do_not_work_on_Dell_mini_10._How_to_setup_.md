---
title: "Fn keys do not work on Dell mini 10. How to setup them in 9.10?"
date: 2010-01-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Artif on 2010-01-13
Ubuntu Netbook Remix 9.10 Karmic was installed on Dell mini 10 laptop. Poulsbo drivers were added to system ( [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/) ). Then LXDE desktop was added by
```
 sudo apt-get install lxde
```When I'm choosing Gnome session at login, then some Fn keys works fine, some - not.
When I'm choosing LXDE session at loging - the same.

I want to use LXDE in the future. I want in any possible way to setup Fn key combinations (for example via Gnome session, command line, etc.).
How Fn key combinations could be tuned in Ubuntu 9.10? How can can be created actions for Fn key combinations? As now, in 9.10, HAL mustn't be used for subj, IMHO older "howtos" aren't applicable in the case.

The computer is Dell mini 10. I can create Bash scripts, there is no problem for me if an answer will be "write a script and place link to it inside some special conf file". At least I need to set up volume and brightness Fn controls. Ideal will be to get a way to set up any other actions.

Thank you for answers.

P.S.

[SIZE=1]What work while Gnome sesion:
F3 - battery information,
F7-F9 volume,
arrows as home, end, PgUp, PgDn,
F10 - print screen.

Didn't work while Gnome sesion:
F2 - wireless and F5,F6 - brightness.
 And there is short screen flicker when &quot;Fn+F1&quot;. It is display switch, [/SIZE][SIZE=1]main screen never &quot;go black&quot; after this. [/SIZE][SIZE=1]I have no device to check if it really switch HDMI output.

While LXDE session works only &quot;arrows&quot; and F3 battery status (gnome-power-manger was added to autostart list).
[/SIZE]

---

### Post by Artif on 2010-01-15
I tried Hotkeys/Troubleshooting from [https://wiki.ubuntu.com/Hotkeys/Troubleshooting](https://wiki.ubuntu.com/Hotkeys/Troubleshooting)
and while step 2 I got for brightness combinations
```
user@laptop:~$ killall gnome-settings-daemon gnome-power-manager
user@laptop:~$ xev | sed -n 's/^.*state \([0-9].*\), keycode *\([0-9]\+\) *\(.*\), .*$/keycode \2 = \3, state = \1/p'
keycode 232 = (keysym 0x1008ff03, XF86MonBrightnessDown), state = 0x0
keycode 232 = (keysym 0x1008ff03, XF86MonBrightnessDown), state = 0x0
keycode 233 = (keysym 0x1008ff02, XF86MonBrightnessUp), state = 0x0
keycode 233 = (keysym 0x1008ff02, XF86MonBrightnessUp), state = 0x0
^C
user@laptop:~$ 

```

---

