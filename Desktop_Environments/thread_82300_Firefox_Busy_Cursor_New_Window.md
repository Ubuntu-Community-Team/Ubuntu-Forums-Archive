---
title: "Firefox Busy Cursor New Window"
date: 2005-10-26
forum: Desktop Environments
---

### Post by ep_ on 2005-10-26
When an instance of Firefox is already running and I  launch a new instance from either the K-menu or the  button I have on the panel, a new window will popup but  I'll also get a jumping busy cursor which last about 25 seconds.  Quite annoying, This problem has persisted through several versions of Kubuntu and Firefox.

I checked the properties on both the menu and the button, they both use 'firefox %u' for the command.   This might be something that needs changing but I believe this was the default k-menu setup with the ubuntu firefox package.

Can't I fix this problem?  I am always able to snappily launch a new window from within Firefox via either File | New Window  or Ctrl-N.  It is very quick and there is no busy cursor happening!  

Regards

---

### Post by shakin on 2005-10-26
[QUOTE=ep_]When an instance of Firefox is already running and I  launch a new instance from either the K-menu or the  button I have on the panel, a new window will popup but  I'll also get a jumping busy cursor which last about 25 seconds.
Regards[/QUOTE]

I've found this also happens when launching a new instance of Firefox. FF will be ready to go, but the mouse cursor still says it's busy. At the moment I have FF 1.5 beta 2 installed and don't get that problem, so it might be specific to 1.0.x or to the Ubuntu FF package.

However, I did manage to fix the problem on 1.0.x by going into KDE Control Panel -> Appearance & Themes -> Launch Feedback and then adjusting the startup indication timeout to only a few seconds. Mine's set to 5 seconds right now, but the default is 30 seconds, whch is the delay you're seeing.

---

### Post by ep_ on 2005-10-27
I too have Firefox Beta 2, just didn't mention it in my original posting.  (rocks btw).  I installed it following this HOWTO: 

[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

On the final step I got the following type of errors```
*** upgradeExtensionChrome: failed for extension talkback@mozilla.org - why not convert to the new chrome.manifest format while you're at it? Failure exception: [Exception... "Component returned failure code: 0x80520015 (NS_ERROR_FILE_ACCESS_DENIED) [nsIFile.create]"  nsresult: "0x80520015
```

Life is good because over all it worked anyway but I  lost my settings and I had to manually import my backed up bookmarks.   I mention all this because right after the install I did not get the busy cursor when launching from the panel whether or not an instance of firefox is already running.   Then all the sudden I started getting the busy cursor from out of the blue.

Funny thing, today (three days later) I launch firefox and get some sort of error dialog about being unable to install chrome.  Now all the sudden, everything is working perfectly and I'm no longer getting the busy cursor when I launch extra instances from the panel or menu.  Weird.

---

