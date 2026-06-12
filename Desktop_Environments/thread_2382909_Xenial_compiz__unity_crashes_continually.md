---
title: "Xenial compiz / unity crashes continually"
date: 2018-01-18
forum: Desktop Environments
---

### Post by mark-reddin on 2018-01-18
Hi.  When I start Xenial Ubuntu Desktop, after login, I cannot interact with the launcher or any other part of the desktop like the icons in the top right of the screen.  If I do, it all disappears, and then reappears after a few seconds, but the loop continues.  If I Alt+Tab, the same thing happens.  I can still Crtl+Alt+Tab to start a terminal, and launch applications that way, but I can't use the UI itself at all.

I am not sure what part of Ubuntu this is an issue with - Compiz or Unity maybe.

How do I go about diagnosing what is wrong?

Extra info - Trusty is fine, and so tool was Xenial from the iso disk image install, until I ran update-manager and applied all the pending updates.  That is when the problems started happening.

Thanks for any help
Mark

---

### Post by Frogs Hair on 2018-01-19
Try the  following.

```
sudo apt-get install dconf-tools
``````
[COLOR=#000000][FONT=&amp]dconf reset -f /org/compiz/[/FONT][/COLOR]
```

---

### Post by mark-reddin on 2018-01-21
Thank you.  After a restart, that solved it.  I have now also upgraded the trusty installation to xenial and it doesn't give the same issue.

---

