---
title: "Firefox window not managed properly."
date: 2010-07-10
forum: Desktop Environments
---

### Post by guitarMan666 on 2010-07-10
I have an issue I never even thought was possible.  It seems that Compiz doesn't want to manage my Firefox window.  It is Firefox 3.6.6 (as pushed via an official Update) and didn't pose a problem until I followed this guide: [http://news.softpedia.com/news/Ubuntu-10-04-Desktop-Customization-Guide-146134.shtml](http://news.softpedia.com/news/Ubuntu-10-04-Desktop-Customization-Guide-146134.shtml) 
to give my Ubuntu a sleeker look.

This should not effect window management in anyway.  In addition to what is listed in the guide, I added 3 applets to AWN: AWN Terminal, Battery Status and CPU Frequency and took one additional step: I changed the required panel in gconf-editor from "gnome-panel" to "awn" to avoid the annoying top panel popping up when I use my screen corners for "Scale" and "Expo."

All other windows are managed properly except Firefox which now has no title bar, no window border and is unable to be moved.  The Put extension does however place it on the correct workspace and it shows up in scale and the shift switcher.  Reloading via fusion-icon doesn't seem to solve it.  Any thoughts?

---

### Post by guitarMan666 on 2010-07-10
Mysteriously, this problem was resolved by putting Firefox into fullscreen then restoring it.

---

### Post by Naggobot on 2010-08-02
Same problem here. Most of the time when I start Firefox after reboot window looks like this. 

[http://www.flickr.com/photos/naggobot/4852864506/](http://www.flickr.com/photos/naggobot/4852864506/)

Window controls are outside of the window and the top applet bar is behind the window. I also can resolve the issue to some extent by pressing F11 for a few times. This gives me access to applet bar and from the applet bar I can right click Firefox tab and select move. 

Annoying little feature since I use laptop and reboot often. 

I am now testing the applet bar as not expanded and it seems that the window opens in the correct size. On the other hand this totally messes up the top applet bar layout.

---

### Post by Naggobot on 2010-08-11
Okay

If the browser is closed from full-screen mode then window controls are missing when the browser is started next time. Firefox stores the last window state to /home/user/.mozilla/firefox/.../localstore.rdf. If the browser is closed as window maximized then there is a line

```
<RDF:Description RDF:about="chrome://browser/content/browser.xul#main-window" width="1274" height="748" screenX="0" screenY="67" sizemode="maximized"/>
```

Now if the window is closed from the full screen mode then last keyword is "fullscreen" and window controls will be missing when the browser is restarted. '

Solution: Do not close the browser from F11 mode or if you can then write a script to modify the line (I can not). 

I think this is somehow related to last Firefox update since I have two separate computers suffering from this now.

---

