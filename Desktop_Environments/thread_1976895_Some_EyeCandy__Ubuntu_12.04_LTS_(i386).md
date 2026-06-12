---
title: "Some EyeCandy | Ubuntu 12.04 LTS (i386)"
date: 2012-05-09
forum: Desktop Environments
---

### Post by debashishone on 2012-05-09
[GNOME Shell Weather Extension]("https://github.com/simon04/gnome-shell-extension-weather").  This extension displays the current temperature in the top GNOME Shell  panel and clicking it, you can see some more info such as the humidity,  pressure or wind as well as a forecast for tomorrow.

[CENTER] [[IMG]http://farm7.static.flickr.com/6048/6235044381_c6c90ff3ef_b.jpg[/IMG]]("http://farm7.static.flickr.com/6048/6235044381_c6c90ff3ef_b.jpg")[/CENTER]
 
GNOME Shell Weather extension comes with a GUI (disabled by default in  GIT until it can be automatically installed via makefile but I've  enabled it for those of you who will install it from the WebUpd8 GNOME 3  PPA) which lets you move the icon from the center of the top bar to the  right, switch between Celsius and Fahrenheit units, enable/disable  symbolic icons, text or comment on the panel and more.

**To Install Gnome Shell Weather Extension in Ubuntu Oneiric/Linux Mint  open Terminal and copy the following commands in the Terminal:**
[INDENT] > sudo add-apt-repository ppa:webupd8team/gnome3
sudo apt-get update
sudo apt-get install gnome-shell-extensions-weather
[/INDENT][B][U]How to configure GNOME Shell Weather Extension:
[/U]1.[/B] Various settings like the position on the panel can be changed from the  extension preferences, but this doesn't work for the location just yet,  so you must use dconf-editor. Install it using the command below:
[INDENT] > sudo apt-get install dconf-tools[/INDENT] [CENTER] [[IMG]http://farm7.static.flickr.com/6118/6235567932_2da0dcda73_b.jpg[/IMG]]("http://farm7.static.flickr.com/6118/6235567932_2da0dcda73_b.jpg")[/CENTER]
 
**2.** Then press ALT + F2 or open a terminal and enter:
[INDENT] > dconf-editor[/INDENT] And in dconf-editor, navigate to org > gnome > shell > extensions > weather and under "woeid",enter the Yahoo weather ID for your city (see below).

**3.** To get your Yahoo ID, go to [http://weather.yahoo.com/](http://weather.yahoo.com/),  enter your city/zip code and when you find it, look for the orange  "RSS" icon on the right. Hovering this icon, you'll see your code - this  is the WOEID.

[CENTER] [[IMG]http://3.bp.blogspot.com/-E-MfxO4X65k/Tt3MC8DqzwI/AAAAAAAAFDc/WpweV41Rhlk/s400/weather.png[/IMG]]("http://3.bp.blogspot.com/-E-MfxO4X65k/Tt3MC8DqzwI/AAAAAAAAFDc/WpweV41Rhlk/s1600/weather.png")[/CENTER]
 
**4.** And finally install GNOME Tweak Tool:
[INDENT] > sudo apt-get install gnome-tweak-tool[/INDENT] Then search for "Advanced Settings" (that's how GNOME Tweak Tool shows  up) in the Activities Overview and enable GNOME Shell Weather extension.

Oh, and if you change the location on the panel, you'll have to restart  GNOME Shell or log out and log back in. That's not required for the  other settings.

---

