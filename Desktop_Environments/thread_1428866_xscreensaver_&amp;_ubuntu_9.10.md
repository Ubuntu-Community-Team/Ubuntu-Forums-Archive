---
title: "xscreensaver &amp; ubuntu 9.10"
date: 2010-03-13
forum: Desktop Environments
---

### Post by portly on 2010-03-13
Sorry if this is a really stupid question......

Since the upgrade from 9.04 to 9.10 I've had problems with screensavers.

I want the bouncing cow, which appears to be xscreensaver. So I can open and set it ok, but it just won't start automatically.

I did have gnome-screensaver installed as well, but managed to uninstall that, which, if the OP was correct, should have allowed the xscreensaver to start.

It hasn't. 

I've used linux for quite a while, but don't really understand how it works "under the hood" - if the car breaks, it goes to a garage. but there's not such thing as "linux garage" as far as I can find so I'm having to try and learn how to cure this myself, without success.....

Could someone point me in the right direction please ????

cheers

P!

p.s. oh and I don't know whether it's possible to use this "system-wide" as I use gnome GUI and my partner, well she uses KDE gui.......

---

### Post by rCXer on 2010-03-13
Is your xscreensaver daemon is running?

System -> Administration-> System Monitor. Click on the "Processes" tab and check if "xscreensaver" is there.

---

### Post by portly on 2010-03-14
> **rCXer said:**
> Is your xscreensaver daemon is running?

System -> Administration-> System Monitor. Click on the "Processes" tab and check if "xscreensaver" is there.

Thanks for the response rCXer,

Yes, the process is there, but it's showing as "sleeping".

I right clicked on it to see what options it might show, but there doesn't seem to be one that will allow me to "wake it up" or too start at boot.

Do you know how that might be done please ???

regards

portly

---

### Post by rCXer on 2010-03-14
hmm... but it should be sleeping. Just to make sure the settings are correct, enter...
```

xscreensaver-demo

```
...into the terminal.

Make sure the Mode isn't "Disable Screen Saver" and that "Blank After" is set to a reasonable time.

---

### Post by portly on 2010-03-17
> **rCXer said:**
> hmm... but it should be sleeping. Just to make sure the settings are correct, enter...
```

xscreensaver-demo

```
...into the terminal.

Make sure the Mode isn't "Disable Screen Saver" and that "Blank After" is set to a reasonable time.
No, that brings up the dialogue box fine.

it's set to 1 screensaver only (chosen favourite being the bouncing cows) and it's set to cycle after 5 minutes and blank after 240 minutes.

And I've still failed to find anything else that gives me a clue as to whats going on.......

thank you for the assistance thus far.....

regards

portly

---

### Post by rCXer on 2010-03-17
> **portly said:**
> 
it's set to 1 screensaver only (chosen favourite being the bouncing cows) and it's set to cycle after 5 minutes and blank after 240 minutes.


That's the problem! "Blank after" is the time the computer needs to be idle before the screen saver turns on.  A value of 240 means that you would have to wait 4 hours before your screensaver starts. Just enter a lower time.

---

