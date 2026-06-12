---
title: "Resolution stuck at 656x512"
date: 2015-12-27
forum: Desktop Environments
---

### Post by Michael_Spohr on 2015-12-27
I just got xubuntu booted up on my Raspberry Pi using a youtube tutorial ([https://www.youtube.com/watch?v=UGSQ7nzVCs4](https://www.youtube.com/watch?v=UGSQ7nzVCs4)), and when I go to change my display settings the drop down menus only have the default settings available. I tried to change it through terminal with xrandr with an internet guide ([http://ubuntuforums.org/showthread.php?p=8595940](http://ubuntuforums.org/showthread.php?p=8595940)), and It gives me the error "Failed to get size of gamma for output default" when I enter xrandr into the terminal, and if I continue through the steps of the guide I get to step 3 and when I make the modeline it gives me the same error. After that none of the following steps work. Is there any other way to set resolution, or somehow get around the error "Failed to get size of gamma for output default"?

UPDATE: It seems that I didn't setup my Pi quite right, and I'm going to format and start fresh

---

### Post by matt_symes on 2015-12-27
Hi

Welcome to the forums.

Try forcing the gamma on the output line. Add this to it.

```
--gamma 1:1:1
``` 

BTW: If you want the most useful help then post the actual commands you have run. 

It's better than a web site link as we'll know exactly what you have tried and the failing step.

Kind regards

---

### Post by Michael_Spohr on 2015-12-27
Sorry for not putting code into the original post, so here ya go: 

```
ubuntu@ubuntu:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 720 x 576, current 720 x 576, maximum 720 x 576
default connected 720x576+0+0 0mm x 0mm
   720x576         0.0* 
ubuntu@ubuntu:~$ cvt 1024 600
# 1024x600 59.85 Hz (CVT) hsync: 37.35 kHz; pclk: 49.00 MHz
Modeline "1024x600_60.00"   49.00  1024 1072 1168 1312  600 603 613 624 -hsync +vsync
ubuntu@ubuntu:~$ xrandr --newmode "1024x600_60.00"   49.00  1024 1072 1168 1312  600 603 613 624 -hsync +vsync
xrandr: Failed to get size of gamma for output default
ubuntu@ubuntu:~$ xrandr --addmode default 1024x600_60.00
xrandr: Failed to get size of gamma for output default
ubuntu@ubuntu:~$ xrandr --output default --mode 1024x600_60.00
xrandr: Failed to get size of gamma for output default
xrandr: Configure crtc 0 failed
ubuntu@ubuntu:~$ sudo gedit /etc/gdm/Init/Default
[sudo] password for ubuntu: 
sudo: gedit: command not found
ubuntu@ubuntu:~$ 
```

After I posted this I realized that the gamma errors weren't stopping me from continuing through the steps, but I couldn't permanently save my changes because it didn't recognize the last bit. I ended up not needing the --gamma thing (at lease i don't think so), but I'm not really sure how to get the last step to work. Am I missing any packages, or is it some mistake I made in the previous steps?

---

### Post by matt_symes on 2015-12-28
Hi

I'm confused. Were you able to change the resolution ?

Anyway, the last command failed because Ubuntu no longer uses GDM. It now uses LightDM so you need to make your changes in its configuration file.

Kind regards

---

### Post by Michael_Spohr on 2015-12-28
Its kinda acting a little weird, after I enter "[COLOR=#000000][FONT=Ubuntu Mono]xrandr --output default --mode 1024x600_60.00" [/FONT][/COLOR]the screen flickers and stays the same resolution outputting the errors "Failed to get size of gamma for output default" and "Configure crtc 0 failed" as seen in the code above. When I go to display settings the drop down has a new option "1024x600", but when I apply it doesn't actually change the resolution. because I don't want to mess anything up, I'm not going to try the last step again until I can get it to work temporarily.

Also Sorry if I'm a little slow to respond, I'm trying to fix a couple problems at the same time & Its getting a little late

---

### Post by flocculant on 2015-12-28
> **matt_symes said:**
> ...
Anyway, the last command failed because Ubuntu no longer uses GDM. It now uses LightDM so you need to make your changes in its configuration file.

Kind regards

well :)

Xubuntu doesn't use gedit - uses mousepad - so that's the reason that the command failed, however lightdm is the right choice :)

---

### Post by matt_symes on 2015-12-28
Hi

> **flocculant said:**
> well :)

Xubuntu doesn't use gedit - uses mousepad - so that's the reason that the command failed, however lightdm is the right choice :)

lol. There's that as well. That'll teach me for answering questions at 4am.

@OP

Have you tried this as your last command in the steps of commands you listed above ?

```
xrandr --output default --gamma 1:1:1 --mode 1024x600_60.00
```

You can't break the system as it's nothing a reboot cannot fix.

Also, as flocculant pointed out, Xubuntu uses mousepad and not gedit. I really should know this as I've used Xubuntu for a number of years now :) 

Anyway if the above command does work then i would recommend creating a custom xorg.conf file instead of editing any of lightDM's configuration files.

Does the above command work after you have created the new mode and added it to the *default* output ?

Kind regards

---

