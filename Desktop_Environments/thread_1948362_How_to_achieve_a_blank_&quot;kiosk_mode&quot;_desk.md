---
title: "How to achieve a blank &quot;kiosk mode&quot; desktop for customers?"
date: 2012-03-28
forum: Desktop Environments
---

### Post by wagalaweia on 2012-03-28
Hi!
I want to provide to the visitors of a museum a Touchscreen-PC, on which just a single software is running forever (in a fullscreen borderless topmost window), thus, only left-clicks and left-double-clicks can be created by the user. Therefore, I want to use some Linux, preferably some Ubuntu-derivate. Even though the desktop is usually hidden (as long as the software does not crash), I want it to be absolutely free of any panels - just a black screen. Most important: I do not want to display any notifications and other stuff ever (e.g. on updates, summertime, screen lock, etc.). However, pressing Ctrl+Alt+T should still open a new terminal (for maintaining when plugging in a keyboard).

Is there some simple flag or some package "kiosk mode", which enables this behaviour?

Or do I have to remove all the panels and notifications on my own? If yes, do you know a complete list of things (panels, notification-manager, ...) that I have to disable or remove?

Any comments are welcome!

---

### Post by wagalaweia on 2012-04-03
...just replying to myself.

Well, of course I tried the search function before posting, but the word "kiosk" came to my mind while writing the post, so I did not search for it. However, googling for "ubuntu kiosk mode" provides the following solution:

[http://www.instructables.com/id/Setting-Up-Ubuntu-as-a-Kiosk-Web-Appliance/?ALLSTEPS](http://www.instructables.com/id/Setting-Up-Ubuntu-as-a-Kiosk-Web-Appliance/?ALLSTEPS)

It especially describes how to start an XSession without any window-manager at all (just starting some software and going back to login screen when it has ended). This provides exactly the functionality I needed.

Further, if anyone is interested in some browser kiosk mode, try Opera. It has the best kiosk mode a browser can have (compared to Chromium, Firefox and IE), including several flags for customization (e.g., hide context menu, disable keys, etc.):

[http://www.opera.com/support/mastering/kiosk/](http://www.opera.com/support/mastering/kiosk/)

---

### Post by Lars Noodén on 2012-04-03
This HowTo looks promising:

[http://www.alandmoore.com/blog/2011/11/05/creating-a-kiosk-with-linux-and-x11-2011-edition/](http://www.alandmoore.com/blog/2011/11/05/creating-a-kiosk-with-linux-and-x11-2011-edition/)

---

