---
title: "chrome issues: name has 'skype' in it, and clicking URL launches chrome but no URL"
date: 2018-01-19
forum: Desktop Environments
---

### Post by dwater on 2018-01-19
I have chrome installed - it's at /usr/bin/google-chrome and /usr/bin/google-chrome-stable links to it. Its version is Google Chrome	63.0.3239.132 (Official Build) (64-bit), and I'm on Ubuntu 17:10.

My main problem is that, if I click on a URL in some other app, eg terminal, or skype, then it opens chrome (good), but doesn't show the URL I clicked on, just leaving the page blank.

In an attempt to diagnose the problem, I tried to find the default applications (not so easy to find manually, but the search behind the 'super' key worked), it was indeed set to chrome, but it was called '(1) Skype - Google Chrome' (I see that it is also that on the launcher too). I tried launching chrome from the command line (/usr/bin/google-chrome), and it is still has skype in its name. I suspect the name issue might be a clue.

Anyway, I figured I'd try Firefox so I switched the default application to 'Firefox Web Browser'; and that does launch ok - ie it opens a window on the appropriate URL.

Next I figured I'd try to set it back to chrome again, but now chrome isn't available as an option - not by any name. The only option is FF.

My objective is to have URLs launch into a new window in chrome when I click them, no matter which app. It would also be nice to have chrome named something appropriate.

Any ideas what might be going wrong?

---

### Post by dwater on 2018-01-19
This seemed to help me with the name:

[https://askubuntu.com/questions/689449/external-links-are-opened-as-blank-tabs-in-new-browser-window-in-chrome](https://askubuntu.com/questions/689449/external-links-are-opened-as-blank-tabs-in-new-browser-window-in-chrome)

ie, just edit the name in google-chrome.desktop

However, I'm still having trouble getting it listed in the 'default applications'.

---

### Post by dwater on 2018-01-19
duplicate comment, sorry...can't see how to delete it, even though the tooltip on 'Edit Post' implied you can delete it somehow...

---

### Post by vasa1 on 2018-01-19
If you need to delete a duplicate post of yours, please click on the report icon mentioning what you want and forum staff will do what has to be done.

---

