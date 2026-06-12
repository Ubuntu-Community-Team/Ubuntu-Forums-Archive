---
title: "I want fluxbox to poweroff when I close netbook lid"
date: 2009-03-02
forum: Desktop Environments
---

### Post by SteveNorman on 2009-03-02
Im using fluxbox on a little acer aspire one. Works great but I would like it to power off when I close the lid. I assume a config file needs a good configing, but I dont know which one. Google has failed me. Help a brotha out.

---

### Post by nathand28 on 2009-03-02
Go to System, Preferences, Power Management and change when lid is closed to Shutdown.
You'll have do this in the On Battery Power tab aswell. Go to the General tab and press always display an icon if you want there to always be an icon on the desktop.

---

### Post by SteveNorman on 2009-03-02
Im using fluxbox not gnome, So I dont have the system option. Unless I am missing something here....

---

### Post by nathand28 on 2009-03-02
Im an idiot...
Try installing wmacpi (for acpi power management) or wmibam (for apm power management).

---

### Post by SteveNorman on 2009-03-02
Solved it,
Added gnome-power-manager & to my .fluxbox/startup file.

I knew I was gonna do me some configuring..YEE HAW
```


$ gedit ~/.fluxbox/startupIn the file add gnome-power-manger with a & after it like so:

# Applications you want to run with fluxbox.
# MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN ''&'' AT THE END.
#
# unclutter -idle 2 &
# wmnd &
# wmsmixer -w &
# idesk &
gkrellm &
gnome-power-manager &
```

---

### Post by SteveNorman on 2009-03-02
Thanks Nathand, I will look into those as well so im not mixing gnome with non-gnome apps.

---

### Post by Locutus_of_Borg on 2009-03-02
there are probably applications to do this for you, but if you don't want to download and install unnecessary crap you can do the following:

```
su -i
echo "%wheel ALL=(ALL) NOPASSWD: /sbin/telinit" >> /etc/sudoers

```

then save this script as ~/.lid_state
```

#!/bin/bash

if grep -q closed /proc/acpi/button/lid/LID/state
then
      sudo telinit 0
fi

```
be sure to chmod +x it

then make a cron job to check this every minute or so:
```
 su -i
crontab -u USER_NAME -e
```
and insert
```
*/1 * * * * /home/YOUR_NAME/.lid_state
```

Should work...


edit: make sure you have cron daemon running
su -i
echo "cron" >> /etc/conf.d/local.start

or something to that effect to start it at boot up

---

### Post by pmheinen on 2013-01-30
Inspired by the reply of Locutus_of_Borg:

instead of having a watchdog run by cron, one can use the FLuxbox keys file.

The close lid action generates a key code.
In the keys file, one can tie this code to an action.


I wanted 'suspend' on close lid.

1) add 'pm-suspend' to sudoers, like so:

sudo echo "ALL ALL = NOPASSWD: /usr/sbin/pm-suspend" \
     > /etc/sudoers.d/pm-suspend

2) add following to ~/.fluxbox/keys:

# suspend on close lid
#   to use this, add pm-suspend to sudoers, like so:
#   sudo echo "ALL ALL = NOPASSWD: /usr/sbin/pm-suspend" \
#     > /etc/sudoers.d/pm-suspend
235 :Exec sudo pm-suspend


NOTE:
The keycode for 'close lid' is 235 on my Dell Latitude.
To check:

a) xev 2>&1 >/tmp/xev.log
b) close lid
c) open lid to re-activate 
d) inspect /tmp/xev.log


Best regards, Paul.

---

