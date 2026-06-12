---
title: "Firefox sound output device"
date: 2009-02-26
forum: Desktop Environments
---

### Post by Revo___ on 2009-02-26
Hello everybody,

currently I am using an USB Device as the sound output device.
All System sounds or those from Rythmbox etc. are played well.

Only those sound that comes from firefox (Flash Player) is played by the System sound device and not by the USB one.

I've asked google for help and found out a command that lists the sound cards.
When I enter
```
cat /proc/asound/cards
```
the following lines appear:
```
0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf3500000 irq 22
 1 [default        ]: USB-Audio - NX-U02          
                      YAMAHA CORPORATION               NX-U02   at usb-0
```

When I enter
```
asoundconf list
```
the following text appears:
```
Names of available sound cards:
Intel
default

```

I tried
```
asoundconf set-default-card default
```
and restarted firefox but that did not help.

Can you help me with that?
What else do you need to know?

Greetings
Revo

---

### Post by Revo___ on 2009-02-26
Sorry.
I accedantly posted this into the wrong topic.
That was changed so that this post is:

--- CLOSED ---

---

