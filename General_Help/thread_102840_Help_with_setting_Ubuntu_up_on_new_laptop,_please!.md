---
title: "Help with setting Ubuntu up on new laptop, please!"
date: 2005-12-12
forum: General Help
---

### Post by climhazzard85 on 2005-12-12
Hi, I just got purchased a new Gateway notebook from best buy (6023GP), primarily to install linux to mess around with it.  I am currently using the bootable CD to test things out, and ubuntu loads perfectly but there are a few problems.

- The mouse pointer movement is waaaaaaaay too fast, and adjusting it doesn't help

- If i use my Function laptop keys..as in volume and brightness, the pointer dissapears.  

I realise that this isn't a real install of linux, but I figure if I can't get these problems fixed I might have to look at another distro.  These problems should be fixable though, any help would be appreciated.  Thanks!

---

### Post by matthewv on 2005-12-12
Sounds like an issue with the mouse or trackpad drivers. I had teh same prog once on my desktop but it dissappeared after a reboot (sounds like windows;))

---

### Post by climhazzard85 on 2005-12-12
[QUOTE=matthewv]Sounds like an issue with the mouse or trackpad drivers. I had teh same prog once on my desktop but it dissappeared after a reboot (sounds like windows;))[/QUOTE]

Well the mouse dissapearing problem is gone if I open a program or have a program open already besides the desktop.  Now I just need to slow the mouse down...there has to be an easy fix for that?

---

### Post by 23meg on 2005-12-12
Are you sure that *increasing* the sensitivity in System / Preferences / Mouse doesn't help?

---

### Post by climhazzard85 on 2005-12-12
[QUOTE=23meg]Are you sure that *increasing* the sensitivity in System / Preferences / Mouse doesn't help?[/QUOTE]

Helps a little bit, but it's still too fast for my liking.

---

### Post by 23meg on 2005-12-12
Is this with the internal pointing device(s) or a mouse, or all? Does decreasing acceleration not help?

---

### Post by climhazzard85 on 2005-12-12
[QUOTE=23meg]Is this with the internal pointing device(s) or a mouse, or all? Does decreasing acceleration not help?[/QUOTE]

It is a trackpad, I decreased acceleration all the way already.  Weird stuff.

---

### Post by 23meg on 2005-12-12
In the InputDevice section of your xorg.conf file that corresponds to your trackpad, try entering this line ```
Option "Resolution" "256"
```
Experiment with the value, restarting X with Ctrl+Alt+Backspace each time and see if it affects speed.

---

### Post by climhazzard85 on 2005-12-13
Thanks, I will do that as soon as I get Ubuntu set up on a real partition, working on that now.  Any advice for getting wireless set up later?  The Gateway has a built in wireless card, but Ubuntu didn't recognize it automatically.

---

### Post by climhazzard85 on 2005-12-13
I have been trying that line, and unfortunately nothing seems to change the trackpad movement at all.  Is it possible that I should change the driver from synaptics (sp?) to something else?

---

### Post by 23meg on 2005-12-13
If it's a Synaptics device, add the following to your InputDevice section that corresponds to it:

```
	Option "MinSpeed" "0.65"
	Option "MaxSpeed" "0.85"
	Option "AccelFactor" "0.025"
```
These are the values that I use. Tweak them to your liking.

---

