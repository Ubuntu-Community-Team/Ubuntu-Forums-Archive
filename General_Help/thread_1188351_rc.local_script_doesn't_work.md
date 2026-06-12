---
title: "rc.local script doesn't work"
date: 2009-06-15
forum: General Help
---

### Post by elektronaut on 2009-06-15
Hi,

I'm trying to devise a solution which will either automatically choose which display to use after boot up (laptop or external) or, if it's not possible to get the necessary parameters for the right decision, let the user decide. This might sound a bit awkward, I know. It's based on several threads which are mentioned in the code below, which you may read in case you are interested in my idea. In fact, I wanted to write a HowTo about it, but at the moment my solution is not working yet. *If you only want to help me and are not too much interested in the script, you can skip the following description and just try to answer my (fat) question at the end.*

The central part of the solution is the **'/etc/rc.local'** script pasted below. This is how it works:

1) Checking which network interface is in use, trying to find out if we are in the home network. 
2) If so, use the external display. 
3) If not, have the user decide.

In effect, it's all about text file manipulation. The following files have to be changed in order for **[COLOR="Red"](a)[/COLOR]** automatic or **[COLOR="Lime"](b)[/COLOR]** manual display configuration:

**/etc/X11/xorg.conf** - either the configuration for the external display **[COLOR="Red"](a)[/COLOR]**, or the one with different server layouts **[COLOR="Lime"](b)[/COLOR]**
**/etc/X11/default-display-manager** - enable **[COLOR="Red"](a)[/COLOR]** or disable **[COLOR="Lime"](b)[/COLOR]** gdm
**~/.bash_profile** - delete **[COLOR="Red"](a)[/COLOR]** or add **[COLOR="Lime"](b)[/COLOR]** the call to the display configuration script

Here is the **'/etc/rc.local'** script, for those who are interested:
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
#
# ... added the following lines so that the correct display is used
# automatically.
# this is based on the following threads:
# http://ubuntuforums.org/showthread.php?t=308673
# http://ubuntuforums.org/showthread.php?t=271045
# and this idea http://ubuntuforums.org/showpost.php?p=2300599&postcount=25

################# automatic display configuration
for a in {1..15} # give the network interface time to come up
do
  if ifconfig eth0|grep -q '192.168.1.2' # CHANGE IP TO REFLECT THE ONE ASSIGNED BY YOUR ROUTER
    # we are at home
    then
      # and use the external display
      cp /etc/X11/xorg.conf.external /etc/X11/xorg.conf
      # we delete the automatic call for the manual display selection script in bash_profile
      if grep -q "/home/elektronaut/bin/xgui.sh"  /home/elektronaut/.bash_profile
        then
          grep -v '/home/elektronaut/bin/xgui.sh' /home/elektronaut/.bash_profile > /tmp/bash_profile.tmp
          cat /tmp/bash_profile.tmp > /home/elektronaut/.bash_profile
          rm /tmp/bash_profile.tmp
      fi
      # set the display manager
      echo "/usr/sbin/gdm" > /etc/X11/default-display-manager
      exit 0
  fi
  sleep 2 # give the network interface time to come up
done

################# manual display configuration
# if we get to this point, we will go bodhi.zazen's way
# and let the user decide - see http://ubuntuforums.org/showthread.php?t=240150

# the configuration with different server layouts
cp /etc/X11/xorg.conf.server-layouts /etc/X11/xorg.conf
# automatic call of the script described in http://ubuntuforums.org/showthread.php?t=271045
if ! grep -q "/home/elektronaut/bin/xgui.sh"  /home/elektronaut/.bash_profile
  then
  echo "/home/elektronaut/bin/xgui.sh" >> /home/elektronaut/.bash_profile
fi
# disable gdm, enable easy reactivation
echo "#/usr/sbin/gdm" > /etc/X11/default-display-manager

exit 0

```


[COLOR="Red"][SIZE="2"]**Finally, my question: Why is this not working? If I call '/etc/rc.local' manually in the console, all files are manipulated as expected. But it doesn't work during boot!**[/SIZE][/COLOR]

---

### Post by elektronaut on 2009-06-16
I'm still working on this. The problem seems to be the order of services startup. Look here for my new thread about this: [Possible to change the boot order of GDM?](http://ubuntuforums.org/showthread.php?p=7466504)

---

