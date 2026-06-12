---
title: "temperature indicator applet"
date: 2010-04-10
forum: Desktop Environments
---

### Post by irielion on 2010-04-10
Today I thought to play around with the new ubuntu indicator applet, so I wrote a temperature monitor applet, named temperature-indicator. I shows the temperature for your CPU and their freq. When passing one trip point, it will notice you of a hot CPU, finally on the critical trip point it will either suspend or shutdown.

The deb is made on lucid, but it probably also works on karmic (or maybe jaunty). 

Try it out on [https://launchpad.net/temperature-indicator](https://launchpad.net/temperature-indicator): [http://launchpad.net/temperature-indicator/0.1/0.1/+download/temperature-indicator_0.1-1sol_all.deb](http://launchpad.net/temperature-indicator/0.1/0.1/+download/temperature-indicator_0.1-1sol_all.deb)

After installing you can find the menu item in Applications->Accessoires. For the next version I will add an autostart option.

---

### Post by km0r3 on 2010-04-10
Cool!  :)

---

### Post by ootuoyetahi on 2010-04-10
Any chance of getting a screenshot?

---

### Post by steveneddy on 2010-04-10
I thought we already had a few of those available in the Gnome panel already?

How is yours different again?

---

### Post by irielion on 2010-04-11
This one is different as it fully integrates with ubuntu's features, like indicator-applet and notify-osd. Additionally, it is a zero-config application, which means you dont have to configure anything. It automatically takes the information from the processor on temperature trip points. It is also a very compact applet and doesn't consume any space on your panel.

A screenshot is not necessary as it is just an icon, and when you click a menu with your temperatures per core and a exit entry.

---

