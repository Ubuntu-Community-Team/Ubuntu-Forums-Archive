---
title: "xscreensaver not turning off monitor"
date: 2005-11-02
forum: Desktop Environments
---

### Post by Yoda_Oz on 2005-11-02
hi,
when i type into a terminal "xset dpms force off" it switches off my laptop monitor.
however xscreensaver will not power off my monitor at all even when the advanced power management features are all turned on. ive even set to turn the monitor off after 1 minute but it didnt work!
is this a bug?

---

### Post by jebc4 on 2005-11-03
Just wanted to jump in with a me too.

Investigating now.

Toshiba Tecra M4
Centrino w/ Nvidia 6200 Go 64m

Also running with RandR for tablet rotating (don't know if that makes a difference).

---

### Post by Yoda_Oz on 2005-11-04
any lucK?

still having the problem?

---

### Post by jebc4 on 2005-11-04
(Sorry new laptop, so busy)

I have set DPMS timeouts in xorg.conf, the default XScreenSaver file that is used in gdm, and my ~/.xscreensaver .

Alas, I have not left the laptop idle for 10 mins ;) -- but the screen went blank in gdm after 10 mins (I couldn't wait another min to see if it shut off -- sorry it was late and I wanted sleep).  If it works I will post my changes.

On a side note, if I do "xset dpms force off" the screen does turn off, but it will not come back on with mouse or keys.  I read that this could be a bug (nvidia?), and a possible work around is to hit "Ctl+Alt+F2" then "Alt+F7" -- basically switching out of X and back in.  Will test this later.

---

### Post by Yoda_Oz on 2005-11-07
ive discovered that my monitor switches off if the computer is left alone for the desired time but only if i dont close the lid. i can let it turn off and then close the lid but if i close the lid first before the monitor turns off then nothing will happen.
is there a bug in one of the acpi scripts? which one do you think?

---

### Post by jrib on 2005-11-07
I have been having similar problems.  I haven't had the time to experiment with what values for the timeout work or not.  It seems to depend on the combined settings for screensaver timeout, cycle screensaver, and turn off monitor (and possibly lock screen).  I can input some values that will NEVER turn off the monitor and just keep the screensaver on for hours, while others work just fine.  Like I said I haven't had time to experiment and once I found one that worked and was close to what I wanted I just left it.  But there definitely seems to be a problem.

Currently, I have "blank after=8", "cycle after=3", "Turn off monitor=15" (other power management settins are 0 and "lock screen" is 1) which works fine.  I believe that my previous setting were the same except that turn off monitor was "14", so the screensaver was cycling and it was also turning off monitor at minute 14 (that was my theory as to why it was failing).  

I'm not sure if this is the same problem that is being described here....  If it is, we may want to post exactly what settings are failing for everyone, and also try the time settings we know work on mine and see if it works on everyone elses computer.  That way we may be able to come to a conclusion about what settings cause it to fail and which don't (trying several settings on one's own computer would be very time consuming which is why I haven't been able to do it myself).

---

### Post by Yoda_Oz on 2005-11-07
well i dont actually allow the screensaver to run at all. i hate screensavers.

the values i have in power management are:
standby after 5 mins (how long til the monitor goes black)
suspend after 5 mins (how long til the monitor goes into power-saving mode)
shutdown after 5 mins (how long til the monitor turns off)

im pretty sure the first 2 dont do anything though because my monitor just turns off after 5 mins anyway... if i leave the lid up, that is!

---

### Post by Yoda_Oz on 2005-11-07
i just restarted my computer and the monitor power off doesnt work now. only if i do the manual xset dpms force off thing, then it works.
i just dont understand whats going on!

---

### Post by WijbrandSchaap on 2005-11-09
Had the same problem here, using nvidia GForce 5700 LE and iiyama lcd-monitor. 
Just edited the ./xscreensaver file and everything runs smooth now. Monitor turns of and on as i please...

---

### Post by NicP on 2005-11-17
I'm having a simmilar problem, my monitor goes blank but does not actually turn off. xset dpms force off blanks the screen but the backlight is still clearly on. The monitor used to turn off before i started changing things in xorg.conf (made tv out work). Any ideas how to regain the functionality of turning the monitor off?

---

### Post by Yoda_Oz on 2005-11-17
make sure in your monitor section of the xorg.conf that you have:

option "dpms" "true"

in there somewhere.

---

### Post by NicP on 2005-11-19
[QUOTE=Yoda_Oz]make sure in your monitor section of the xorg.conf that you have:

option "dpms" "true"

in there somewhere.[/QUOTE]


Champion! Thanks! :)

---

### Post by Yoda_Oz on 2005-11-24
bump...

im still having this problem. the actual screensaver works perfectly but the power management features just dont work. its as if xscreensaver is ignoring them.

any idea why?

---

### Post by sn33kyP3t3 on 2005-11-30
I've been trying to figure this one out myself....

Up until about a week ago xsreensaver worked perfectly monitor would go to stand by as expected...

Synaptic updated some modules, acpi, amoung others, then it broke. Now the monitor blanks correctly but never goes into  power saving mode.

Further invesigating shows that dpms works fine manualy using this script:
```

#!/bin/bash
vbetool dpms off
sleep 5
vbetool dpms on

```

I've been trying to find out what proceses xscreensaver calls when it wants to  shut of the monitor, but no luck. 

If it is a simple script, then I can tweak it to use vbetool to do what I want.

Let us know if you find a solution...I'll do the same.

---

