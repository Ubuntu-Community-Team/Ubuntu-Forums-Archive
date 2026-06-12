---
title: "disable touchpad while usb mouse is plugged in"
date: 2009-05-09
forum: General Help
---

### Post by ultimatebuster on 2009-05-09
How do you disable an Alps touchpad (dell inspiron 1525) while having a USB mouse plugged in?

---

### Post by AndThenWhat on 2009-05-09
I found how on this website:
[http://www.linuxine.com/2008/06/how-to-disable-touchpad-in-ubuntu.html](http://www.linuxine.com/2008/06/how-to-disable-touchpad-in-ubuntu.html)

Apparently edit your xorg configuration file:

1. Alt+F2
2. Type "gksu gedit /etc/X11/xorg.conf" (without the quotes)
3. Find the line that says Section “InputDevice”
4. Under that section add a line that reads: Option “SHMConfig” “on”
5. Save and close that file

Now to turn it off:

1. Alt+F2
2. Type "synclient touchpadoff=1"
3. Hit enter and you're done

To turn it back on:

1. Alt+F2
2. Type "synclient touchpadoff=0"
3. Hit enter and you're done

---

### Post by Tipped OuT on 2009-05-09
Don't see the reason to disable it, unless your touch pad is defected or something. I use Alps Touch Pad too :).

---

### Post by djurny on 2009-05-10
synclient does need shm to be enabled, i didnt manage to get that thing to be enabled though..
xinput is another approach that should also work:

```

#!/bin/sh
DISPLAY=:0

id=$(xinput --list|sed -ne "s/.*ALPS.*id=\([0-9]\+\).*/\1/p")
prop=$(xinput --list-props $id|sed -ne "s/.*Tap Action (\([0-9]\+\)).*/\1/p")

xinput set-int-prop $id $prop 8 0 0 0 0 0 0 0

# EOF

```

add that piece of script to whenever mouse is plugged in and you should be ready to go :)

please note that this will only disable tapping on the 1525 touchpad (which i find VERY annoying..)

---

### Post by ultimatebuster on 2009-05-11
turning it on and off is very annoying. I might accidentally tap the touchpad while typing and i'll start typing at a completely different location, which is very annoying.

---

### Post by xMarine73 on 2009-05-14
Script to turn it on and off automatically when usb mouse is plugged in.

You will need to change the included script in one place to match your configuration. Documentation is included in the script with the steps to do that.  I also included the setting to delay the touchpad while typing when the TP is active.

Make the script executable.  Add it to your start-up applications.

Hope this helps.

---

### Post by mom2twinzz on 2010-06-01
Thank you for the script.  I tweaked it a bit for my own use, as   I tend to use the USB mouse for the most part all the time.  It worked great.  I am gonna try it for my WACOM Bamboo next. :)

---

### Post by j_patterson on 2010-10-05
Ya my touchpad gets in the way all the time, and in general xmarine's script worked but i ran into some problems with it.

At least on my computer, when it doesn't find the mouse in xinput list it configures the touchpad and starts syndaemon, but it does that over and over again (every 2 seconds) and i end up with hundrends of instances of syndaemon running and that eventuallly crashes my computer...  I can avoid this by sticking "killall syndaemon" right above the line "syndaemon -i 3 -d;", but i guess that means that syndaemon is being turned on and off every 2 or so seconds.  Any suggesions on a more efficient way to get around this problem?

Also I have a mouse at work and one at home(different models), so the way this is written it only works for one, i thought changing the line to :

if [xinput list 'Microsoft Basic Optical Mouse'] || [xinput list 'Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)'];
then

would make it recognize either, but that didn't work.  I am not that experienced in bash scripting, anyone know the correct way to say recoginize either mouse?


Thanks a lot!

---

### Post by pefrase on 2010-10-24
> **j_patterson said:**
> 
At least on my computer, when it doesn't find the mouse in xinput list it configures the touchpad and starts syndaemon, but it does that over and over again (every 2 seconds) and i end up with hundrends of instances of syndaemon running and that eventuallly crashes my computer...  I can avoid this by sticking "killall syndaemon" right above the line "syndaemon -i 3 -d;", but i guess that means that syndaemon is being turned on and off every 2 or so seconds.  Any suggesions on a more efficient way to get around this problem?

I had exactly the same problem and initially I came up with the same solution as you. It seemed to work fine, but I was also unhappy with the constant stopping and starting of syndaemon. Then I changed the line "syndaemon -i 3 -d;" to:

```
if ! ps -A | grep syndaemon; then syndaemon -i 3 -d; fi;
```

That seems to work and doesn't constantly stop/start syndaemon. But I'm no bash expert either, so there's probably a better way to do this.

---

### Post by rava_sd on 2010-10-25
Hey, I think it is great that you get the scripts working, but again, it would be nice to have this option in the general mouse settings. I dual boot with Windows XP and despite being so old, it has the option to automatically disable the touchpad if USB mouse is present. I think this should become a general option for everyone in Ubuntu as well... give users the choice. Scripts and editing configurations like that is too risky for me, so I'll wait for easier and safer methods to get it done. :P

I am not quite sure how to officially suggest this for Ubuntu...

Thanks.

EDIT: There seems to be an almost three year old suggestion for this here: [http://brainstorm.ubuntu.com/idea/554/](http://brainstorm.ubuntu.com/idea/554/)

---

