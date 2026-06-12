---
title: "Turn off stupid update notifications in taskbar"
date: 2012-06-02
forum: Desktop Environments
---

### Post by vapor0 on 2012-06-02
It's the most annoying thing - a stupid exclamation point that always lives in my Xubuntu taskbar. Oh, sure, you can get rid of it for five minutes. But then it's back again, looking stupid, and being the irritating PITA it always is.

Is there a way to turn it off? While still keeping the indicator applet? And without turning off Ubuntu's auto-update features, etc.?

Thanks in advance.

---

### Post by LewisTM on 2012-06-03
First install the dconf-tools package
Then launch dconf-editor
The settings you are looking for are under com/ubuntu/update-notifier...
Enable no-show-notifications

More info [here]("http://www.tolaris.com/2012/06/01/disabling-update-notifier-in-ubuntu-12-04/").

Cheers

---

### Post by vapor0 on 2012-06-03
I've done it. I also turned off apport crash notifications. (Of course, I don't actually know if it's working yet... but if there's no update notifications in the next hour, I'm calling it a success.)

Thanks!

---

