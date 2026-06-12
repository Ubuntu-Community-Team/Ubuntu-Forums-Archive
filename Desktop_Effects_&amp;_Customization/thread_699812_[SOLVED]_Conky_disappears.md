---
title: "[SOLVED] Conky disappears"
date: 2008-02-17
forum: Desktop Effects &amp; Customization
---

### Post by Bruce M. on 2008-02-17
Conky was running beautifully in Feisty, when I did a clean install of Gutsy it will not start ... or starts and disappears.  :(

Sessions

 Conky **<-- checked** - Command: /home/bruloo/.startconky
 Conkyw5 **<-- checked** - Command: /home/bruloo/.startconkyw5
 Network Manager **<-- NOT checked**
 Power Manager **<-- checked**
 Restricted Drivers Manager **<-- checked**
 Tracker **<-- checked**
 Update Notifier **<-- checked**
 User folders update **<-- NOT checked**
 Visual **<-- checked** **[COLOR="Red"]?*¿[/COLOR]** See below
 Volumn Manager **<-- checked**


**[COLOR="Red"]?*¿[/COLOR]** Visual <-- checked --> Autostart the preferred AT <--> What is this?


 At startup I get:

[LIST=1]
[*]The login screen: Name & Password
[*] Hit Enter
[*] A pause
[*] Screen goes black for 2 seconds
[*] Pause
[*] Screen comes back with black square upper left and right (Conkys)
[*] Bottom panel appears
[*] Top panel appears
[*] Icons appear on panels
[*] Conky Upper-Left appears
[*] Conky Upper-Right NEVER appears.
[*] Do anything an the conky on the Upper-Left disappears
[*] Click on Shutdowm Icon; then Restart
[*] Both Conkys reappear before system shutdown.
[*] Process starts all over again.
[/LIST]

Conky starts fine when I:

```

bruloo@The-Team:~$ ./.startconky
bruloo@The-Team:~$ Conky: /home/bruloo/.conkyscripts/conkymain: 31: no such configuration: 'shadecolor'
Conky: forked to background, pid is 6920

Conky: desktop window (12000ae) is subwindow of root window (45)
Conky: window type - override
Conky: drawing to created window (2e00001)
Conky: drawing to double buffer

```

And further more, it stays in place!

Any help appreciated.
Bruce

---

### Post by FuturePilot on 2008-02-17
See if this helps
[http://ubuntuforums.org/showpost.php?p=4320781&postcount=2]("http://ubuntuforums.org/showpost.php?p=4320781&postcount=2")

---

### Post by 1337455 10534 on 2008-02-17
OK, if your .conkyrc is in /home/usr/, then write a script;
#!/bin/bash
sleep 19 &&
conky &&
exit
and go to System->Prefs->Startup and add your script to startup. (chmod +x yourscript.sh first).
Along with this (or without, your choice), try adding one of these options to your conkyrc
background no
use_xft yes
xftfont Calibri:size=8
xftalpha 0.8
update_interval 1
own_window yes
own_window_type override
own_window_transparent yes
# commented out ,skip_taskbar, skip_pager, sticky
own_window_hints undecorated,below,skip_taskbar
double_buffer yes
draw_shades yes
draw_outline no
stippled_borders no
border_margin 0
border_width 1
default_color black
default_shade_color black
alignment top_middle
minimum_size 1260
gap_x 0
gap_y 30
use_spacer yes
no_buffers yes

Kill (killall -9 conky) and restart conky every time you change an option.

---

