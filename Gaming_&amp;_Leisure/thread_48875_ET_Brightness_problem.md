---
title: "ET Brightness problem"
date: 2005-07-14
forum: Gaming &amp; Leisure
---

### Post by pt123 on 2005-07-14
I use nvidia setting program screen to brightren up my screen. But when I run ET it resets the brightness levels to default (dark), and even using the brightness setting on ET its too dark to play. 

On Windows the brightness settings were kept with nvidia. 

Is there a way I can edit the brigtness setting for the display in a text file maybe?

---

### Post by endy on 2005-07-14
In the console for ET try experimenting with thses commands:

```

r_gamma
r_intensity
r_mapoverbrightbits
r_overbirghtbits

```

But note that taking these values too high will cause punkbuster to kick you. My settings are as follows, stored in an autoexec.cfg file:

```

r_gamma "3" 
r_intensity "1.5"
r_mapoverbrightbits "3"
r_overbrightbits "1"

```
You may need to set:
```

r_ignorehwgamma "1"

```

---

### Post by pt123 on 2005-07-14
These seem to be the maximum settings allowed 
r_gamma "3" 
r_intensity "1"
r_mapoverbrightbits "2"
r_overbrightbits "1"

R-gamma 3 made it brighter bt still too dark to play. I wil stick to windows for games.

---

### Post by endy on 2005-07-14
Because you say for desktop use you need to use nvidia-settings to brighten it up enough to use, this makes me wonder if you have your monitor set up corectly. Are all games and your desktop on both windows and linux too dark unless you use nvidia-settings (or the windows equivalent)?

If this is the case I'd suggest you look into your monitor setup :???: Perhaps your monitor cable needs replacing, do you have another one to test with?

I just can't stand to see anyone reverting back to windows  :)

---

### Post by pt123 on 2005-07-15
Its an old computer but in windows I can use nvidia utility to brighten the screen up. When playing ET I can brighten it further in the nvidia utility. 

But on Ubuntu I can brighten the monitor by adding Gamma stting in x11.conf file. But when Et starts it reverts to the default gamma, and then adds its limited brightness/gamma settings on top.

---

### Post by endy on 2005-07-16
Ok I found a way to do this but I had to run ET on a new X display (which I do anyway), then I used the command 'xgamma' to set the gamma of that X display. This should hopefully work for you but it will take a bit of config to get going, anyway if you want to try follow this:

1. First to allow you to run a new X display you need to edit the '/etc/X11/Xwrapper.config' file:

```

sudo cp /etc/X11/Xwrapper.config /etc/X11/Xwrapper.config.custom
sudo md5sum /etc/X11/Xwrapper.config > /var/lib/xfree86/Xwrapper.config.md5sum
sudo dpkg-reconfigure xserver-common

```
Then  make sure you change the first option to "Anybody" then just hit enter twice.


2. To run ET on a new X display I made a shortcut:

```

echo "xinit /usr/local/games/enemy-territory/et $* -- :1" > ./x.et
chmod a+x ./x.et
sudo cp ./x.et /usr/local/bin

```


3. Run 'x.et' in a terminal, ET should run on a new xserver. To access you original X server (ie your desktop) you need to now press: 

```

CTRL + ALT + F7

```


4. Now we are back on our desktop open a ternimal and experiment with the xgamma command, but make sure you pass the '-display' parameter do it knows which X display to gamma correct, for example:

```

xgamma -display :1 -gamma 6.0

```


5. Now go back to ET by pressing:

```

CTRL +  ALT + F8

```


That's basically it, I hope it works for you and I didn't miss anything. Don't forget you can switch back and forth via the two X servers whenever you like, but don't forget to quit ET when you're done playing. Also it appears that this way of setting the gamma doesnt seem to register in ET so punkbuster shouldn't kick you for having a high gamma setting :)

---

### Post by pt123 on 2005-07-16
Hey thanks but I managed to get Et installed on a new comp which has a bright monitor.

---

### Post by endy on 2005-07-17
D'oh :)

Was fun to figure it out so I don't mind :)

---

