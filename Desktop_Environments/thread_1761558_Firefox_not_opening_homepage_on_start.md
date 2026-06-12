---
title: "Firefox not opening homepage on start"
date: 2011-05-18
forum: Desktop Environments
---

### Post by PhillyKingston on 2011-05-18
[COLOR=black][FONT=Verdana]I started using 11.04 awhile ago, and switched from Unity to Classic because I didn't like switching from the mouse to the keyboard that frequently to open applications. I noticed that Firefox had stopped using the setting of opening my homepage when I started Firefox and have been trying to figure out why. It turns out yesterday I think I figured it out. There is an add-on for Unity Menus installed, once I disabled that the behavior returned to normal. Hopefully, someone else here will find that useful.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]If someone could let me know why this is a problem or if there is another way to achieve the same results I'd really appreciate it.[/FONT][/COLOR]

---

### Post by lovinglinux on 2011-05-18
There are some bugs in the global menu. I guess this is another one.

Make sure you have you have "Show my home page" in the startup section of the preferences and thta the home page is set to *about:startpage*.

---

### Post by emc on 2011-07-30
> **PhillyKingston said:**
> [COLOR=black][FONT=Verdana]I started using 11.04 awhile ago, and switched from Unity to Classic because I didn't like switching from the mouse to the keyboard that frequently to open applications. I noticed that Firefox had stopped using the setting of opening my homepage when I started Firefox and have been trying to figure out why. It turns out yesterday I think I figured it out. There is an add-on for Unity Menus installed, once I disabled that the behavior returned to normal. Hopefully, someone else here will find that useful.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]If someone could let me know why this is a problem or if there is another way to achieve the same results I'd really appreciate it.[/FONT][/COLOR]

I am having the same issue.  Of course, I have already restarted many times, have ensured Firefox Preferences -> Firefox starts: "Show my home page" and Home Page: about:startpage

I have also tried changing to any website - like [http://www.google.com](http://www.google.com) and still when I restart Firefox 5 I get "Connecting" and at the bottom it is some number.  

Fix - Disable iMacros... I believe this bug happened when I accidentally synced the iMacros folder to Ubuntu One.  Since then - no connecting to any home page and nothing I can think of will change this beyond disabling iMacros.  Once I re-enable iMacros and restart - it will connect.  The first time I use a bookmark with iMacros then restart firefox will recreate the bug and will not connect.  Any help would be greatly appreciated.  I have uninstalled imacros reinstalled - I have deleted the folder and put it back - I am at a loss here...

---

### Post by emc on 2011-07-30
SOLVED!  Go to CompizConfig Settings Manager and search "D-bus" and uncheck that bad boy... I did that earlier trying to get Tomboy to listen to keyboard shortcuts.  Didn't fix Tomboy and it was precisely the thing causing the problem with Firefox not connecting to home pages.  iMacros obviously plays some part in this because disabling it would allow the browser to connect to home page.  I spent hours trying to solve this - come here and finally post the problem - and then minutes later solve it. Go figure!

---

### Post by emc on 2011-07-30
I am sorry - this is not Solved after all... I am having the same thing happen again and I cannot seem to get Firefox to connect to a home page or start page. I open Firefox and it just says "connecting to..."  So I hit stop and then navigate to any page I want using a bookmark or typing the web address in the URL and then it has no problems.  I just have to always hit 'stop' and then go to a page I want... 

Considering just going back to 10.10 until these bugs are worked out.  I have yet to learn my lesson on waiting until the OS is 'ready' rather then when it launches.  

The bug can come and go - I just never know when it will do either. 

Ubugtu - Free bugs !!

---

### Post by lovinglinux on 2011-07-30
Try to disable ipv6.

[LIST]
[*]Type about:config in the address bar, press Enter.
[*] Find network.dns.disableIPv6 in the list.
[*]Right-click -> Toggle.
[*]Restart Firefox and try again.
[/LIST]

---

