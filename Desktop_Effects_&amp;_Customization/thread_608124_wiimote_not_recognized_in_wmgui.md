---
title: "wiimote not recognized in wmgui"
date: 2007-11-09
forum: Desktop Effects &amp; Customization
---

### Post by xjgnsdof on 2007-11-09
I performed all of the steps for setting up the wiimote in Cwiid (in the wiki, I'm at the "Controlling the Remote" step), but in wmgui I get a pop-up saying "unable to connect" and a Terminal message saying "Error opening control channel." I basically copied and pasted every command, so I have no clue why it's working for some of you and not for me. The Wiimote is brand new, and so is my Bluetooth dongle (which manages to pick up the Wiimote in the hcitool scan). What's wrong here?

---

### Post by xjgnsdof on 2007-11-10
up

---

### Post by xjgnsdof on 2007-11-11
solved...merely had to specify my wiimote bluetooth address, which is discoverable after the hcitool scan command.

---

### Post by barney_1 on 2008-01-07
This helped me.  wmgui just kept saying "unable to connect".

1. Get your wiimote bluetooth address.  Press 1 and 2 on the wiimote at the same time.  The four blue leds will start blinking.  Then type this the console:
```
hcitool  scan
```

You should get something like this:
```
demo@faiserver:~$ hcitool  scan
Scanning ...
       00:19:1D:7C:4D:E6       Nintendo RVL-CNT-01
```

2. Plug that number in for wm gui:
```
wmgui 00:19:1D:7C:4D:E6
```

Should work like a charm.

---

