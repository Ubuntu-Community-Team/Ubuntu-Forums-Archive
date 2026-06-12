---
title: "Terminal (shell) command for USB port"
date: 2009-04-23
forum: General Help
---

### Post by fasti on 2009-04-23
Shalom and Hi to everybody,

I'm looking for an Ubuntu-Terminal (shell) command that would turn off ONE of the USB ports in my PC, and another command that would revive it (turn it back on).
Anything that shuts the power down in the socket (in one port only) would be great.

Thanks in advance.

---

### Post by kerry_s on 2009-04-23
i don't think you can do just 1 port, it's all 1 system "usbcore". 
what device is at the end of that port that you want to restart?

anyways it's> **sudo rmmod usbcore** <to remove
or
**sudo modprobe -r usbcore**

to restart it> **sudo modprobe usbcore**

it's better to do the device if you can, usbcore will take out all usb's. 
i use it when i suspend, cause it won't suspend with my usb wifi connected.

---

### Post by fasti on 2009-04-24
trying "sudo modprobe -r usbcore" I got:

        FATAL: Module usbcore is in use.

and trying "sudo rmmod usbcore" I got:

        ERROR: Module usbcore is in use by rt73usb,rt2x00usb,xpad,usbhid,uhci_hcd,ehci_hcd

am I supposed to kill some proccess before rmmmoding the usbcore?

---

### Post by kerry_s on 2009-04-24
what are you trying to do? why do you need to mess with the usb at all?

---

### Post by fasti on 2009-04-24
My wifi connection drops once a day or so,
and it won't re-connect unless I unplug+replug the usb dongle (wifi adapter).

I would like to make the computer think I've unplugged+replugged it, by shell command (and run it periodically by cron, when the connection drops).



so, what else do I need to do before "sudo modprobe -r usbcore" to make it work?
(so it won't say "ERROR: Module usbcore is in use by rt73usb,rt2x00usb,xpad,usbhid,uhci_hcd,ehci_hcd").

---

### Post by kerry_s on 2009-04-24
then you only need to do the wifi drivers.

[B]sudo modprobe -r rt73usb rt2x00usb
sudo modprobe rt73usb rt2x00usb[/B]
or
you could try restarting it:
[B]sudo ifconfig ra0 down
sudo ifconfig ra0 up[/B]
or
try changing your router beacon period most are set to 60 to 100 secs, but the connection times out around 30. i set mine to 25 and don't have dropped connections anymore.
also look at what other connections are on and use a different channel than every 1 else.
i use wicd so it's easy for me, you can use "sudo iwlist ra0 scan".

---

### Post by Skawt_S on 2011-06-04
Hey, I have the same problem with my external hard drive, do these commands do all the ports at once? or is there a way to detect which port my hard drive is plugged in, I have to un-plug it and plug it back in every time I restart my computer. I think it has something to do with it not seeing the hard drive turn on if it is already on it just does not notice it there? or something like that haha im still a little new..

Next thing I am wondering is if I can put these into a Perl script for start up or is there an easier way to do this??

---

