---
title: "Capturing SMART data values"
date: 2011-07-16
forum: Desktop Environments
---

### Post by gen_x on 2011-07-16
I want to capture the temperature value in the SS and output that to Conky, is there a way of doing this without installing any other hard drive monitoring utility?

-thanks in advance

[[IMG]http://img810.imageshack.us/img810/5557/screenshot250gbharddisk.png[/IMG]](http://img810.imageshack.us/i/screenshot250gbharddisk.png/)

---

### Post by georgemc on 2011-07-16
Looks like you allready have "smartmontools" installed.  If not use your
favorite method to install them.

This is what I did.

To make this work as a normal user I set the sticky bit on smartctl so it runs as root;  Yes I understand
that it gets overwritten whenever smartctl is updated, and I understand the possible security 
implications with setting the sticky bit.

```

sudo chmod 4755 /usr/sbin/smartctl

```I made a script named "SMART_TEMP" in my ~/bin directory.  Its easy to test, just run it with a device name:
I.e.
/home/user_name_here/bin/SMART_TEMP sda

the output would look like "37", or whatever the current temp of the HDD is.

I added the script in the appropriate place to my .conkyrc file.  See entries below.

Of course replace "user_name_here" appropriately.

Hope this helps.

George


SMART_TEMP script

```

#!/bin/bash
#
# Get HD temp once a minute - for conky
# invoke with the device sda or sdb and it returns the temp
# SMART_TEMP sda|sdb
#
# Access requirements:
# /usr/sbin/smartctl must have the sticky bit set
# sudo chmod 4755 /usr/sbin/smartctl

DEVICE="$1"


SD=`smartctl -a /dev/$DEVICE|egrep Temperature_Celsius|tr -s " "|cut -f 10 -d " "`
echo $SD

```The DOTconkyrc entries:

```

S.M.A.R.T. Temp /dev/sda ${execi 60 /home/user_name_here/bin/SMART_TEMP sda} ${goto 170}C
S.M.A.R.T. Temp /dev/sdb ${execi 60 /home/user_name_here/bin/SMART_TEMP sdb} ${goto 170}C

```

---

