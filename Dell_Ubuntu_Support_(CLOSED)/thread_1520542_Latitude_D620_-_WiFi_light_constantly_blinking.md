---
title: "Latitude D620 - WiFi light constantly blinking"
date: 2010-06-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by LinuxChobo on 2010-06-29
I just installed 10.04 on my D620 with an Intel pro/wireless 3945ABG card and everything works beautifully except that the small WiFi LED icon near the hinge of the screen keeps blinking as opposed to staying lit the entire time.

This is more of an annoyance as opposed to a technical problem but I was wondering if anyone's encountered this before. A google search really didn't provide much help.

---

### Post by metalf8801 on 2010-07-01
> **LinuxChobo said:**
> I just installed 10.04 on my D620 with an Intel pro/wireless 3945ABG card and everything works beautifully except that the small WiFi LED icon near the hinge of the screen keeps blinking as opposed to staying lit the entire time.

This is more of an annoyance as opposed to a technical problem but I was wondering if anyone's encountered this before. A google search really didn't provide much help.

I'm using the same card and the light is blinking guess I didn't really notice it till now but yeah it is kind of annoying

---

### Post by LinuxChobo on 2010-07-01
Is it something to do with the driver? Heck i'd be happy if the light wasn't even on. I guess I'll do some more research to see what causes this.

---

### Post by LinuxChobo on 2010-07-02
metalf8801 - I found this on the forums and it appears to work for all intel wifi cards

```

#!/bin/sh

if [ "$IFACE" = "wlan0" ]; then
    for direc in /sys/class/leds/ath9k-phy0::rx
    do
        echo none > $direc/trigger
        # never trigger blinking for RX
    done
    
    for direc in /sys/class/leds/ath9k-phy0::radio
    do
        echo none > $direc/trigger
        # never trigger blinking for radio
    done

    for direc in /sys/class/leds/ath9k-phy0::assoc
    do
        echo phy0assoc > $direc/trigger
        # do trigger blinking during association
    done
    
    for direc in /sys/class/leds/ath9k-phy0::tx
    do
        echo phy0assoc > $direc/trigger
        # never trigger blinking for TX
    done
fi

```Here's the link to the original post that I found this on - [http://georgia.ubuntuforums.org/showthread.php?t=966511&page=9](http://georgia.ubuntuforums.org/showthread.php?t=966511&page=9)

It also has extra code to run the script. I haven't had a chance to try it out since I'm at work right now :(

---

### Post by ghosh_rajk on 2010-09-10
Please check out the following link,
[http://alexcabal.com/stop-blinking-intel-wifi-led-on-ubuntu-karmic/](http://alexcabal.com/stop-blinking-intel-wifi-led-on-ubuntu-karmic/)
 
Might be helpful.

---

