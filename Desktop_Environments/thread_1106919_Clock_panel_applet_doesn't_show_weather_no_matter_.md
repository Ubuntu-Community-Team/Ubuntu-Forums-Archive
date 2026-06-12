---
title: "Clock panel applet doesn't show weather no matter what"
date: 2009-03-26
forum: Desktop Environments
---

### Post by mahy on 2009-03-26
Hello people,

I'm running Ubuntu 8.10 with Gnome. There's this "Clock" applet in the panel in the top right-hand corner, which is supposed to display current weather once I set up a location. But it simply doesn't. When I set up the location, by width of the panel increases by a few milimeters, but no other change occurs. The weather is only visible when I **click** the panel, and a calendar shows up. I tried some googling, e.g. [this workaround]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg854308.html") to match the timezones, but it didn't help. My timezones are correctly set up, yet the weather conditions don't show up on the clock panel.... Any ideas?? TIA

---

### Post by ooburns on 2009-03-26
I don't even know why the whether options are there; it's never worked for me either. :P

Luckily, there's a separate weather applet that works fine. If you go to "add to panel...", there's one called Weather Report.

---

### Post by Daddyo-613 on 2009-03-26
> **mahy said:**
> Hello people,

I'm running Ubuntu 8.10 with Gnome. There's this "Clock" applet in the panel in the top right-hand corner, which is supposed to display current weather once I set up a location. But it simply doesn't. When I set up the location, by width of the panel increases by a few milimeters, but no other change occurs. The weather is only visible when I **click** the panel, and a calendar shows up. I tried some googling, e.g. [this workaround]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg854308.html") to match the timezones, but it didn't help. My timezones are correctly set up, yet the weather conditions don't show up on the clock panel.... Any ideas?? TIA

The problem may be with the graphics driver and not the applet. 8.10 bundles ver. 177 of the nVidia driver. The threads suggest that once again there are problems with nVidia. I have a Geforce 7300 LE card and when I upgraded to 8.10 the title bars on my active window went blank. You might want to try changing your desktop theme. Some are more graphics intensive than others. System>Preferences>Appearance then select and try various themes. I changed from <Human> to <Glossy> and it worked for me.

I also entered the location information in the clock and the weather information  properly displays. Good luck!
B'H

---

### Post by mcduck on 2009-03-27
> **mahy said:**
> Hello people,

I'm running Ubuntu 8.10 with Gnome. There's this "Clock" applet in the panel in the top right-hand corner, which is supposed to display current weather once I set up a location. But it simply doesn't. When I set up the location, by width of the panel increases by a few milimeters, but no other change occurs. The weather is only visible when I **click** the panel, and a calendar shows up. I tried some googling, e.g. [this workaround]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg854308.html") to match the timezones, but it didn't help. My timezones are correctly set up, yet the weather conditions don't show up on the clock panel.... Any ideas?? TIA

Exactly how are you setting up the location?

The way to do it (to get weather data) is to start typing in the "Location Name"-field and then pick the closest location it suggests. (the suggested locations are the ones that have weather data, most of the times they are airports and such).

Just setting correct time zone won't work for weather data.

Also, when you click the applet to view the calendar & locations, do you have a home icon next to your location? If not, click the "Set" button that appears when you hover your mouse over the location. This is how you select which location's time & weather data the applet shows in the panel if you have multiple locations configured.

If you have done all these correctly and the weather data still doesn't show, it's most likely a problem with your current theme.

---

### Post by fabricates on 2009-04-22
Thank you so much! The 'set' advice worked perfectly :)

---

### Post by sridharpandu on 2009-11-24
Thank you mcduck. It works

---

### Post by kk_furtiva on 2010-01-04
The Set stuff works like a charm! Thx

---

### Post by Fancycakes on 2010-05-28
I didn't have a home icon, so I double clicked on the map and a dot where I was supposed to be started to blink - then the set button appeared. I clicked it and now I have weather! =D

> **mcduck said:**
> Exactly how are you setting up the location?

The way to do it (to get weather data) is to start typing in the "Location Name"-field and then pick the closest location it suggests. (the suggested locations are the ones that have weather data, most of the times they are airports and such).

Just setting correct time zone won't work for weather data.

Also, when you click the applet to view the calendar & locations, do you have a home icon next to your location? If not, click the "Set" button that appears when you hover your mouse over the location. This is how you select which location's time & weather data the applet shows in the panel if you have multiple locations configured.

If you have done all these correctly and the weather data still doesn't show, it's most likely a problem with your current theme.

---

