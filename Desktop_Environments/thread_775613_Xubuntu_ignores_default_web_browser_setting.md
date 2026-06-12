---
title: "Xubuntu ignores default web browser setting"
date: 2008-04-30
forum: Desktop Environments
---

### Post by rjmoerland on 2008-04-30
I originally posted [this ]("http://ubuntuforums.org/showthread.php?t=768138")thread, because Thunderbird did not open hyperlinks anymore after an upgrade of Xubuntu 7.10 to 8.04. I had removed firefox 3 and replaced it with firefox 2, since some of my often-used extensions were not supported.

I found a bit of a hack, that worked with Thunderbird, and it now opens hyperlinks again. Therefore, I've marked the original thread as solved. However, it seems that my whole desktop is browser ignorant. Not one application opens firefox-2, my preferred browser (and set as such in the 'Preferred Applications' dialog), except for Thunderbird due to my hack. Currently, the only solution I have found to work is to create a symbolic link in /usr/bin, named firefox and link it to firefox-2. Extremely silly, but this does revive all the clickable links on my desktop again. Does anyone know a better solution? Or does anyone know where Xubuntu stores its preferred application settings? Has this changed since 7.10?

Thanks!

---

### Post by rjmoerland on 2008-05-02
Anyone?

---

### Post by mali2297 on 2008-05-02
> **rjmoerland said:**
> Does anyone know a better solution? Or does anyone know where Xubuntu stores its preferred application settings? Has this changed since 7.10?

These settings are stored in the file **~/.config/xfce4/helpers.rc**. If you make you own launch command, it will be stored in **~/.local/share/xfce4/helpers/custom-WebBrowser.desktop**.

---

### Post by rjmoerland on 2008-05-02
> **mali2297 said:**
> These settings are stored in the file **~/.config/xfce4/helpers.rc**. If you make you own launch command, it will be stored in **~/.local/share/xfce4/helpers/custom-WebBrowser.desktop**.

Thanks for the info - everything seems to be there. I have
```

WebBrowser=custom-WebBrowser

```
in my ~/.config/xfce4/helpers.rc file. And indeed also a file named ~/.local/share/xfce4/helpers/custom-WebBrowser.desktop that defines the command and its parameters. It just doesn't seem to be used :confused:

---

### Post by mali2297 on 2008-05-02
> **rjmoerland said:**
>  And indeed also a file named ~/.local/share/xfce4/helpers/custom-WebBrowser.desktop that defines the command and its parameters. It just doesn't seem to be used 

What's the content of the .desktop file?

---

### Post by rjmoerland on 2008-05-02
It's 
```

[Desktop Entry]
NoDisplay=true
Version=1.0
Encoding=UTF-8
Type=X-XFCE-Helper
X-XFCE-Category=WebBrowser
X-XFCE-CommandsWithParameter=/usr/bin/firefox-2 "%s"
Icon=firefox-2
Name=firefox-2
X-XFCE-Commands=/usr/bin/firefox-2


```

---

### Post by mali2297 on 2008-05-03
I don't know why it doesn't work, but might it be the "-" in "firefox-2"?

Your solution is probably the easiest.

---

### Post by rjmoerland on 2008-05-03
I thank you for your time. I've decided to downgrade back to Gutsy again. The amount of tiny things that do not work anymore is just not worth the gain of upgrading to Hardy, yet.

Thanks again!

---

### Post by CrusaderAD on 2011-12-13
Old thread, same problem. I'm experiencing this in 11.10. Any ideas?

---

### Post by scottwm on 2011-12-18
I installed Xubuntu-11.10 yesterday (had been using Ubuntu-10.10) and was having a problem setting Google Chrome as the default browser. Clicking the "Set as default" button that shows up in chrome did not work. And in fact, it made it so that no application was the default browser.

The first thing I tried was to open the Applications Menu and go to Settings / Settings Manager / Preferred Applications and under "Web Browser" click "Other ..." in the drop-down list. I set the path to chrome in the dialog box (/opt/google/chrome/google-chrome for me; I installed using a .deb package I downloaded from google.com yesterday).

It partially worked. That is, it worked for http:// and https:// links. But file:// links and .html files on my hard drive still came up in Firefox. This was a bit annoying to me, because I spend a decent amount of time in HTML documentation for things like Python, SWIG, etc.

Anyway, the missing piece (which took me a while to figure out) was to open Thunar (File Manager), right-click on an .html file, and click "Properties ...". I found that "Open With:" was set to Firefox. Ah yes ... So I selected "Google Chrome" and now the file:// URLs and local .html files open the way I want.

---

### Post by DarkED on 2012-02-07
Same problem over here. Xubuntu 11.10 on several machines not liking the fact that I want chromium-browser to be default. It's a very nice OS otherwise :D

EDIT: Just figured out a possible workaround. If you go into Settings Manager -> Preferred Applications and set 'chromium-browser' to be default (you must type the command manually) then actually open Chromium and tell it to NOT check if it's the default again, it seems to work around this issue. I'll report back after a couple more reboots.

---

### Post by pmorch on 2012-02-14
Ok, so I have *no* idea why this worked, but it did for me:
In a terminal, run "gnome-control-center", click "Preferred Applications" and select your desired browser there too. At least thunderbird and glipper took their selection from there. Go figure. :-( Works for me now. :-)

---

### Post by ShawnMilo on 2012-04-25
I had this same problem, only in Thunderbird.

Nothing worked until I followed the instructions here:

[http://kb.mozillazine.org/Default_browser#Setting_the_browser_that_opens_in_Thunderbird_-_Linux](http://kb.mozillazine.org/Default_browser#Setting_the_browser_that_opens_in_Thunderbird_-_Linux)

Set "True" in these values:

network.protocol-handler.warn-external.http
network.protocol-handler.warn-external.https
network.protocol-handler.warn-external.ftp

That way, next time you click a link, Thunderbird will provide a dialog asking you which browser to use, and you can click the checkbox to have it remember that choice.

This appears to have inserted extra lines to mimeTypes.rdf in my Thunderbird "profile" directory.

---

