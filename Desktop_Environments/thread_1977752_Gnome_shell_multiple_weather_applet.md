---
title: "Gnome shell multiple weather applet"
date: 2012-05-10
forum: Desktop Environments
---

### Post by Mr.Pytagoras on 2012-05-10
Hi 

How can I start the weather applet in gnome shell say two times, one would be for one city and the second one for another.

---

### Post by Frogs Hair on 2012-05-10
Indicator weather will allow for the  setup of more than one location, but it will appear as an icon on the bottom right and remain hidden until you move the cursor to the bottom right of the screen.  My current gnome shell weather extension displays on top, but only allows for one location. ```
sudo apt-get install indicator-weather
```  Restart the shell and start the weather indicator by selecting the icon from applications. When the icon appears on the bottom right enter preferences for setup.

---

### Post by Mr.Pytagoras on 2012-05-11
if you install the classic systray extension it will be displayed at top panel and always visible.

---

### Post by mrpot on 2012-05-21
> **Frogs Hair said:**
> Indicator weather will allow for the  setup of more than one location, but it will appear as an icon on the bottom right and remain hidden until you move the cursor to the bottom right of the screen.  My current gnome shell weather extension displays on top, but only allows for one location. ```
sudo apt-get install indicator-weather
```  Restart the shell and start the weather indicator by selecting the icon from applications. When the icon appears on the bottom right enter preferences for setup.
Hi, how to put weather indicato on the top panel in gnome-shell?I have only one location, there is nothing similar to the classic gnome panel?

thanks

---

### Post by Frogs Hair on 2012-05-21
The gnome shell extension that made the use of indicator-weather possible in the top panel was rejected for some reason. You can add the extension at the link though. [http://www.webupd8.org/2011/10/install-gnome-shell-weather-extension.html](http://www.webupd8.org/2011/10/install-gnome-shell-weather-extension.html)

---

### Post by Frogs Hair on 2012-05-21
This is how mine appears , but I like it that way .

---

### Post by tumutanzi.com on 2012-05-21
I have also the problem, now solved, thanks for the solution offered here.

---

### Post by mrpot on 2012-05-22
many thanks, extension installed !works fine ;-)
see attachments, for anyone is useful,
only one thing, in the webup8 page he talk about and rss icon to find the WOEID,
i'm not see this icon, but with firefox ctrl+u,
search for : woeid or in my case for:
providerLocId

after this word are the WOEID code to paste into extension prop.s

many thanks to all

---

