---
title: "Wiimote and Linux Games"
date: 2009-04-01
forum: Gaming &amp; Leisure
---

### Post by roblloyd on 2009-04-01
Hi, Does anyone know how to map a wiimote as controller for linux games? i wanna try vdrift using a mario-kart steering wheel type arrangement!

The wiimote is already hooked up and working as a mouse, but I'm not sure where to go from there.

Cheers in advance

---

### Post by damis648 on 2009-04-01
[Here]("http://ubuntuforums.org/showthread.php?t=993376") you go. :popcorn:

---

### Post by roblloyd on 2009-04-01
Thanks for the fast reply, but not all that helpful. I can already do the whole wiimote as a mouse thing, but i want to access the sensors so that you unlock the full potential of the wiimote as a steering wheel/golf club/baseball bat doohicky.

I'm wondering if there has been any progress so that a) when they one day get a wii emulator going it will work properly, and b) so that i can play games on my computer so that its like a wii! What do you think damis?

---

### Post by damis648 on 2009-04-01
I wrote a config file that maps everything on the controller to axis and buttons a while ago, have a look.

[http://pastebin.ubuntu.com/142490/plain/](http://pastebin.ubuntu.com/142490/plain/)

Copy the contents to /etc/cwiid/wminput/controller and use the command:
```
gksudo wminput -c controller <your wiimote's bluetooth address>
```
to start it. I recommend setting the Plugin.acc.Roll_Scale and Plugin.acc.Pitch_Scale to 0.0 when mapping buttons, and setting a single one to 1.0 and the other to 0.0 when mapping one axis, and then reverse for the other axis. :popcorn: This keeps you from accidentally mapping an axis when mapping a button (it's pretty sensitive) and accidentally mapping the wrong axis. Then just set both back to 2.0 when you're done mapping.

---

### Post by roblloyd on 2009-04-02
> **damis648 said:**
> 

[http://pastebin.ubuntu.com/142490/plain/](http://pastebin.ubuntu.com/142490/plain/)



damis, the link doesn't work, but i think i see what you mean. Playing around with vdrift, it knows that i'm using a wiimote, but it maps the controls to the buttons rather than the sensors. I'll have a play when i get a chance. Cheers

---

### Post by damis648 on 2009-04-02
> **roblloyd said:**
> damis, the link doesn't work, but i think i see what you mean. Playing around with vdrift, it knows that i'm using a wiimote, but it maps the controls to the buttons rather than the sensors. I'll have a play when i get a chance. Cheers

Try [this]("http://pastebin.ubuntu.com/142490/").  (Click view as plain text)

---

