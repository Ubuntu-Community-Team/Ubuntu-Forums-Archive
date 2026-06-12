---
title: "Startup script Detos Dell"
date: 2012-03-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kevinpower on 2012-03-01
Hallo,
 
[COLOR=#c98f33][COLOR=black][FONT=Courier New]xrandr | grep maximum[/FONT][/COLOR]
[COLOR=black][FONT=Courier New]gtf 1440 900 59.9[/FONT][/COLOR]
[COLOR=black][FONT=Courier New]xrandr --newmode "1440x900_59.90" 106.29 1440 1520 1672 1904 900 901 904 932 -HSync +Vsync[/FONT][/COLOR]
[COLOR=black][FONT=Courier New]xrandr --addmode VGA 1440x900_59.90[/FONT][/COLOR]
[COLOR=black][FONT=Courier New]xrandr --output VGA --mode 1440x900_59.90[/FONT][/COLOR]
 
 
[COLOR=black]If i want to use this screen resolution everyting works, but i want that these commands starts automatically when the system is running. These commands have we accommodated as Display.sh. [/COLOR]
[COLOR=black]if i use this command to /etc/init.d/display.sh it doesn't work.[/COLOR]

[/COLOR][COLOR=black]if we starts manually the display.sh script it works and the system changed the screen resolution in 1440x900[/COLOR]

[COLOR=black]Does anyone have any ideas?[/COLOR]
 
 
Thanks!

---

