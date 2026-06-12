---
title: "play sund when critical battery"
date: 2020-02-08
forum: Desktop Environments
---

### Post by V Boti on 2020-02-08
Can somebody help me with a solution to play sound when xfce power manager critical battery warning pops up?

Thank you

---

### Post by TheFu on 2020-02-08
I have a cron task setup to run this script every 30 minutes:
```
$ more ~/bin/batt-chk.sh 
#!/bin/bash

# Battery 0: Not charging, 100
BATT=$(/usr/bin/acpi  -i |/bin/grep  -v capacity \
|/bin/sed  -e 's/^.*[cC]harging, //g' -e 's/\%.*$//' \
|/bin/sed -e 's/^.*Discharging, //g' -e 's/\%.*$//')

# echo \"$BATT\"

if [ 50 -ge $BATT ] ; then
   /usr/bin/wall  "==INFO== Low battery: $BATT"
   /usr/bin/mpv  /usr/share/sounds/ubuntu/stereo/phone-incoming-call.ogg
else
   echo "==INFO== Battery Level: $BATT %"
fi
```

---

