---
title: "keyboard doesn't work after login"
date: 2008-12-28
forum: Desktop Environments
---

### Post by madhusker on 2008-12-28
Hi,

I am running hardy and all was well until the keyboard quit responding while sorting files in Dolphin.  I thought a reboot may do the trick but I was wrong. There are no problems at all at log in. I can enter my user name and password no problem but once the desktop loads the USB keyboard is dead.

Note - I created a test user account and it works perfect!  There is something with my main user account that will not allow keyboard to work after initial log in.  The USB mouse works fine in either case. Any ideas where to start?

---

### Post by madhusker on 2008-12-28
Answer found here:
[URL="http://www.linuxforums.org/forum/redhat-fedora-linux-help/136192-solved-my-keyboard-doesnt-work-after-login.html"]
http://www.linuxforums.org/forum/redhat-fedora-linux-help/136192-solved-my-keyboard-doesnt-work-after-login.html[/URL]

> I fixed it. I was checking settings in Control Panel. Under Regional and Accessibility - Accessibility, Keyboard Filters, there's something called "SlowKeys". Slow Keys was turned on. Once I deselected it, the keyboard worked again.

No idea how that got turned on (obviously)....

---

