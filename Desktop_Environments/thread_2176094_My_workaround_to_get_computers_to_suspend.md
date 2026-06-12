---
title: "My workaround to get computers to suspend"
date: 2013-09-22
forum: Desktop Environments
---

### Post by opus1 on 2013-09-22
The built in suspend functions (using the buttons on the panel, or auto timed suspend) wouldn't work on both the computers on which I installed xubuntu 12.04 documented here: [http://ubuntuforums.org/showthread.php?t=2172157]("http://ubuntuforums.org/showthread.php?t=2172157"). 

To start diagnosing, I issued a "sudo pm-suspend" in the terminal and the computer suspended/resumed just fine. I tried something I read in a forum about adding "xfce4-power-manager --no-daemon" as an autostart application, but ultimately it didn't work. So I came up with my own routine to the computer to suspend if no users are on the system.  Your mileage may vary, but it has worked well for me for the last month and a half with 3 separate user accounts on each computer.

1.) ensure that each user's power manager (setings >> settings manager >> Power Manager >> On AC) has the "put the computer to sleep when inactive" set to "Never" or else it will interfere with some steps in this procedure.

2.) if it doesn't already exist, create a group for all the users on the system (mine was called "allusers"):
```

sudo groupadd allusers

```
Add each user to the group
```

sudo usermod -a -G allusers username

```

3) Set up a common area that all users can read/write to. I created "/usr/share/lockCheck/", and did ```
chown root:allusers
``` to ensure that all the users in the "allusers" group could read and write to it.

4.) create a script for each user to monitor when xscreensaver locks the screen and unlocks the screen. When the screen is locked by any user, it writes a file to the share area that is basically a way to record the time. If any user unlocks the screen it removes the file. My script was adapted from [https://bbs.archlinux.org/viewtopic.php?pid=1182514#p1182514](https://bbs.archlinux.org/viewtopic.php?pid=1182514#p1182514). I tried a perl script I found first that did the same thing, but it kept one processor pegged at 100% all the time, so i deleted it. ```
#!/bin/bash
#monitors for screen lock and adds a ".lock" file to the shared area
#also monitors for screen unlock and removes the ".lock" file from the shared area 
process() {
while read input; do 
  case "$input" in
    UNBLANK*)	rm /usr/share/lockCheck/.lock ;;
    LOCK*)	touch /usr/share/lockCheck/.lock ;;
  esac
done
}

/usr/bin/xscreensaver-command -watch | process
```
5.) put the monitoring script into each user's start up applications: Settings Manager >> Session and Startup >> autostart applications >> add and then point it to the script made in #4.

6.) We don't want a user to log in after another has made the lock file and have their session abruptly hibernate, so the lock file must be removed whenever a user logs in. Make a script to remove the lock file (just entering the command into an autostart application entry didn't work for me).```
#!/bin/bash
rm -f /usr/share/lockCheck/.lock
```
7.) I want to be able to inhibit the suspend if I'm doing something and need to lock the screen in the meantime. That is a simple as writing an inhibit file to the share area and then having the system check for it. The tricky part is creating a panel Icon that can toggle to show the inhibit status. A couple of forums recommended the genmon plugin, but I found a purely BASH solution at [https://forum.xfce.org/viewtopic.php?id=6814](https://forum.xfce.org/viewtopic.php?id=6814) which I adapted as follows (I'm not entirely sure how it works, but it does!). The trick is to set up a launcher that calls it with a "%k" following the command. So in my case I saved the below script as ~/scripts/inhibitSuspend.sh, and my launcher called it as "~/scripts/inhibitSuspend.sh %k":```
#!/bin/sh

filename=${1#file://}
#does the ".inhibit" file exist?
if [ -f /usr/share/lockCheck/.inhibit ]
then
   #yes it does, remove it and change the panel icon to the hibernate icon
   rm -f /usr/share/lockCheck/.inhibit
   desktop-file-edit --set-icon="system-suspend-hibernate" "$filename"
   touch "$filename"
else
  #no it doesn't, add it and change the panel icon to the "no-hibernate" icon
   touch /usr/share/lockCheck/.inhibit
   desktop-file-edit --set-icon="gpm-inhibit" "$filename"
   touch "$filename"
fi
```
8.) Now that all the users are writing and removing the lock file correctly, the system needs to check periodically to see if it can suspend. I logged in as root and created the following script (which I called "checkForSuspend.sh"):```
#!/bin/bash

#get the current date/time
today=`date +%s`

#write the date to a log
date>>/root/.suspend.log

#first check to see if the sleep function is being inhibited
if [ ! -f /usr/share/lockCheck/.inhibit ]
then
   #assign the name of the file to check to a variable
   file=/usr/share/lockCheck/.lock

   #check the file's date/time stamp
   fileDate=`date -r $file +%s`

   #How many minutes old is the file?
   diff=$(($today-$fileDate))

   #if the file is over 15 minutes old, suspend the server
   #if test $diff -gt 900; then

   if test $diff -gt 600; then
     echo "${diff}, suspend">>/root/.suspend.log
     sudo pm-suspend
   else
     echo "${diff}, no suspend">>/root/.suspend.log
   fi
else
   echo "inhibit file present, no suspend">>/root/.suspend.log
fi

```
9.) now write a cron job for the root user to fire off the above script every 10 minutes. This way, the computer will suspend after 10-20 minutes of activity (depending upon when the lock file was written. Not too precise, but who cares?). Issue "crontab -e" as root and add:
```

0,10,20,30,40,50 * * * * /root/scripts/checkForSuspend.sh

```
10.) Finally, make sure that the computer will go back to sleep in 10 minutes after being turned back on, but with no one logging in, by touching the lock file on resume. This is a little tricky because root has to touch it, which renders it untouchable, or undeletable, by other users. So, in addition to touching the file, the permissions and owner need to be changed as well. So add a script in "/etc/pm/sleep.d" ( I called mine "20_removeLock", but that's not the best name):
```

#!/bin/bash

case "$1" in 
    thaw|resume)
       touch /usr/share/lockCheck/.lock 2>/dev/null
       chown root:allusers /usr/share/lockCheck/.lock
       chmod 770 /usr/share/lockCheck/.lock
       ;;
     *)
       ;;
esac
exit $?

```
As I said, so far this has worked as expected under heavy computer use from myself, my wife and two kids on two separate computers.  The only possible problem I could think of with the logic is that you could wake the computer a split second before the cron job checks for suspend and it could go right to sleep again, but the chances of that happening are pretty low.

---

