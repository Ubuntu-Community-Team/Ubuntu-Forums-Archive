---
title: "Jaunty shut down/restart hang"
date: 2009-05-01
forum: General Help
---

### Post by prem1er on 2009-05-01
When I shutdown or restart Jaunty the progress bar on the shutdown splash screen completes and then the screen goes black with a blinking cursor in the top left corner.  Keyboard is locked.

---

### Post by wersdaluv on 2009-05-01
Happens to me too 
[https://bugs.launchpad.net/ubuntu/+bug/369760](https://bugs.launchpad.net/ubuntu/+bug/369760)

---

### Post by prem1er on 2009-05-01
Thank you.

Tested both 32 bit and 64 bit versions of Ubuntu 9.04.

---

### Post by yurx cherio on 2009-06-28
It has been the problem for me as well. I have Ubuntu 64bit running on Dell Inspiron E1705 (9400).

Somehow my problem is related to my wireless card (I have Intel 3945ABG). Any time I shutdown after bringing down wireless the computer shuts down properly. I even wrote a script for that:

#!/bin/bash
sudo ifconfig wlan0 down
sudo /sbin/shutdown -h now

---

### Post by moster on 2009-06-28
I used to fight with broadcom and netgear wireless devices... It was battle I could not win. In end, I dumped that and bought d-link and all problems vanished.

Point is, all those devices have similar prices, it all depend how lucky you are if you buy and then try it to run under linux.

Now, I have 4 wireless netgear PCI cards, one netgear USB wireless stick and one D-link USB wireles stick an one integrated broadcom card.

I could not even surf normally till I get D-link, now I can crack WEP protection if I want. I do not need to crack it, but point is, that thing work better that I could imagine. There is no drivers, special editing config files... just plug-in.

---

### Post by dynamics on 2009-09-04
Hello...
Nobody seems to be interested in finding a solution to this problem. I too am struggling with this. 
But sometimes... Yes!  'Sometimes' when I 'Log off' first and then shutdown it shuts  down properly.  But if I directly commend to shut down it does not. Then I have to press the power button and force power OFF.

I tried to shutdown from terminal ($su and then $halt ) ... again same problem...

Please help me to sort this out.
Thanks

---

### Post by Lepy on 2009-09-05
I too am experiencing this problem on my mythbuntu installation. 
Last night everything was working quite well. Today, when I came to watch some tv, the screen remained black upon remote key-presses.
Upon reboot, the system gives me a "kinit: No resume image" message and goes into low graphics mode (being my main backend I do not have automatic update enabled), which baffles me the most.
And now, after many unsuccessful attempts to re-enable nvidia driver functionality to the 6800GT, I find a blinking cursor when powering down.

Can anyone offer any help? I know I'm having more than just the restart hang problem, but they all appeared at the same time with absolutely no modification to the system what-so-ever.

---

### Post by oxmosys on 2009-09-06
You can use this workaround to live in peace until the bug get fixed. Copy all this script text into a file named K00killwlan and save it in /etc/rd0.c and /etc/rd6.c with execution permissions (so it gets executed at restart and shutdown request, therefore stopping your wlan card before it stall poweroff) :


```
#!/bin/bash
#
# This file has to go to /etc/rc0.d/ and /etc/rc6.d/
#
#This script kill wlan so it does not prevent computer to shutdown (until the driver is fixed in linux source itself).
#[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/365733](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/365733)

case "$1" in
  stop)
	ifconfig wlan0 down
  ;;
  *)
	exit 0
  ;;
esac

exit 0
```

---

### Post by dynamics on 2009-09-07
Thats cool ...
Thank you :-)

---

### Post by Giggity on 2009-10-11
> **yurx cherio said:**
> It has been the problem for me as well. I have Ubuntu 64bit running on Dell Inspiron E1705 (9400).

Somehow my problem is related to my wireless card (I have Intel 3945ABG). Any time I shutdown after bringing down wireless the computer shuts down properly. I even wrote a script for that:

#!/bin/bash
sudo ifconfig wlan0 down
sudo /sbin/shutdown -h now
Thanks.  That script works for me, and now my laptop shuts down properly!  I did have to remove the first line to get it to work, though.

---

