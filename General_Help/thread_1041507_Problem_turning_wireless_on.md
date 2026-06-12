---
title: "Problem turning wireless on"
date: 2009-01-16
forum: General Help
---

### Post by mprogrammer on 2009-01-16
Hi everyone,

I just installed ubuntu on my hp notebook. It seems working alright but the problem is I can't turn the wireless on using the touch button I don't know if that's because of missing driver or something??

Anyway the button lights red when the wireless is off and in windows when I press it it turns blue and it turns the wireless card on. I don't know what to do to fix that.

Help me please and thanks in advance...

---

### Post by orlox on 2009-01-16
First we should know the model of your wireless card. Run the command
> 
lspci -v

on a terminal and put the output here.

Also, you should specify the version of ubuntu you are using (8.10 probably)...

---

### Post by mprogrammer on 2009-01-16
it's a broadcom something. I'm running windows right now so how I can exactly know what kind it is??

---

### Post by mprogrammer on 2009-01-16
anyone????

---

### Post by orlox on 2009-01-16
Knowing its a broadcom should be enough. I have a broadcom and to enable it I install the b43-fwcutter package. This one extracts firmware that is neccesary to use your wireless card (It doesnt come by default because of some legal issues I believe...).

If you have intrepid, then you can do this by using a wired connection. Go to system->administration->Synaptic package manager. Open configuration->repositories and mark all the tickets in the first window that appears. Close that window and press reload, then, search for b43-fwcutter, install it and follow the instructions. After restarting your computer, wireless should work.

A small comment about the wireless light. It wont be blue unless the card can correctly communicate with the OS. Not being able to enable the wireless with the button doesnt mean the button doesnt work...

---

### Post by mprogrammer on 2009-01-16
alright, problem is I can't even use the wired connection but that's a router problem cuz even in windows I need to disable and enable the wired connection. How do I do that in linux I mean where is the thing that's equivalent to device management in windows??

---

### Post by orlox on 2009-01-16
What do you mean by disable-enable the wired connection??

I guess you can do something like what you say using the notification icon. In ubuntu there should be a notification icon for the network (if its disabled, probably it looks like a monitor with a cross). To disable it, press the right button, and choose disable networking. If you do it again, you will see the option to enable the networking.

---

### Post by mprogrammer on 2009-01-16
I tried that but I was trying do something like uninstall the driver for the wired connection and then reinstall it. I know this might be harder in linux than in windows but it might be my only way to connect!!!!

---

### Post by mprogrammer on 2009-01-16
never mind about the wired connection I'm on it now but I'm still having problems with the wireless.

---

### Post by orlox on 2009-01-16
Did you installed b43-fwcutter as mentioned above???

---

### Post by mprogrammer on 2009-01-16
I just did and restarted the system but not only wireless is still not working wired connection stopped working too haha. that's a mess I'm using vista right now. I'm pretty much a beginner so I have a lot to learn.

---

### Post by mprogrammer on 2009-01-16
Yes I did!!

---

### Post by orlox on 2009-01-16
Well, id try two things...

First, be sure you have a broadcom. Put the output of these two commands (run them on a terminal Applications->Accesories->Terminal):
```

lspci -v | grep Broadcom
lspci -v | grep Network

```
Also, to see if effectively youre using the broadcom driver, check under System->Administration->Hardware controllers (Not sure if this is exactly the name, my ubuntu is in spanish), and check if the broadcom driver is enabled

---

### Post by orlox on 2009-01-16
Another comment, in the hardware controller app, you should see two entries for broadcom. If one is enabled, and still you dont have wirelless, disable it and try with the other one.

Also, its very weird that you dont have wired network. Are you sure it appears as enabled in the notification icon???

---

### Post by mprogrammer on 2009-01-16
03:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)

that's for the first line so I guess I do have broadcom. and when I go to the hardware drivers it only lists one driver and it says enabled but not in use and it doesn't say broadcom it only says w
and I tried to to disable and enable it again and restarted the system but it didn't work still.

---

