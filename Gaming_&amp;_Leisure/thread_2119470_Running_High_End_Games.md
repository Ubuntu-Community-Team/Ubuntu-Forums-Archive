---
title: "Running High End Games?"
date: 2013-02-23
forum: Gaming &amp; Leisure
---

### Post by Auzzie2009 on 2013-02-23
Hey, guys so this is my first post. And i have a multiboot windows 7/ Ubuntu PC. Now on Windows 7 i can run all the high end games(Skyrim, Battlefield 3, Fallout New Vegas) on highest settings. Now when i moved over to Ubuntu i have a hard time playing pretty much any game that has a decent graphics. Any ideas on how to fix this?

---

### Post by zombifier25 on 2013-02-23
What problems are you having? You should try to be more specific.
This probably has something to do with your other thread that states that Steam gives an OpenGL error.

---

### Post by Auzzie2009 on 2013-02-23
I ahve fixed the OpenGL problem with Steam. With the games, sometimes the app store will not let me run them(you know the buy anyway option) and on the games it does i can get extreme lag, and that sort of thing.

---

### Post by zombifier25 on 2013-02-23
Try using a lightweight DE, like LXDE, to play games and see if the performance improves. Unity is a rather heavy beast.

---

### Post by Auzzie2009 on 2013-02-23
I will get LXDE to see if it will help.

---

### Post by myromance123 on 2013-02-24
The first question that comes to mind is if you've actually installed any graphics drivers for your system. Off the bat, Ubuntu uses an open-source driver for your card (be it AMD/ATi or Nvidia). The Open Source drivers are not up to par with the proprietary drivers yet, meaning less performance.

[B]---------------------------
NOTE: before trying to install the drivers like below, please update Ubuntu and do the following to keep yourself safe from experiencing problems later on.

Open a Terminal and input this:
sudo apt-get install linux-headers-generic

Hit enter, and when it asks for your password just put it in and hit Enter again. It may ask [Y/n], just hit "y" and Enter again. Now you're ready to follow the below instructions.
---------------------------[/B]

In Ubuntu's Dash, search for System Settings. On the top right select the "Additional Drivers" tab.

If you're using an AMD/ATi card, make sure that you have fglrx-updates or I think it's now called post-release driver selected. Then hit Apply Changes and restart your computer.

If you're using an Nvidia card, make sure you have the 310 drivers selected (will be called experimental-310, you can try experimental-304 too). Then hit Apply Changes and restart your computer.

If you're using an Intel Integrated graphics card, then you shouldn't have to do anything. It should already be installed automatically.

Hopefully this helps you, but this might not be the issue you're having either. I personally use the Nvidia 310 experimental drivers, and can play all my games at 1080p with full settings.

*P.S: Do you have "Unredirect Fullscreen" ticked in CCSM? This might help increase performance for your fullscreen games.

---

### Post by Auzzie2009 on 2013-02-24
Thank You!

---

### Post by myromance123 on 2013-02-25
Glad I could help you :)

---

### Post by Lightning Dragon on 2013-02-25
Good work, myromance123. :)

Auzzie, if it worked could you mark the thread solved? It would help a lot of people with this problem if they came across the thread. Also, when you log into Ubuntu, you should see a little white star like icon next to the log in window display. If you click that, you can select between different desktop environments so you don't have to use Unity.

---

