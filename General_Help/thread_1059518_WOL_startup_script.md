---
title: "WOL startup script?"
date: 2009-02-03
forum: General Help
---

### Post by BassKozz on 2009-02-03
My NAS powers off everynight to save electricity thanks to a little script I created (see: [Advanced Shutdown Script - Powersaving]("http://basskozz.wordpress.com/2009/02/03/advanced-shutdown-script-powersaving/")).
But now every-morning, before I power on my desktop I need to boot up my NAS 1st :(, and I am lazy, so the energy exerted to push the power button on my NAS box can be better used else where :p

So I created a little script that will wake up my NAS box and mount the share(s):
```
#!/bin/sh
###
# 2/3/09
# wake-NAS.sh
# Wake-On-Lan wake NAS Script
###

echo "Begin: $(date)" >> /home/user/scripts/wake-NAS.log
wakeonlan AA:BB:CC:DD:EE:FF >> /home/user/scripts/wake-NAS.log
sleep 5m
mount -a >> /home/user/scripts/wake-NAS.log
echo "End  : $(date)" >> /home/user/scripts/wake-NAS.log

```

So how can I get this script to run everytime my desktop boots? Where do I need to put it?  I would prefer if this was one of the very first scripts to run on bootup, because it needs to wait (sleep) for 5minutes while the NAS boots before it tries to mount it.
There is 1 MAJOR factor that plays into this is that this script MUST be run as root (sudo) because the 'mount -a' command won't run otherwise.

If anyone knows of a better way of going about this, I am all ears [IMG]http://i4.photobucket.com/albums/y105/basskozz/ears-smile-big.gif[/IMG]

**EDIT**: after a quick google search I did find this: [Startup Scripts]("http://azitech.wordpress.com/2007/11/23/startup-scripts/")
Which explains you need to move the script to /etc/init.d/ and then run 'update-rc.d FOO defaults' (where "FOO" is the script's name), but I am still unclear as to whether or not this will run the script as root (sudo) in order to 'mount -a'?

---

### Post by BassKozz on 2009-02-04
**Update**:
So I put this script in /etc/init.d/ and ran 'update-rc.d wake-NAS.sh defaults' and rebooted, and it worked :D

However, there are two problems:
[list=1]
[*]It caused my bootup time to be +5minutes, due to the line "sleep 5m", I figured it would just run the script in the background on bootup and not holdup the boot, but that's not the case...
Is there a way to get this to run in the background so it doesn't hold up my bootup times?
Or maybe I could make the "mount -a" a separate script that runs after the machine is fully booted (i.e. System>Preferences>Sessions).
[*]It runs at shutdown as well, which is pointless, I don't want to wake my NAS when I am shutting down, nore do I want to mount my shares (mount -a) :(
[/list]
Any idea's?

---

### Post by Dougie187 on 2009-02-04
Not sure if this helps, but it's worth a shot.

[http://ubuntuforums.org/showthread.php?t=571322](http://ubuntuforums.org/showthread.php?t=571322)

---

### Post by BassKozz on 2009-02-06
> **Dougie187 said:**
> Not sure if this helps, but it's worth a shot.

[http://ubuntuforums.org/showthread.php?t=571322](http://ubuntuforums.org/showthread.php?t=571322)

nope :(

---

