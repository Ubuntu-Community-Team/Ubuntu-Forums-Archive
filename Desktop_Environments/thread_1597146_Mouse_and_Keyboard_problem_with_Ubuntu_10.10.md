---
title: "Mouse and Keyboard problem with Ubuntu 10.10"
date: 2010-10-15
forum: Desktop Environments
---

### Post by rostamiani on 2010-10-15
Hi
I installed UBUNTU 10.10 64bit yesterday and there is some problems with my mouse and keyboard

1.Sometimies my keyboard is stopped working
2.When I enable Num Lock ,the left button of my mouse disables !

Reconnecting mouse or keyboard fixes the problem

My mouse : A4tech XL-750BK
Keyboard : Microsoft Comfort Curve 2000

Thanks

---

### Post by Actieman on 2010-11-17
Hi,

Ik have the same problem. Sometimes the left mouse button does not respond. The cursor is there and is moving with no problem. The right button is occasionally accepted. Keyboard input also same problem.

I have not tried reconnecting the devices though, will do so! Thanks inadvance .. 

strange but very annoying problem if you have to reboot your system the entire time! Other news .. i REALLY love Maverick Meerkat!

Cheers

---

### Post by rostamiani on 2010-11-17
> **Actieman said:**
> Hi,

Ik have the same problem. Sometimes the left mouse button does not respond. The cursor is there and is moving with no problem. The right button is occasionally accepted. Keyboard input also same problem.

I have not tried reconnecting the devices though, will do so! Thanks inadvance .. 

strange but very annoying problem if you have to reboot your system the entire time! Other news .. i REALLY love Maverick Meerkat!

Cheers
Try reconnecting your mouse instead of restarting the whole system !

---

### Post by Actieman on 2010-11-17
> **rostamiani said:**
> Try reconnecting your mouse instead of restarting the whole system !

As mentioned in my reply "Will do so" :)

I have been thinking and I THINK that it only happens when i'm listening music through Rhythmbox or Amarok. When a song changes I get a fade in and fade out message showing the new song .. i think something is going wrong there .. i'm not sure and it might seem strange but i think it's a graphical problem..

Cheerio!

---

### Post by guilhermejf on 2010-11-20
I also have this kind of problem.
Using Microsoft Wheel Optical mouse and Microsoft WiredKeyboard 600.
I notice that when I press a multimedia key, such as volume, play/pause, or calculator, the left mouse button stops working.
Even if I reconnect the mouse in the same or another USB port, it does not work. If I plug another mouse, the left button also does not work.

---

### Post by sasy360 on 2010-11-22
I've got this problem too with A4tech XL-750BK. very annoying bug and reconnecting the mouse does not solve the problem.

---

### Post by kurumurthy on 2010-11-22
Same problem .........:KS

---

### Post by vanburg on 2010-11-23
Exactly the same problem. After i pressing Play/Pause MM key, usb mouse works as it's left button holds down. Usb keyboard also have problems after that (i can't even alt+tab to opened terminal window). Only Ctrl+Alt+F1 and sudo rmmod usbhid and then replug keyboard helps, or reboot.

Furthermore, the seeking bar in rhythmbox does not seeking.

Maybe it's problem with rhythmbox?

---

### Post by slidersv on 2010-11-27
I had the problem with mouse freezing once in a while on 10.10 x64, and it was solved by installing proprietary display drivers. Check if you have any drivers that could be updated, System > Admin > Additional Drivers.
Or check your display drivers some other way.

P.S.: while installing drivers my system froze :( Nothing worked EXCEPT the mouse... Oh, the irony.

---

### Post by PhilipTheHermit on 2010-11-29
Hi, guys, I had some problems with my mouse on Ubuntu also, and would like to share what I found out.

So, I've just recently installed Ubuntu 10.10, and tonight I  opened up YouTube and played a Bossa Nova clip (the one that was done as some sort of film project).  Suddenly, my mouse's left button and middle buttons stopped working. I ended up having to reboot.  

I tried to repeat the situation, and found out it's kind of random.  Sometimes it happens, sometimes it doesn't.  Later on it occurred when Firefox wasn't even maximized, and I was running a chess game in another window. 

After a while, I was about to try and make it happen again when for some reason I decided to hit the volume button on my keyboard and lower the volume.  Bang!  The mouse stopped working.  At this point no windows were open at ALL.  

Now I had a theory:  My keyboard, a Microsoft Digital Media Keyboard 3000, may be sending something weird over USB.  So I replaced it with a completely standard Dell 104-key keyboard, which plugged into a PS/2 plug instead of USB, and I rebooted. 

The problem was gone.   I haven't had another crash all night, despite trying to create one.  

So, my theory, in a nutshell, is that my keyboard was somehow interfering with my mouse when I hit one of the extra, non-keyboard-standard buttons, and that it was somehow related to the USB system.

The two things I changed were: 1) Switched to a generic keyboard, and 2) switched to putting the keyboard in the PS/2 plug instead of USB.  The result was that the mouse stopped crashing. 

Hope someone finds this useful...

---

### Post by guilhermejf on 2010-12-04
After last update, it got solved! Problem gone. :D
Not shure what it was.

---

### Post by gatordude on 2011-03-14
I recently upgraded to Ubuntu (64 bit) 10.10.  My USB mouse doesnt work at all after boot and I have to reboot and sit there and wiggle my mouse (not sure if I really have to do that but it does seem to help). Sometimes it takes 2 or 3 reboots to get it to work.

Any ideas?

---

### Post by Krytarik on 2011-03-14
> **gatordude said:**
> I recently upgraded to Ubuntu (64 bit) 10.10.  My USB mouse doesnt work at all after boot and I have to reboot and sit there and wiggle my mouse (not sure if I really have to do that but it does seem to help). Sometimes it takes 2 or 3 reboots to get it to work.

Any ideas?
As another workaround you could just "reload" your mouse instead of reboot/relogin. I wrote the script below once, because the mouse wheel of my last mouse sometimes wasn't detected at startup, when the batteries were low.

Script:
```
#!/bin/sh

output1=`gksudo "modprobe -v -r usbhid" | grep rmmod`
output2=`gksudo "modprobe -v usbhid" | grep insmod`

if [ -n "$output1" -a -n "$output2" ]; then
notify-send -i gnome-mouse "USB-HIDs reloaded"
else
notify-send -i error "Reload failed"
fi

exit 0
```Launcher (desktop-file):```

[Desktop Entry]
Name=Reload Mouse
Type=Application
Terminal=false
Name[en_US]=Reload Mouse
Exec=/usr/local/bin/mouse_reload
Icon=gnome-mouse
Categories=GNOME;GTK;System;Settings;
```

---

### Post by gatordude on 2011-03-15
Thanks for the information. But this happens when I boot my pc and come to think of it I dont have control of my keyboard either when it happens so it would be hard for me to run any scripts.

My mouse has a full charge on it when this happens. I read where somebody suggested just unplug the mouse and plug it back in and that worked for me.

I had Ubuntu 9.10 (32bit) installed and never had a problem with my mouse. I did have a problem with my external USB HD's where I would have to from time to time remove both of them and my PC would boot.

I have only had this problem with the 64 bit version of 10.10. Does it exist with the 32 bit version also? I am getting ready to install windows 7 (just cuz i need Office) so I will be reloading Ubuntu back on it. Will probably just reinstall 9.10 on it if this USB problem is in the 32 bit version of 10.10.

---

### Post by Krytarik on 2011-03-15
> **gatordude said:**
> 
I have only had this problem with the 64 bit version of 10.10. Does it exist with the 32 bit version also? I am getting ready to install windows 7 (just cuz i need Office) so I will be reloading Ubuntu back on it. Will probably just reinstall 9.10 on it if this USB problem is in the 32 bit version of 10.10.
AFAIK there is generally no issue with USB on 10.10, at least of what I see in these forums, since I run 10.04. Also, the issue I had was back in Gutsy 7.10, I don't know if it would re-occur in the current version because I switched the mouse and the Ubuntu version at nearly the same time.

---

### Post by new_tolinux on 2011-05-02
I've got a part of the problems described here...

After a random interval (2-48 hours) the ps2-keyboard and mouse stop working.
To try I plugged an usb-keyboard and mouse in, which works without problems (although the "main" keyboard and mouse still don't function).
After a reboot everything works agan, until.... 
To give it a try I left the USB-mouse and keyboard also plugged in and yet I'm typing this from the USB-keyboard because the PS2-keyboard and mouse are simply not responding anymore (which last until I reboot again).

---

### Post by Krytarik on 2011-05-02
@new_tolinux: How about using PS2/USB adapters?
Those were downright thrown after you during the time of transition. ;-)

Also, what version of Ubuntu are running, really 9.04, like your profile states?

Do both of the PS2 input devices stop working simultaneously?

---

### Post by gatordude on 2011-05-02
I forgot about this until my 11.04 update and had issues.

While running 10.10 I had  this issue with the keyboard and mouse. And I ended up having to unplug all of my external USB hd's and that  helped.

---

### Post by new_tolinux on 2011-05-06
> **Krytarik said:**
> @new_tolinux: How about using PS2/USB adapters?
Those were downright thrown after you during the time of transition. ;-)

Also, what version of Ubuntu are running, really 9.04, like your profile states?

Do both of the PS2 input devices stop working simultaneously?
Sorry for my late reaction...

The PS2-keyboard just has a PS2-plug, the mouse (trackball) is connected with an USB-to-PS2-adapter.
Both the PS2-devices stopped working at the same time, yes.

I was running 10.10 x64 (alternate), but since it annoyed me that much I did an upgrade to 11.04 and as it seems the problem has disappeared. The 9.04 message dates from when I registered around here, atm I only have 11.04 and 10.04LTS running on different machines. I'll change that right away.

---

