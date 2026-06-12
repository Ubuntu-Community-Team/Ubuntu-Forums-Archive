---
title: "Disable Dell Bluetooth / Turn Off at Startup"
date: 2009-05-29
forum: General Help
---

### Post by encore2097 on 2009-05-29
Hi,

My ubuntu 9.04 works great on my Dell Vostro 1400, everything works flawlessly! I can turn off bluetooth manually if I right click the Bluetooth icon > Preferences > "General Tab" > Uncheck "Dell Bluetooth Switch" and that will correctly turn off my bluetooth. 

Is there any way to have it unchecked at startup? As I would only like to turn it on when I need to.

-------------------------------------------------------

[SIZE=3]Q: Bluetooth works fine, how do I turn it off (saving power) while still having the option to enable it when I need it?

A: 
Turn _OFF_ bluetooth:
```
sudo /usr/lib/hal/hal-system-smbios --bt 0
```Turn _ON_ bluetooth:
```
sudo /usr/lib/hal/hal-system-smbios --bt 1
```Check bluetooth status:
```
/usr/lib/hal/hal-system-smbios --st_bt ; echo $?
```Append "/usr/lib/hal/hal-system-smbios --bt 0" to /etc/init.d/bluetooth to turn bluetooth off at startup

If you need to use bluetooth, goto: System > Preferences > Bluetooth, this will re-enable Bluetooth.

[SIZE=2]Works perfectly on Dell Vostro 1400[/SIZE][/SIZE]

---

### Post by ghindo on 2009-05-30
If you want, you can disable it altogether in the BIOS.  That's what I've done for my Dell laptop ;)

---

### Post by encore2097 on 2009-05-30
I'd rather not do that because I use it from time to time and it would not be efficient to have to go into the BIOS everytime I need to use it.

---

### Post by Mirages on 2009-05-30
System>Preferences>Startup Applications

uncheck Bluetooth

---

### Post by encore2097 on 2009-05-30
No, disabling the bluetooth-applet from startup just disables the control while leaving my bluetooth on. That is not a solution.

If someone could tell me a terminal command for bluetooth-applet that will let me turn off the "Dell Bluetooth Switch" then i could just add it to a startup script or something. Effectively resolving my issue :)

---

### Post by mcduck on 2009-05-30
Edit /etc/default/bluetooth and change the line "BLUETOOTH_ENABLED=1" to "BLUETOOTH_ENABLED=0"

---

### Post by encore2097 on 2009-05-30
Same issue... 

going through the bluez source right now to figure out how their "killswitch" works... its the only thing that actually turns off the BT module correcetly (light goes off BT app unloads because it is set to "Only when adapter is present")

---

### Post by encore2097 on 2009-05-30
Solved: see first post

---

### Post by davethebald on 2009-05-30
Maybe you can help me.  I veified that bluetooth is on using the command listed above and it returned a "1".  My Dell BT Travel mouse is on and blinking, but the computer (XPS M1330) does not see it in "Device Search".  Any ideas?

Thanks

---

### Post by encore2097 on 2009-05-31
> **davethebald said:**
> Maybe you can help me.  I veified that bluetooth is on using the command listed above and it returned a "1".  My Dell BT Travel mouse is on and blinking, but the computer (XPS M1330) does not see it in "Device Search".  Any ideas?

Thanks

Bluetooth devices do not automatically pair up. Click on the bluetooth icon on the taskbar, and then use the manager or wizard to pair up your device with your computer.

---

### Post by davethebald on 2009-06-01
I have already tried that.  When I use the wizard, the device does not appear in the "Select the device you want to setup" box.  

In fact, my daughter's cell phone (which does show on the search list on my office Thinkpad) does not appear on the list for my ubuntu Dell.  It acts like it is not on, or is not searching, or is not receptive.

Thanks

---

### Post by guyhillyer on 2009-10-22
The prescribed solution, using hal-system-smbios, does not work for me.  I'm using Jaunty on a Dell E6400.  The utility program crashes with a message about "corrupted double-linked list."

However, as necessity is the mother of invention, I script-kiddied my way to a python-based solution.  It's a command line utility that takes one argument "on" or "off".

For what it's worth.

---

### Post by Wollombi on 2009-12-01
The best way I have found in 9.10 is to add the following line to /etc/rc.local
```
rfkill block bluetooth
```

This makes it so that (on my HP DV5t anyway) bluetooth is off when I first boot/login, but I can still turn it back on with the bluetooth applet that is in the notification area by default (if it isn't there you can add it to the panel).  This is exactly what I wanted, so for me, anyway, this is a win. :D

---

### Post by hackel on 2009-12-12
Are you certain that rfkill is actually turning off your bluetooth adaptor (to save power)?  On my Dell, rfkill simply disables the bluetooth software, but the adaptor is still active and the LED remains on.  In order to really disable it, I must run:

smbios-wireless-ctl --bt=0

Unfortunately, since this disables the adaptor entirely, bluetooth-applet disappears since it thinks there is no bluetooth adaptor present.  Basically, bluetooth-applet/HAL needs to support these smbios commands directly.

---

### Post by clevertomato on 2010-01-12
I have a Dell Studio 1555 and want to have bluetooth turned off at startup but still be able to turn it on when I need it. I've read several suggested methods, but I'm not sure which to use for my system.

Can anyone give me a push in the right direction, please?

---

### Post by kolinab on 2010-04-24
> **Wollombi said:**
> The best way I have found in 9.10 is to add the following line to /etc/rc.local
```
rfkill block bluetooth
```

This makes it so that (on my HP DV5t anyway) bluetooth is off when I first boot/login, but I can still turn it back on with the bluetooth applet that is in the notification area by default (if it isn't there you can add it to the panel).  This is exactly what I wanted, so for me, anyway, this is a win. :D

Thanks for posting this solution. It seems to work perfectly with my Thinkpad T60. Panel functionality remains, but bluetooth is off by default after a reboot. Perfect.

---

### Post by mspacek on 2010-05-20
> **Wollombi said:**
> The best way I have found in 9.10 is to add the following line to /etc/rc.local
```
rfkill block bluetooth
```

This makes it so that (on my HP DV5t anyway) bluetooth is off when I first boot/login, but I can still turn it back on with the bluetooth applet that is in the notification area by default (if it isn't there you can add it to the panel).  This is exactly what I wanted, so for me, anyway, this is a win. :D

I can confirm that this also worked for me in Ubuntu 10.04 on my Thinkpad W510. Now, the bluetooth LED on the laptop defaults to off on bootup, and the bluetooth applet reports the same. I can still turn it on and off manually using the applet.

---

### Post by mspacek on 2010-05-22
Ubuntu should really just remember the last radio state by default, for WiFi too. I've made a brainstorm idea advocating this:

[http://brainstorm.ubuntu.com/idea/24893/](http://brainstorm.ubuntu.com/idea/24893/)

Go vote it up!

---

### Post by o1e9 on 2010-06-05
> **Wollombi said:**
> The best way I have found in 9.10 is to add the following line to /etc/rc.local
```
rfkill block bluetooth
```

This makes it so that (on my HP DV5t anyway) bluetooth is off when I first boot/login, but I can still turn it back on with the bluetooth applet that is in the notification area by default (if it isn't there you can add it to the panel).  This is exactly what I wanted, so for me, anyway, this is a win. :D

Thanks! Works for me on Dell XPS1530 / Ubuntu Lucid, bluetooth light is off and applet allows to enable it.

---

### Post by hackel on 2010-06-05
Hmm, on my XPS M1530, "rfkill block bluetooth" does NOT power off the bluetooth adapter nor does the light turn off, it simply disables it, just like the applet icon does.  "smbios-wireless-ctl --st_bt" shows that bluetooth is still enabled.  Also running Lucid, I wonder what could be different?

Do you also have the Dell/Broadcom 355 Bluetooth adaptor (BCM2046)?

---

### Post by bluepicaso on 2010-06-14
```
rfkill block bluetooth
```

Hey thanx a lot this one helped. I have Dell inspiron 1525.
Though i disabled the bluetooth program at startup but my was able to find the connection on my phone as well the light on my lappy was on... Your method really helped :p

---

### Post by BennBuntu on 2010-06-14
Running a thinkpad t410, I installed laptop-mode-tools from repos, then edit /etc/laptop-mode/bluetooth.conf. There's a few other tweaks in there too, with options for on battery / on AC etc.

---

### Post by Fintican on 2010-09-14
I had the same problem with my IBM Z60m but that "rfkill block bluetooth" command worked for me. It looks like for IBMs it works :)

Although It would be great if OS could remember the on/off state of wifi/bluetooth from shut down to start up as proposed. I voted for it!

---

### Post by ellardc on 2011-09-25
> **o1e9 said:**
> Thanks! Works for me on Dell XPS1530 / Ubuntu Lucid, bluetooth light is off and applet allows to enable it.


works for me as well. lenovo x200

---

### Post by arkanabar on 2011-10-11
I'm on a Dell N5110 laptop.  I don't use bluetooth AT ALL.  Right now, I promptly shut off bluetooth with Fewt's [Jupiter 0.0.50 applet]("www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html") upon login, but I'd really like for it never to turn on.  Unfortunately, the BIOS doesn't really allow me to disable bluetooth while leaving wifi enabled.  The OP solution won't work for me, cos Natty doesn't use HAL.  So what should I do?

oh, nota bene:  I'm using lubuntu-desktop, not Unity.

---

### Post by faust99 on 2011-11-23
> **Wollombi said:**
> The best way I have found in 9.10 is to add the following line to /etc/rc.local
```
rfkill block bluetooth
```

This makes it so that (on my HP DV5t anyway) bluetooth is off when I first boot/login, but I can still turn it back on with the bluetooth applet that is in the notification area by default (if it isn't there you can add it to the panel).  This is exactly what I wanted, so for me, anyway, this is a win. :D

Works on Lenovo x201 under oneiric.

Also, for other noobs, the line has to be added before exit0.

---

