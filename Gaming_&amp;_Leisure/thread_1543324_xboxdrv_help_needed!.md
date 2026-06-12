---
title: "xboxdrv help needed!"
date: 2010-07-31
forum: Gaming &amp; Leisure
---

### Post by d00derino on 2010-07-31
Hi friends,

After consulting with the gurus over at the XBMC forums, I finally replaced xpad with xboxdrv for my Xbox 360 controlling needs.

The journey wasn't easy, but it grew hair on me chest. 

My last stop before admitting complete and utter victory against the beast that was xboxdrv (and in essence, XBMC), I need some help writing an /etc/rc.local file that will run the commands I require at bootup. 

Here is what I have appended to /etc/rc.local (that I got from a user at XBMC's forums):
```
/usr/local/bin/xboxdrv-daemon.py -v -x /usr/local/bin/xboxdrv -- --deadzone 6000 --dpad-as-button --trigger-as-zaxis -D & /usr/bin/cpufreq-set -d 2000000

exit 0
``` 

I'm no bash guru, nor do I play one on television. I'm not even going to act like I know what that script does. Because while I get the gist of it, I don't understand how the script runs in sudo, and I don't understand the translation between what is in rc.local to commands I'd type in the Terminal. Are they any different?

If so, this is what I need rc.local to do:

[LIST=1]
[*]sudo modprobe uinput
[*]sudo rmmod xpad (I really don't want to blacklist this for some reason)
[*]sudo xboxdrv --deadzone 6000 --dpad-as-button --trigger-as-zaxis -D
[/LIST]

For whatever reason, the rc.local script I got doesn't work on boot up. I think it's either because it doesn't have sudo access, because I need to manually modprobe uinput, or because I can't get xboxdrv-daemon to work on it's own. Is there anyway I can make modprobe uinput permanent?

Also, I know xboxdrv-daemon makes it so that you can get rid of the console while keeping the process alive, but how do you work it? 

Thanks for any and all help. I greatly appreciate it. Many good karmas and Internet cookies to those who help.

---

### Post by 2Karl on 2010-08-03
try adding your script lines to /etc/init.d/local instead.

so 

```
gksudo gedit /etc/init.d/local
```

and add:

```


#!/bin/sh

/usr/local/bin/xboxdrv-daemon.py -v -x /usr/local/bin/xboxdrv -- --deadzone 6000 --dpad-as-button --trigger-as-zaxis -D & /usr/bin/cpufreq-set -d 2000000

exit 0


```

should hopefully do the trick

---

