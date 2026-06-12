---
title: "screen resolution unchangeable with docking station"
date: 2005-11-07
forum: Desktop Environments
---

### Post by phen on 2005-11-07
hello all!

i am using an hp nc6120 laptop. its internal screen's maximum resolution is 1024x786. Now i connected the laptop to a docking station, closed the lid and connected a 19" lcd screen to the docking station. i am not able to change its resolution above 1024x786.

i tried to dpkg-reconfigure, i tried to change xorg.conf in several ways:

first, i added the mode to the display section:
SubSection "Display"
		Depth		24
		Modes		"1280x1024@75" "1024x768"
EndSubSection

second: i tried to add higher refresh rates to monitor section:
Section "Monitor"
        Identifier      "Monitor1"
        HorizSync       28-82
        VertRefresh     43-76
        Option          "DPMS"
EndSection

afterall, i tried to use a second screen definition and start Xorg with startx -- -screen Benq
it is still 1024x786, but the font is smaller now.

after hours of messing around with the config file, i attached it to this post.
i am getting lost with this topic... and any help is greatly appreciated, 

thank you all in advance!

phen

---

### Post by phen on 2005-11-08
update: i had to switch of the internal display (it wasn't switched off automatically) to get the desired resolution. but as a consequence, i was not able to use kde applications anymore. the DCOPserver saved its runtime date in a file called dcopserver_host_NODISPLAY instead of dcopserver_host_0. therefore, i am back on 1024x786. this is getting annoying!

---

### Post by phen on 2005-11-09
update: Now i am able to use my big lcd. I dont start any DM at startup, but boot into console. then i choose my display by using the laptops hotkeys. now i boot into X with resolution 1280x1024. however, if i've chosen the laptops internal display, X will fall back to 1024x786. 

Because the monitor i use for x is the one that started it, the dcopserver can find his files again.

I like that it recognizes it automatically. I don't like that it has to be so difficult to enable a second display with a different resolution. 

Finally, i dont mind to use the console, but there is one question left: is there a console command that i could use to enable my screen without opening my laptop and pressing the hotkey? because the point of my docking station is that my laptop is hidden underneath my desk to save as much space as possible. not it is standing opened on my desk, buttons ready to get pressed...

thanks for listening to my monologue :-)

---

