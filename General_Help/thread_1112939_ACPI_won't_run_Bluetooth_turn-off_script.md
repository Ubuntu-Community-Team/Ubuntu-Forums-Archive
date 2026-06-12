---
title: "ACPI won't run Bluetooth turn-off script"
date: 2009-04-01
forum: General Help
---

### Post by PacShady on 2009-04-01
Hey all

Having trouble getting a powersave script to run properly with ACPI. I'm trying to get it to run "/etc/init.d/bluetooth stop" (and variants such as starting with a period and space, starting with 'sh', running from an entirely separate script with these commands as well, etc). If I run my script manually, it runs everything the way it's supposed to. If I run /etc/acpi/power.sh manually, it runs how it's supposed to. But when I try to unplug and plug my laptop back in, it doesn't run that particular command. Everything else in the script runs fine, tested by running aplay before and after the bluetooth script.

Is there something about how ACPI executes commands in scripts that stops this from working properly? Any ideas on how I can fix it? Here's the script I'm trying to run when the laptop is unplugged. Google is no help :(


```
#!/bin/sh

. /etc/init.d/bluetooth stop
hciconfig hci0 down
sleep 1
rmmod btusb

hal-disable-polling --device /dev/cdrom
```

---

### Post by sdennie on 2009-04-01
Your script looks fine but the place you are putting it hasn't worked since Gutsy.  You instead need to put it in /etc/pm/power.d.  In which case you'll also need to wrap it to detect which action is happening.  Try:

```

#!/bin/sh

if on_ac_power ; then
    hal-disable-polling --device /dev/cdrom
    
    modprobe btusb

    hciconfig hci0 up
    /etc/init.d/bluetooth start
else
    /etc/init.d/bluetooth stop
    hciconfig hci0 down
    sleep 1
    rmmod btusb

    hal-disable-polling --device /dev/cdrom
fi

```

That's the general idea.  You may need some modifications to get it to actually work.  I do lots of stuff like this on my machine.  This thread may give you some ideas: [ HOWTO: XPS m1330 power savings]("http://ubuntuforums.org/showthread.php?t=847773")

---

### Post by PacShady on 2009-04-01
Thanks, that fixed it :) Also took a few of your ideas for further power saving, my laptop is a guzzler :s max of like 2 hours even after all the power saving stuff.

---

