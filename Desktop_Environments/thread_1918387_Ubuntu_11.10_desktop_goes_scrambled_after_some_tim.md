---
title: "Ubuntu 11.10 desktop goes scrambled after some time"
date: 2012-01-31
forum: Desktop Environments
---

### Post by dleclair on 2012-01-31
I'm running Ubuntu 11.10 on an IBM ThinkCenter computer. What I'm finding is repeatedly after some time of use, the video rendering on my desktop goes all scrambled and I can't even read any of the text on the screen.

I need to restart machine for it to back to normal for a while but inevitably it just goes scrambled again after some time.

I've attached a screenshot of what it looks like when it goes scrambled.

I'm not sure where to even start with this one. Can anyone help?

Thanks.

---

### Post by UltimateCat on 2012-01-31
Did you open your terminal and request this command?

```
ifconfig

```

Or does it open on it's own?  If it opens on it's own it might be your graphic card.

You can google your graphics card and do research on it and a driver for it.

I had a similar problem with my graphics card after a series of updates.

Check on your driver and see that it is working properly by going to
SYSTEM>ADMINISTRATION> Hardware Drivers

[http://help.ubuntu.com/community](http://help.ubuntu.com/community)

[http://ubuntu-manual.org/](http://ubuntu-manual.org/)

[http://ubuntuforums.org/showthread.php?t=1585060](http://ubuntuforums.org/showthread.php?t=1585060)

Hope this helps

---

### Post by dleclair on 2012-02-01
To your first question, yes, the terminal window on the screen shot is showing the output from ifconfig however it doesn't happen automatically. I manually opened the window and ran ifconfig myself. If you were finding that this was happening automatically for you then I can't see how this would be in any way related to the video driver.

I just ran lspci and I can see that this machine is using Intel integrated 82945G/GZ chip set. As you can probably tell by now this machine is new to me so I'm learning it's configuration as I go.

I guess I'll do some searches to see if there are any known problems with the 82945G/GZ adapter with Ubuntu 11.10.

Any other thoughts or suggestions are welcome!

---

### Post by quirino77 on 2012-02-08
Isn't it a hardware problem? (memory or graphic card).

---

