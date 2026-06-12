---
title: "Automatic Startup of uShare on Jaunty Jackalope (9.04)"
date: 2009-05-28
forum: General Help
---

### Post by TombstoneX on 2009-05-28
[COLOR=Red]**[SIZE=5]_SOLVED_[/SIZE] (See last post I made)**[/COLOR]
I have been trying to get uShare to startup when the computer boots to no avail. Any help would be greatly appreciated.

I am running Wireless, as apposed to a wired connection.

The command I use in terminal to start it manually is:

```
ushare -x -c /home/tombstonex/Videos
```I have tried running to in the System >> Preferences >> Startup Applications.

I have also tried what someone suggested of editing the " /etc/rc.local " with the following lines

```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

[B]#! /bin/bash
ushare -x -c /home/tombstonex/Videos &[/B]


exit 0

```

---

### Post by TombstoneX on 2009-05-28
anyone?

---

### Post by TombstoneX on 2009-05-28
I was reading online about an Init.d starting scripts automatically at boot-up. Using the documentation, I created a executable file " /etc/init.d/startushare " with the following in it:

```
#!/bin/sh -e
#
# uShare init script
#
### BEGIN INIT INFO
# Provides:          ushare
# Required-Start:    $all
# Should-Start:
# Required-Stop:
# Should-Stop:
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: uShare
# Description:       uShare Autorun
### END INIT INFO


ushare -x -c /home/tombstonex/Videos
```

Then I issued the command " **sudo update-rc.d ushare defaults** " to make it run at startup, and still nothing.

---

### Post by TombstoneX on 2009-05-28
_[SIZE=6][COLOR=Red]**SOLVED**[/COLOR][/SIZE]_


**Issue: **I figured it out. Because I am running wireless the ushare would always fail to load because it was loading to quickly before the wireless had a chance to reconnect with the router.

**How i fixed it:**

Created a simple script with the following lines:


```
sleep 10
ushare -x -c /sharepath
```This makes it so that it waits 10 seconds before running the command. Then make the script executable.

**sudo chmod +x *scriptname***

Add the script to the Startup Applications list:

System >> Preferences >> Startup Applications

create a new entry and point the command to the script you created.

Now reboot and test if it works, if it doesnt you may need to add more time to the sleep command in the script.

---

### Post by twent4 on 2009-08-20
> **TombstoneX said:**
> 

**sudo chmod -x *scriptname***



Just a quick correction, that should be **+x**

---

### Post by TombstoneX on 2009-08-21
> **twent4 said:**
> Just a quick correction, that should be **+x**

sorry for the typo.. corrected :)

---

