---
title: "Have links open in firefox without changing focus"
date: 2008-05-21
forum: Desktop Environments
---

### Post by chmac on 2008-05-21
G'day,

I'd like to have web links open in firefox while the current application retains focus. For example, if I click a link in an email (evolution), I'd like firefox to start loading the link, but the email to remain on top of the screen, current, with focus, whatever.

This was the default behaviour on Fedora 8 with Firefox 2. I'm not sure if it's a change since switching to Ubuntu, or Firefox 3, or something else.

Any tips / tricks would be great.

---

### Post by bobjenkins on 2008-05-21
So when you open firefox through a link of a different app (evolution and whatnot) you want the app (evo) to stay on top?

I think there is a setting in firefox, Edit > Preferences > Tabs > then play around with those settings, mainly the one that says "When I open a link in a new tab, switch to it immediately. 

Make sure you have this option set to New window.
-New pages should be opened in
**A. New window**
B. New tab

Hopefully that helps

Sorry I do not know how to do with while retaining the option to open new links in tabs.

---

### Post by chmac on 2008-05-21
> **bobjenkins said:**
> So when you open firefox through a link of a different app (evolution and whatnot) you want the app (evo) to stay on top?

Exactly, you've understood precisely what I'm after! :)

> **bobjenkins said:**
> I think there is a setting in firefox, Edit > Preferences > Tabs > then play around with those settings, mainly the one that says "When I open a link in a new tab, switch to it immediately. 

Make sure you have this option set to New window.
-New pages should be opened in
**A. New window**
B. New tab

Unfortunately this doesn't change the behaviour. I think the issue lies with gnome-open, that's my guess. But I'm not sure. I can't find much documentation on gnome-open. But I believe that's the command that's called by evolution (or other programs) to open links.

This is the default behaviour in Fedora 8 with Firefox 2, so I reckon it must be possible. Maybe I could grab the gnome-open executable from F8 and try that...

---

### Post by chmac on 2008-05-21
> **chmac said:**
> This is the default behaviour in Fedora 8 with Firefox 2, so I reckon it must be possible. Maybe I could grab the gnome-open executable from F8 and try that...

Tried that, no luck. It's odd though, the bin on F8 is 12K while on Ubuntu it's only 4.2K. Anyway, the result is the same, Firefox comes to the focus, in fact even more so as it pops in front of Evolution, whereas with Ubuntu's gnome-open Evolution stays in front, but loses focus and goes semi-transparent.

---

### Post by mark541 on 2008-05-21
In the address bar, type "about:config". Next, look for a line named "browser.tabs.loadDivertedInBackground". If you have one, change the value to "True" by double-clicking on the line. 

If you don't have this line, you can make one. Right-click on any line and select "New" then "Boolean". Type "browser.tabs.loadDivertedInBackground" as the new name and click OK. Select "True", click OK and you're done. You'll may have to restart Firefox for the change to take effect.

---

### Post by mark541 on 2008-05-21
A quick follow up. You can see all of the "about:config" entries (including the "browser.tabs.loadDivertedInBackground" entry) here: 

[http://kb.mozillazine.org/About:config_entries](http://kb.mozillazine.org/About:config_entries)

If you screw up and create an unwanted config line, you can remove (delete) it by following the instructions here:

[http://kb.mozillazine.org/Resetting_preferences](http://kb.mozillazine.org/Resetting_preferences)

---

### Post by chmac on 2008-05-21
> **mark541 said:**
> In the address bar, type "about:config". Next, look for a line named "browser.tabs.loadDivertedInBackground". If you have one, change the value to "True" by double-clicking on the line.

Genius, this is **almost** exactly what I wanted! :) It looks like it is a change in Firefox 3 then. Thanks a million. Oh, and no need to restart Firefox for it to take effect.

What I really want is for the tab to take focus, but the application Firefox itself to not take focus. So the new tab opens, and the item on the Window List goes bold (the application is grabbing attention), but my evolution window is still the focused window.

I've checked the about:config page and I can't see anything that will set this up. The current situation is good, except there's no feedback that the link has actually loaded. So if you click it several times, you end up with a load of firefox tabs open that you hadn't noticed. Say if Firefox was on a different workspace for example. Update: It also means all new tabs open in the background, which is not quite ideal.

I might install Fedora 9 and see what happens with Firefox 3 there...

---

### Post by em3ry on 2009-03-31
> **mark541 said:**
> In the address bar, type "about:config". Next, look for a line named "browser.tabs.loadDivertedInBackground". If you have one, change the value to "True" by double-clicking on the line. 

If you don't have this line, you can make one. Right-click on any line and select "New" then "Boolean". Type "browser.tabs.loadDivertedInBackground" as the new name and click OK. Select "True", click OK and you're done. You'll may have to restart Firefox for the change to take effect.
thank you mark541

---

### Post by 1011101 on 2009-04-02
I have the opposite problem. Whenever I click a link in evo or another program, it opens in a firefox window somehow minimized or in the background. I have to click it twice in the task bar to see the window. 

I want it to open in the foreground instead. My browser.tabs.loadDivertedInBackground setting is already set to false.

---

