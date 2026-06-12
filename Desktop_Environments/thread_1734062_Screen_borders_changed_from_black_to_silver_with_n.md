---
title: "Screen borders changed from black to silver with no input from me"
date: 2011-04-19
forum: Desktop Environments
---

### Post by tdcarlo on 2011-04-19
So I am surfing the internet when I notice that the top and bottom borders are now silver, normally they are black. The borders that contain Applications, Places and System. I never changed them, at least knowingly. I first rebooted to see it would change back. It didn't, they were still silver. I, next, went to System, Preferences, Appearance and I found I had a custom theme. I never intended to create a custom theme. I changed my theme back to Ambiance and then 10 minutes later the borders changed back to silver and the Theme was reset to custom. I changed it back to Ambiance and it's been stable for 30 mins. When I check now, I have no custom settings listed for themes. 

Anybody have a clue why this might be happening?


I am using Ubuntu 10.10

---

### Post by Copper Bezel on 2011-04-19
There's an odd bug that's been killing Gnome Settings Daemon in 10.10, killing the theming so that everything is flat grey, but the behavior's just a little different - just loading Gnome Settings Daemon fixed it in those instances.

If it happens again, try running this to see if it's a related problem:

```
killall gnome-settings-daemon; gnome-settings-daemon
```

---

### Post by tdcarlo on 2011-04-20
Thanks Copper Bezel,

That did the trick....

---

