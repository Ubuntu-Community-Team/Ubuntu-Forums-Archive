---
title: "Bash proxy script???"
date: 2006-01-11
forum: General Help
---

### Post by bb002 on 2006-01-11
I'm looking to make a bash script that i can run, that will enable/disable the proxy for several applications to free myself the trouble of doing it by hand. It gets old doing it by hand twice a day 5 days a week.

I need to know how to change the proxy of each of these apps from a terminal:

Gnome     -- For a few panel-applets
firefox     -- Hey, I need tp browse the internet too.
synaptic/apt-get -- Any software I decided install while at work.

Hopefully this won't require the use of "sed" or the like. Otherwise I'll need to be spoon-fed the specific commands....

Anyone done this before and got a script laying around or know some nice tips to ease this along...

---

### Post by schilcha on 2006-01-11
For firefox, there's an extension called "SwitchProxy", that lets you choose from a list of proxies while browsing (no need to restart or anything -- just point and click). I'm using it with success with firefox 1.0.7.

For terminal-apps (like apt-get), set the environment-var $http_proxy or $ftp_proxy. You can try to set them automatically in your ~/.bashrc according to your ip-address (if they are different for at the different networks you connect to, such as 10.0.0.x at one and 10.42.42.x at the other site)

For gnome-stuff, I can't help...

Good Luck!

---

### Post by bb002 on 2006-01-12
Thanks!

I found where to change gnome's proxy.
```

gconftool --type bool -s /system/http_proxy/use_http_proxy true
killall gnome-panel

```
The Gnome panels realize the value has changed but ignore I unless i killall panels. I'll probably just end up using the firefox extension since that's what I change the most. the others are when i need them, which isn't often.

---

### Post by bb002 on 2006-01-12
double post....Kept getting "lost connection to origin server" for "www.ubuntuforums.org". Just now got let back in....

---

