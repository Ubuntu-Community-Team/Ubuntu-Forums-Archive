---
title: "Idle brightness brighter than current brightness!"
date: 2009-05-23
forum: General Help
---

### Post by Beacon11 on 2009-05-23
Hello all.

I'm not sure if this is a bug, or if I'm just missing something. I wasn't able to form a very fruitful Google search, so I decided to post here.

I'm running Ubuntu 9.04 netbook remix on my Asus eeepc 901. When I'm running on battery power, I have the power manager set to dim the display when idle. However, let's say I'm reading some web page in the dark. I usually turn my brightness down nearly all the way as it otherwise hurts my eyes. As I'm reading, I don't touch anything. After a few minutes, power manager deems my computer "idle" and the display brightens! To reiterate: If I have my current brightness lower than whatever is set for the "idle brightness," power manager actually makes my screen brighter to match the idle brightness. Shouldn't it check to see if I'm already dimmer than the idle brightness? Can I change this without delving into source? It's a pretty annoying issue, as I do this kind of thing quite often.

---

### Post by florus on 2009-05-23
How about adjusting your power settings so that the computer does not become idle until it has been inactive for an hour.

---

### Post by Beacon11 on 2009-05-24
Where is the option to change idle time? All I see is when to put computer and display to sleep. Beyond this, should I file this as a bug? Or is there a way to change this functionality? My point is this: I shouldn't have to change my idle time, as I WANT my display to dim when it's brighter than the idle brightness. I don't want to change it to an extended idle time every time I want to read something. It's not seriously supposed to work this way, is it?

---

### Post by Beacon11 on 2009-06-16
Anyone got any ideas?

---

### Post by my_key on 2009-12-09
Type alt + F2 to run a program (or use terminal) and run gconf-editor. Go to / > apps > gnome-power-manager > backlight and change the value of the keys (that are pretty self explanitory) to your liking.

The default values are:
brightness_ac 100
brightness_dim_battery 50
idle_brightness 30

If you would like a bit more time before the display starts dimming adjust the value of idle_dim_time to your liking. The default is 10 for 10 seconds, but I like it at 20.


Cheers 

Michael 'my_key' Cox

---

