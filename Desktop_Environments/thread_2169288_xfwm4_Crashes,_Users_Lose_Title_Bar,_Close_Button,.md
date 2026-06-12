---
title: "xfwm4 Crashes, Users Lose Title Bar, Close Button, Etc."
date: 2013-08-21
forum: Desktop Environments
---

### Post by Kirk Schnable on 2013-08-21
I am managing a large deployment of several hundred machines running Xubuntu 12.04.  We've recently been plagued with a problem where XFCE's window manager seems to be crashing on some users' profiles.  

We're currently running XFCE 4.8 on Xubuntu 12.04 LTS.

After xfwm4 crashes, it no longer shows up in ps aux (because it's not running anymore).  The users lose their title bar on every window, so they lose the ability to resize, close, maximize, etc. for any open window.  Sometimes, I also can't switch windows, so I find myself opening a terminal and then not being able to type inside it.

When the crash happens, the solution is either to open a terminal and run "xfwm4&", which immediately relaunches xfwm4 and fixes the problem, or to relocate\remove the users' dotfolders so as to reset their profile settings.

I'm not sure yet what setting or file is causing the problem.  It seems to be totally random.  I have not found any useful log information yet.  Perhaps someone could point me in the right direction of where to look for that?

I am going to use Puppet to push out this simple watchdog script for now until we have a better solution.  I'm going to run it using their "Sessions & Startup" where I placed a general start-up bash script I can easily modify over the network without touching their profile.   (exactly for situations like this).
```
#!/bin/bash
###########################################
#            XFWM4 Restarter              #
###########################################
#> Paths to Binaries
PS="/bin/ps"
GREP="/bin/grep"
WC="/usr/bin/wc"
ECHO="/bin/echo"
SLEEP="/bin/sleep"
TOUCH="/bin/touch"


#> Settings
problematicapp="xfwm4"
relaunchbin="/usr/bin/xfwm4"
MYLOG="/tmp/xfwm4-mws.log"


############ CODE, DO NOT EDIT ############
$TOUCH $MYLOG
while [ 1 ]; 
do
if [ $($PS aux | $GREP $problematicapp | $WC -l) -gt 1 ];
then
    $ECHO "xfwm4 is running."
    $ECHO "xfwm4 is running." >> $MYLOG
    $SLEEP 10
else
    $ECHO "xfwm4 is crashed."
    $ECHO "Restarting xfwm4..."
    $ECHO "xfwm4 is crashed." >> $MYLOG
    $ECHO "Restarting xfwm4..." >> $MYLOG
    $relaunchbin&
fi
done
```

Does anyone else have any good information on this problem?

Thanks,
Kirk

---

### Post by ajgreeny on 2013-08-21
Have a look in Sessions & Startup in the settings manager and see if xfwm4 is showing in the **session** tab with **immediate** at the end as the restart option.  It is in mine, but I have done nothing to get that situation, so if your errant machines do not have it there must be some way to add it.

---

### Post by Kirk Schnable on 2013-09-03
> **ajgreeny said:**
> Have a look in Sessions & Startup in the settings manager and see if xfwm4 is showing in the **session** tab with **immediate** at the end as the restart option.  It is in mine, but I have done nothing to get that situation, so if your errant machines do not have it there must be some way to add it.
Thanks, I did look at this as you suggested.  It was set to **immediate**.  :\

On the bright side, my patch I pushed out is working marvelously.

---

