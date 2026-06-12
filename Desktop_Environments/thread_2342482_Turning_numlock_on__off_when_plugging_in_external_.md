---
title: "Turning numlock on / off when plugging in external keyboard"
date: 2016-11-07
forum: Desktop Environments
---

### Post by Chip88 on 2016-11-07
Hi there,

after upgarding last weekend from 14.04 LTS to 16.04, I'm trying now to get the numlock turning on automatically when I plug in an external keyboard.
Of course, I found many instructions how to do this.

I did exactly the following:
```
lsusb
``` to find out *idVendor* and *idProduct*[COLOR=#000000][FONT=&amp]:[/FONT][/COLOR]
```
Bus 001 Device 007: ID 04fc:05d8 Sunplus Technology Co., Ltd Wireless keyboard/mouse
```

[COLOR=#000000][FONT=&amp]Then I installed *numlockx* and created a file [/FONT][/COLOR]**25-usbkeyboard.rules**[COLOR=#000000][FONT=&amp] in [/FONT][/COLOR]**/etc/udev/rules.d/**[COLOR=#000000][FONT=&amp]:
[/FONT][/COLOR]```
ACTION=="add", SUBSYSTEM=="input", ATTRS{idProduct}=="05d8", ATTRS{idVendor}=="04fc", RUN+="/usr/local/bin/numlock on", ENV{REMOVE_CMD}="/usr/local/bin/numlock off" 

ENV{ID_VENDOR_ID}=="04fc", ENV{ID_MODEL_ID}=="05d8", ACTION=="remove", RUN+="/usr/local/bin/numlock off'"
```

I also created another file **numlock** in **/usr/local/bin/**:
```
#!/bin/shexport XAUTHORITY=/home/mark/.Xauthority #falls Session-Daten benötigt werden


case "$1" in
  on)
    export DISPLAY=':0.0'; /usr/bin/numlockx on
    ;;
  off)
    export DISPLAY=':0.0'; /usr/bin/numlockx off
    ;;
esac
exit 0

```

[COLOR=#000000][FONT=&amp]Restarted the notebook and got the login screen: Numlock is turned off (LED is off).
[/FONT][/COLOR]Put in the password, logged in and numlock turned on automatically (LED is also on).

**&#8594; But: **When I unplug the USB receiver, **nothing** happens (LED keeps on).
Now, when I am plugging in the USB receiver, the LED turns off for a second and then automatically turns on again.
So it seems to me that the* &#8203;ACTION=="add" *works fine.

[COLOR=#000000][FONT=&amp]But why is the [FONT=Verdana]the[/FONT]* &#8203;ACTION=="remove"* not working correctly?

Thank you in advance about any advices & hints!

Regards,
Chipy
[/FONT][/COLOR]

---

### Post by bra|10n on 2016-11-08
Is there any particular reason you don't always want numlock on ?

---

### Post by Chip88 on 2016-11-08
> **bra|10n said:**
> Is there any particular reason you don't always want numlock on ?

Hey bar|10n,

thank you for your reply.

Yes, there's a simple reason:
At home, I work with an external keyboard, which has a separate numlock. If I would activate it permanently, I am causing the problem that numlock will always be on - also an my internal notebook keyboard. So if I am not working at home and without an external keyboard, the internal numlock will be turned on anyway.

Acutally, I just wanted to avoid this...

---

### Post by CantankRus on 2016-11-08
I don't know how all this works but the last part of your 25-usbkeyboard.rules file seems to have an extra single quote...
```
RUN+="/usr/local/bin/numlock off[COLOR="#FF0000"]'[/COLOR]"
```

---

