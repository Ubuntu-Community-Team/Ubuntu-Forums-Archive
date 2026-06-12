---
title: "I broke my gnome!"
date: 2009-01-17
forum: Desktop Environments
---

### Post by eatberrys on 2009-01-17
When i log in to my gnome desktop All that i can see is my background.
I do hear the login sound thou and can login to different environments such as fluxbox and fvwm.

after i login i can use ctrl+alt+back to log out . then when i log in to Fluxbox i run "top" and gnome-panel is eatting my cpu 
after killing gnome-panel the cpu stops over working 

Help to get my gnome back would be awesome 

thanks in advanced!

---

### Post by eatberrys on 2009-01-19
Well no one responded but i figured it out 
For any one that sees this thread trying to fix there gnome
```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

---

### Post by CraigPaleo on 2009-01-19
> **eatberrys said:**
> Well no one responded but i figured it out 
For any one that sees this thread trying to fix there gnome
```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

What exactly does that do? My Gnome is fine - just curious. Someone around here has in their signature to never run the rm command unless you know what it does and what you're doing. From that, I got the impression that rm removes things.

This might come in handy for the Travelocity Gnome. :-)

---

### Post by adamlau on 2009-01-19
```
man rm
```

Forces the recursive removal of the listed GNOME settings files. The files will be recreated once X is restarted.

---

### Post by Bishop01 on 2009-03-05
Hi, 

I am using Ubuntu 8.10. I experimented with other window managers e.g. Awesome but accidentally chose it as my 'default session'. How can I go back to Gnome?

Thanks

---

### Post by NoaHall on 2009-03-05
> **Bishop01 said:**
> Hi, 

I am using Ubuntu 8.10. I experimented with other window managers e.g. Awesome but accidentally chose it as my 'default session'. How can I go back to Gnome?

Thanks

Click "Sessions" before loging in, then choose Gnome

---

### Post by hictio on 2009-03-05
> **eatberrys said:**
> Well no one responded but i figured it out 
For any one that sees this thread trying to fix there gnome
```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

> **CraigPaleo said:**
> What exactly does that do? My Gnome is fine - just curious. Someone around here has in their signature to never run the rm command unless you know what it does and what you're doing. From that, I got the impression that rm removes things.

This might come in handy for the Travelocity Gnome. :-)

Executing that command will put your Gnome desktop like the first time you logged on into  it.
For what I read you should execute not on a running Gnome session, but, either from a recovery session on the CLI; or after stopping the graphical environment from a Virtual Console.

---

