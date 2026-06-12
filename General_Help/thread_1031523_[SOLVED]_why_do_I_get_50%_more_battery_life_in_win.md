---
title: "[SOLVED] why do I get 50% more battery life in windows?"
date: 2009-01-05
forum: General Help
---

### Post by vav on 2009-01-05
I have a Dell Inspiron 9300 with ATI graphics. I run Ibex with Compiz Fusion.
I got a new battery for it since I recently have need to use my computer uncorded. 
Battery life in Ubuntu is 2 hrs 30 mins. 
Battery life in WinXP is 3 hrs 40 mins. 
This is a HUGE difference! I use Ubuntu as my primary OS, so this is really hurting. What is the problem? no power management for the GPU? no sleep cycles for the CPU? I would love to remedy this in a way that would be persistent with future updates of the kernel etc. I'm disinclined to believe that it's compiz-fusion, since this problem has been there before compiz came to ubuntu, and with my older crappy battery too. I've run ubuntu for the last 3 years on it and will continue to do so. I would like to do it with pride though.

---

### Post by amauk on 2009-01-05
are these actual times before the battery runs out?
(or just what the OS reports as the "battery life")

---

### Post by vav on 2009-01-05
This is a very valid question and I agree with the premise. The estimated time shown especially in winxp is so ephemeral it's just garbage. 
My battery HAS run out in approx 2 and half hours in ubuntu. to the point where the computer's light flashes (I believe this is not under OS control). 
In winxp, what I do believe in is the percentage battery charge shown (I'm at 66% after an hour and half) since this is just info read from the battery and not an estimate made by winblows. I haven't had my battery run out in win yet (and it would be awesome to have the same happen in ubuntu)

---

### Post by vav on 2009-01-05
This is a very valid question and I agree with the premise. The estimated time shown especially in winxp is so ephemeral it's just garbage. 
My battery HAS run out in approx 2 and half hours in ubuntu. to the point where the computer's light flashes (I believe this is not under OS control). 
In winxp, what I do believe in is the percentage battery charge shown (I'm at 66% after an hour and half) since this is just info read from the battery and not an estimate made by winblows. I haven't had my battery run out in win yet (and it would be awesome to have the same happen in ubuntu)

---

### Post by amauk on 2009-01-05
you could try installing powertop
[http://www.lesswatts.org/projects/powertop/](http://www.lesswatts.org/projects/powertop/)

---

### Post by lswb on 2009-01-05
Besides a possible difference in estimated battery life as Amauk suggests there a few things you can do to increase battery time in ubuntu.

1) In power management reduce display backlight time and inactive time before sleep to low settings.

2) Edit your screensaver and power management settings so that screensavers do not run when on battery power, or perhaps run for only a minute or so. Some of them are surprisingly CPU intensive. 

3) As root edit the file /etc/default/acpi-support and change the line
ENABLE_LAPTOP_MODE=false to ENABLE_LAPTOP_MODE=true. As the comments suggest, if you experience hangs/freezes/similar problems after this you may need to change it back to false.

4) Depending on your work habits and typical usage, you may want to reduce the hd spindown time below default in the same file.

BTW, in my experience, the linux power managers will not give an accurate estimate of remaining battery time until they have seen the system go from a fully charged to fully discharged battery in a single session.

---

### Post by vav on 2009-01-07
This is certainly a combination of problems. even after a couple complete discharges, I haven't gotten ubuntu to predict battery life well. At any rate, my primary intent is to increase battery life, so I've tried the above fixes (laptop mode enabled, powertop downloaded and it's recommendations followed to some extent) but in addition lookie what I found for ati cards with the fglrx driver :)

sudo aticonfig --list-powerstates
sudo aticonfig --set-powerstate=NUMBER

Even in a 'low' powerstate, compiz works decently thought a little jerkily. Its hard to say for sure, but it seems like my avg power consumption in the lowest powerstate goes to about 18W from the highest 23W :D 20% more batt life with gpu powersaving :)

---

### Post by vav on 2009-01-10
So with enabling laptop_mode and the ati power saving, and sometimes using 
sudo iwpriv eth1 set_power 5

I'm at more than 3.5 hrs :guitar:

Not only that, after going through a complete discharge cycle in 1 session and complete charge cycle in another session, now ubuntu shows the battery estimated time quite accurately! :)

The synaptic driver is still causing unnecessary wakeups-from-idle on my cpu as shown by powertop :(

I also use the 'conservative' setting in my cpu frequency scaler. the default ondemand should work well too!

compiz still works decently well and I have my screen at full brightness :P on my 3 yr old laptop. kudos.

Peace on this count.

---

