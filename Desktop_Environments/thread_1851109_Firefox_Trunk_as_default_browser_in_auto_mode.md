---
title: "Firefox Trunk as default browser in auto mode"
date: 2011-09-27
forum: Desktop Environments
---

### Post by arky on 2011-09-27
How do I make the firefox-trunk as the default browser in auto mode. When I click a link in xchat, the link opens with chromium-browser. Here is my x-www-browser setting. 



 sudo update-alternatives --config x-www-browser 
There are 2 choices for the alternative x-www-browser (providing /usr/bin/x-www-browser).

  Selection    Path                       Priority   Status
------------------------------------------------------------
  0            /usr/bin/chromium-browser   40        auto mode
  1            /usr/bin/chromium-browser   40        manual mode
* 2            /usr/bin/firefox-trunk      40        manual mode

Press enter to keep the current choice[*], or type selection number:

---

### Post by Krytarik on 2011-09-27
Wanna know how it looks in my case, while all links from every apps are opened in Firefox? Here it is :p :
```
There are 2 choices for the alternative x-www-browser (providing /usr/bin/x-www-browser).

  Selection    Path                       Priority   Status
------------------------------------------------------------
* 0            /usr/bin/chromium-browser   40        auto mode
  1            /usr/bin/chromium-browser   40        manual mode
  2            /usr/bin/firefox            40        manual mode

Press enter to keep the current choice
[*], or type selection number: 

```So, it doesn't seem to be of real importance what is set there. More important is what is set in "Preferred Applications", for a start.

---

### Post by arky on 2012-01-02
The correct file to edit is mimeinfo.cache. However the chromium replaces the default browser quite often (will file a bug).


sudo nano /usr/share/applications/mimeinfo.cache 

#Before

x-scheme-handler/http=chromium-browser.desktop;firefox-trunk.desktop;
x-scheme-handler/https=chromium-browser.desktop;firefox-trunk.desktop;

#After 
x-scheme-handler/http=firefox-trunk.desktop;chromium-browser.desktop;
x-scheme-handler/https=firefox-trunk.desktop;chromium-browser;

---

