---
title: "UNR desktop interface on &quot;regular&quot; Ubuntu?"
date: 2010-04-08
forum: Desktop Environments
---

### Post by Rockyc on 2010-04-08
I'm sure that this question has been asked before, but I wasn't able to find any info in a search:

My son installed UNR on a netbook for a friend, and I was immediately smitten with the interface. I think it would work great on an old laptop with a 1024x768 display.

Is there a way to install that desktop interface on a regular 9.10 installation?

---

### Post by Megaptera on 2010-04-08
Hi,
In 9.04 one could switch between regular Gnome and NBR look by installing some basic stuff.
As far as I know with 9.10 you need to download & install the NBR iso - I don't think there's a "conversion kit". If one turns up though, I'll grab it too!! 
Same for 10.04 btw.

Richard

---

### Post by nothingspecial on 2010-04-08
```
sudo apt-get install go-home-applet human-netbook-theme maximus netbook-launcher window-picker-applet
```

---

### Post by Naggobot on 2010-04-08
When the first adopter has had the courage to try the above, please post your results here. Can you switch between modes and how? Do you notice any adverse effects?

I wondered this same thing my self some time ago.

With the help of the package names I was able to find a[ wikipedia page]("http://en.wikipedia.org/wiki/Ubuntu_Netbook_Edition#cite_note-10") of the UNE as it is now called which led me to [confirmed bug]("https://bugs.launchpad.net/ubuntu/+source/desktop-switcher/+bug/463915") for desktop switcher in 9.10.

As you probably noticed the package list nothingspecial posted does not include the desktop switcher

---

### Post by Rockyc on 2010-04-08
Hmmm. . . installed okay but nothing happened after a logout/login - only a blank brown wallpaper.

Does it require desktop effects to be turned on? Ubuntu doesn't like the ATI chip in my laptop, so I can't run Compiz. I tried using a custom xorg.conf, but the display is still flaky.

My display started acting funny, so I removed the packages.

---

### Post by nothingspecial on 2010-04-08
You have to add the packages to system > preferences > startup applications except for the theme

---

### Post by Rockyc on 2010-04-08
Reinstalled after an update. . .

netbook-launcher fails to launch from a terminal window.

libnotify-Message:GetServerInformation call failed: The name org.freedesktop.Notifications was not profided by any .service files

libnotify-Message: Error getting spec version

---

