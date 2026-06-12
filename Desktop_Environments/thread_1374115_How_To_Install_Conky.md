---
title: "How To Install Conky ?"
date: 2010-01-06
forum: Desktop Environments
---

### Post by //ro0t on 2010-01-06
Hello Guys ! :) I want to install conky , i need help :( i tryed many ways but they don`t work :(

---

### Post by oldos2er on 2010-01-06
```
sudo apt-get update && sudo apt-get install conky
```

If for some reason it doesn't work, please copy and paste the output here.

---

### Post by //ro0t on 2010-01-06
> **oldos2er said:**
> ```
sudo apt-get update && sudo apt-get install conky
```

If for some reason it doesn't work, please copy and paste the output here.

[B]Reading package lists... Done
Building dependency tree       
Reading state information... Done
conky is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[/B]

how i can turn-on it  ?

---

### Post by footloose143 on 2010-01-06
Sounds like you already have it installed, just try running "conky" it from your terminal

---

### Post by //ro0t on 2010-01-06
> **footloose143 said:**
> Sounds like you already have it installed, just try running "conky" it from your terminal

when i write **conky** there is this : 

[COLOR="Red"]Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
Conky: forked to background, pid is 13131
grozn1@grozn1-desktop:~$ 
Conky: desktop window (20000af) is subwindow of root window (13c)
Conky: window type - override
Conky: drawing to created window (0x6200001)
Conky: drawing to double buffer
Conky: can't open /sys/class/power_supply/BAT0/uevent: No such file or directory
Conky: can't open /proc/acpi/battery/BAT0/state: No such file or directory
Conky: can't open /proc/apm: No such file or directory[/COLOR]


i tryed and wrote this code **conky -a top_right** but it don`t work too. and there was this error too. what can i do for solve this problem , i like it and i want to use :(

---

### Post by oldos2er on 2010-01-06
You might need to create .conkyrc. See [http://conky.sourceforge.net/docs.html](http://conky.sourceforge.net/docs.html) , scroll down to Configuration Settings.

---

### Post by footloose143 on 2010-01-06
> **//ro0t said:**
> when i write **conky** there is this : 

[COLOR="Red"]Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
Conky: forked to background, pid is 13131
grozn1@grozn1-desktop:~$ 
Conky: desktop window (20000af) is subwindow of root window (13c)
Conky: window type - override
Conky: drawing to created window (0x6200001)
Conky: drawing to double buffer
Conky: can't open /sys/class/power_supply/BAT0/uevent: No such file or directory
Conky: can't open /proc/acpi/battery/BAT0/state: No such file or directory
Conky: can't open /proc/apm: No such file or directory[/COLOR]


i tryed and wrote this code **conky -a top_right** but it don`t work too. and there was this error too. what can i do for solve this problem , i like it and i want to use :(


Looks like your default conky config file is messed up, try downloading any simple rc file and use 

conky -c "Filename" &

---

### Post by //ro0t on 2010-01-06
i can`t create folder or file in conky foder ! i`ve config  :S

---

### Post by oldos2er on 2010-01-06
.conkyrc should be in your home folder. **touch .conkyrc** run in a terminal will create the file, then use gedit or whatever your favorite text editor is to customize it. Suggestions here: [http://ubuntuforums.org/showthread.php?t=1358302](http://ubuntuforums.org/showthread.php?t=1358302)

---

### Post by //ro0t on 2010-01-07
thanks everyone for help :)

---

### Post by pratap13 on 2011-02-20
> **//ro0t said:**
> Hello Guys ! :) I want to install conky , i need help :( i tryed many ways but they don`t work :(
same prob here . . .plz help :(

---

### Post by faixan on 2011-12-11
> **pratap13 said:**
> same prob here . . .plz help :(

make that x2 :( :( :( i just installed conky, every thing was fine before i created the file .conkyrc in home folder, file is there, and apparently the config. i downloaded is also sort of working, the weather is being updated in the "weather" file placed in my home folder, but i see nothing on screen, and when i run conky from terminal this appears;


```

Conky: .conkyrc: 14: no such configuration: 'border_margin'
Conky: desktop window (16000b3) is subwindow of root window (ad)
Conky: window type - override
Conky: drawing to created window (0x5a00001)
Conky: drawing to double buffer
Conky: can't open /sys/class/power_supply/BAT0/uevent: No such file or directory


```

and it stops there till i press Ctrl+C and terminate it... :\
what should i do?

btw, i downloaded this config;

[http://www.quicktweaks.com/2008/09/27/gmail-weather-beauty-right-on-your-ubuntu-desktop/](http://www.quicktweaks.com/2008/09/27/gmail-weather-beauty-right-on-your-ubuntu-desktop/)

---

### Post by faixan on 2011-12-11
> **faixan said:**
> make that x2 :( :( :( i just installed conky, every thing was fine before i created the file .conkyrc in home folder, file is there, and apparently the config. i downloaded is also sort of working, the weather is being updated in the "weather" file placed in my home folder, but i see nothing on screen, and when i run conky from terminal this appears;


```

Conky: .conkyrc: 14: no such configuration: 'border_margin'
Conky: desktop window (16000b3) is subwindow of root window (ad)
Conky: window type - override
Conky: drawing to created window (0x5a00001)
Conky: drawing to double buffer
Conky: can't open /sys/class/power_supply/BAT0/uevent: No such file or directory


```

and it stops there till i press Ctrl+C and terminate it... :\
what should i do?

btw, i downloaded this config;

[http://www.quicktweaks.com/2008/09/27/gmail-weather-beauty-right-on-your-ubuntu-desktop/](http://www.quicktweaks.com/2008/09/27/gmail-weather-beauty-right-on-your-ubuntu-desktop/)


Got it working, still having issues, but atleast it's working now...

---

### Post by chowanec on 2011-12-11
I had the same problems under gnome3 -- generally that I would run conky and nothing would happen.  It would run in the background, but wouldn't draw anything.

I had to change the window settings from:

own_window_type override

to 

own_window_type desktop

And that worked fine for me.

---

### Post by faixan on 2011-12-11
> **chowanec said:**
> I had the same problems under gnome3 -- generally that I would run conky and nothing would happen.  It would run in the background, but wouldn't draw anything.

I had to change the window settings from:

own_window_type override

to 

own_window_type desktop

And that worked fine for me.

i've the default Gnome that comes with Maverick Meerkat, i'm having problem with ```
own_window_type override
``` that whenever i boot my computer, it stays always on top, doesn't effect the maximising of the windows i open but they go behind it, i changed it to desktop, it completely vanished... :s don't know what happen with that... now i've it on normal... don't know if it's working fine yet or not, just sharing an experience.

---

### Post by faixan on 2011-12-12
> **faixan said:**
> i've the default Gnome that comes with Maverick Meerkat, i'm having problem with ```
own_window_type override
``` that whenever i boot my computer, it stays always on top, doesn't effect the maximising of the windows i open but they go behind it, i changed it to desktop, it completely vanished... :s don't know what happen with that... now i've it on normal... don't know if it's working fine yet or not, just sharing an experience.

yea, just rebooted and re-configured it all, 
```
own_window_type override
``` doesn't work for me after a reboot, it just stays on top of every thing even keeps the desktop background behind it on top of every thing i open, untill i kill the process and restart conky.
i changed it to 
```
own_window_type desktop
```
after this just one click on the desktop blank area, and conky's gone... again need to restart conky to see it :(
but
```
own_window_type normal
```
is working fine for me now, even though the show desktop controls now work on it, which i don't really want to happen, but i can live with that considering all other options.

---

