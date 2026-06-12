---
title: "an applet to show weather in my panel"
date: 2006-01-01
forum: General Help
---

### Post by taseal on 2006-01-01
One thing I miss about gnome panel was that I had bunch of things on it....

for example, it told me the current speed CPU was running at, had 3 weather reports (istanbul, erzurum and boca raton) and had a Stock ticker... I dont have any of that with KDE... is there a way to add those to my top panel in kubuntu?

---

### Post by Omnios on 2006-01-01
think they have weather and a few CPU and ram ones in synaptic think it was under kde kicker. The weather app is ok but didn't care for the resources that much as I used a small kicker panel

---

### Post by M4VE on 2006-01-01
[QUOTE=taseal]One thing I miss about gnome panel was that I had bunch of things on it....

for example, it told me the current speed CPU was running at, had 3 weather reports (istanbul, erzurum and boca raton) and had a Stock ticker... I dont have any of that with KDE... is there a way to add those to my top panel in kubuntu?[/QUOTE]

maybe it's not the answer you were looking for, but why not add gdesklets to your desktop?  It'll tell you what you want to know, and it works well, I use it.  Anyway hope this helps.

---

### Post by Omnios on 2006-01-01
SuperKaramba is pretty good to as a dock app. Lots of usefull info with a small resource footprint.

[IMG]http://ubuntuforums.org/gallery/showimage.php?i=1066&c=3[/IMG]

[http://ubuntuforums.org/gallery/showimage.php?i=1066&c=3]("http://ubuntuforums.org/gallery/showimage.php?i=1066&c=3")

 This dock app used about 5 megs of ram and 2 or 3 cpu as well as I made it my self. Read the superkarambe scripting how to and looked over a few existing SUperKaramba apps.

---

### Post by mazelado on 2006-01-01
KDE has applets similar to gDesklets, but they go in the taskbar. To get the weather load the KWeather applet from the Konsole:

*sudo apt-get install kweather*

Then, right-click on the taskbar, select "Add Applet to Panel...", scroll down and select "Weather Report", then click the "Add to Panel" button. The weather applet should appear in the taskbar where you can right-click to move or configure it.

As far as a stock ticker, if you can find/make an RSS feed for your stocks, you could add the KNewsTicker applet to the panel the same way and then add your stock RSS feed. You may need to load another package if those aren't showing up:

*sudo apt-get install kicker-applets*

I don't know of any applets that show the CPU speed, but there are a few that will show CPU load, memory, etc. They're in the same place as the previous two that I mentioned.

---

### Post by taseal on 2006-01-02
[QUOTE=mazelado]KDE has applets similar to gDesklets, but they go in the taskbar. To get the weather load the KWeather applet from the Konsole: *sudo apt-get install kweather* Then, right-click on the taskbar, select "Add Applet to Panel...", scroll down and select "Weather Report", then click the "Add to Panel" button. The weather applet should appear in the taskbar where you can right-click to move or configure it. As far as a stock ticker, if you can find/make an RSS feed for your stocks, you could add the KNewsTicker applet to the panel the same way and then add your stock RSS feed. You may need to load another package if those aren't showing up: *sudo apt-get install kicker-applets* I don't know of any applets that show the CPU speed, but there are a few that will show CPU load, memory, etc. They're in the same place as the previous two that I mentioned.[/QUOTE] 

that weather applet is just what I need but it looks like you can only have 1 weather report up at a time =/ not to mention it doesnt include my city boca raton :( lol

---

### Post by taseal on 2006-01-02
I installed the ticker thing, but I cant find it :confused:

---

### Post by Omnios on 2006-01-02
Try your menu some of the dock apps start from the menu and run in the bar. YOu can also make it so they automaticly start on start up to run them in bar. That is one of the things I did not like about kde dock apps.

---

