---
title: "[Dapper] Monitor on standby after x time"
date: 2006-07-13
forum: Desktop Environments
---

### Post by HydroDiOxide on 2006-07-13
Using[ this]("http://www.linux.com/howtos/Battery-Powered/powersav.shtml") website I figured out how to get my monitor to go to standby after an x amount of time (on xserver-xgl) using the 

```
$ sudo xset +dpms
$ sudo xset dpms 300
```

Great! However, somehow these settings aren't stored. So everytime I reboot I have to execute these commands, which is almost as annoying as trying to remember to turn off my CRT when I go out of the room.

I would really appreciate if someone would come to my rescue and tell me how I would be able to get this fixed. Both the gnome power manager and the xscreenserver apps don't work and putting the line

```
Option "StandbyTime" "20"
```in my xorg.conf doesn't work either.

---

### Post by rubso on 2006-07-13
i have the same problem >.<" i wish if someone could solve it.

---

### Post by rubso on 2006-07-13
bump

---

### Post by HydroDiOxide on 2006-07-14
Right, I've got an nvidia videocard (6800 series) so maybe someone can verify this is an nvidia driver problem. However I would appreciate a solution (maybe a script that sets the xset time-outs at user login).

---

### Post by rubso on 2006-07-14
HydroDiOxide: we could make it a startup in GNOME.. which means everytime you log in, this command will be executed, how is that?

---

### Post by HydroDiOxide on 2006-07-14
Yup. Shame it doesn't work by using the config files, but a startup script would easy my pain. Tried it already but this n00b couldn't get it right.

---

### Post by HydroDiOxide on 2006-07-14
So, anyone else with an idea how the get the pixelgun to standby? All seems to be set up correctly, at least my /var/log/Xorg.0.log looks good, but the thing won't switch to standby after the set amount of time. Please help, getting desperate here...

---

### Post by ElijahLofgren on 2006-07-14
> **HydroDiOxide said:**
> Using[ this]("http://www.linux.com/howtos/Battery-Powered/powersav.shtml") website I figured out how to get my monitor to go to standby after an x amount of time (on xserver-xgl) using the 

```
$ sudo xset +dpms
$ sudo xset dpms 300
```

Great! However, somehow these settings aren't stored. So everytime I reboot I have to execute these commands
...


I think something like this should work to get the commands executed on every boot:

   1.  Create the file /etc/init.d/xset-dpms.sh with the content:
```

#!/bin/bash
xset +dpms
xset dpms 300

```

   2. Make it executable with the command:

      ```
sudo chmod 775 /etc/init.d/xset-dpms.sh
```

   3. Make it be run on every boot:

      ```
sudo update-rc.d xset-dpms.sh defaults
```

(Someone else helped me find out how to create a startup script like that for my printer: [http://www.elijahlofgren.com/ubuntu/#scx-4521f](http://www.elijahlofgren.com/ubuntu/#scx-4521f) )

Hope this helps. ;)

---

### Post by rubso on 2006-07-14
even that command won't make the monitor go into standby mode.
man, that's getting weird.

---

### Post by rubso on 2006-07-15
guys, xserver-xgl and compiz, is making these problems with the power managment...
i've uninstalled it completey and reconfigured my xorg.conf file, and the power managment is working now :) ..

---

### Post by HydroDiOxide on 2006-07-18
> **rubso said:**
> guys, xserver-xgl and compiz, is making these problems with the power managment...
i've uninstalled it completey and reconfigured my xorg.conf file, and the power managment is working now :) ..

Thought so. So no powermanagemt in combination with with the xgl xserver? How do I get rid of it?

---

### Post by ElijahLofgren on 2006-07-18
> **HydroDiOxide said:**
> Thought so. So no powermanagemt in combination with with the xgl xserver? How do I get rid of it?

A forum search turned up this: [http://ubuntuforums.org/showthread.php?t=203621&highlight=remove+xgl+server](http://ubuntuforums.org/showthread.php?t=203621&highlight=remove+xgl+server)

Hope it helps. ;)

---

### Post by one_stinky_bum on 2006-09-09
So there's no way to get compiz to turn off monitors after some time? I have a blank screen saver, so it looks off, but I wouldn't mind conserving the lamp hours in my laptop.

---

### Post by ijanos on 2006-09-09
hey this dpms thingie is cool :) 
BUT a few seconds (sometimes almost a minute) after my monitor turns off the backlight just come back but the screen remains black (It's a tft). Does anybody have a tip what can do that?

---

### Post by one_stinky_bum on 2006-09-09
Yeah, that's exactly my problem here.

---

### Post by ijanos on 2006-09-10
I got it!

I simply removed the xserver-xorg-air package, reboot and voilá DPMS settings is xorg.conf works fine.

---

### Post by one_stinky_bum on 2006-09-10
does that affect AIGLX or Compiz in any way?

---

### Post by ijanos on 2006-09-10
Oh yes, they wont work after that :D
Seems you have to try another method if you want to keep xgl/compiz.
Maybe you can try *sudo vbetool dpms off* but beware after that you can only turn back your monitor with *sudo vbetool dpms on*

---

### Post by one_stinky_bum on 2006-09-10
Ok, cool... that's what I figured.

I think I'll wait till a compiz-friendly solution comes along.

---

