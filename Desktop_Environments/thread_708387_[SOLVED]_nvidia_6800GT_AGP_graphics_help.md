---
title: "[SOLVED] nvidia 6800GT AGP graphics help"
date: 2008-02-26
forum: Desktop Environments
---

### Post by oddworld on 2008-02-26
I tried to get the NVIDIA drivers working, but I think I have put myself into a ditch.
Now there are no graphics at all, and I can see nothing, even ctrl-alt F1 wont display anything.

I need to get the drivers working, but nothing had really worked yet.
Any idea how I can get low-graphics back?
Is there a command like dpkg-reconfigure or something that will restore my xorg.conf?

---

### Post by oddworld on 2008-02-26
I did:
```

sudo dpkg-reconfigure xserver-xorg

```
But I cant see it. 
I see a fuzzy blue screen, but I dont even have graphics in ubuntu. 
I see the splash screen, and hear the drums, but even in ctrl-alt F1, I am completely blind.

I pushed random buttons in the above code, but nothing worked.
Now it appears I have some graphics but the screen is stuck on:

*starting ana(h)ronistic cron anacron
*starting deffered execution scheduler atd
*starting periodic command scheduler crond
*checking battery state...
*running local boot scripts (/etc/rc.local)

But its frozen on that screen

I am able to log in using CTRL-ALT-F1, but now what?

---

### Post by oddworld on 2008-02-27
[SOLVED]
I reinstalled ubuntu and used envy.
1.) install envy
2.) REBOOT
3.) use envy
4.) REBOOT
5.) worked  :)

---

