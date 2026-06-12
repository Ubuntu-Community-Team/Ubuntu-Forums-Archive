---
title: "Inhibit auto-suspend NOT screensaver"
date: 2012-10-12
forum: Desktop Environments
---

### Post by opus1 on 2012-10-12
I want to be able to inhibit auto-suspend, but still have the screensaver run in xubuntu precise (basically the "inhibit-applet" in Gnome2). As is pointed out in countless posts, xubuntu has no such feature (although the screenshot at the xfce4-power-manager page shows an "inhibit" menu item that is missing from my version!).

I don't know if this is the right forum for this; if not please direct me.

I have tried installing gnome-power-manager, but I can't get it to start (doing a "which gnome-power-manager" results in nothing, and I can't find it on my system).  Additionally, there doesn't appear to be a "gnome-power-preferences" anymore.

I looked at "caffeine", but the developers say that it inhibits both screensaver and sleep -- not quite what I want -- while others claim it only inhibits the screensaver.  So I haven't bothered trying it yet.

I've read some posts about people with a similar need writing scripts to manipulate Dbus to inhibit sleep, but it seems that sleep doesn't always work when they "un-inhibit".

I have been searching off and on for a week with no solution. can anyone help?

---

### Post by Toz on 2012-10-13
> (although the screenshot at the xfce4-power-manager page shows an "inhibit" menu item that is missing from my version!).Is this a xubuntu install or an xfce install on top of ubuntu? Interestingly, I don't see this option in either my 12.04 install ( Xfce 4.8 ), or in my 12.04 VM with Xfce 4.10.

> I want to be able to inhibit auto-suspend, but still have the screensaver runHave a look at the options in "Settings Manager -> Power Manager", specifically:
- "On AC" tab - "Put the computer to sleep when inactive for"
- "On Battery" - "Put the computer to sleep when inactive for"

and "Settings Manager -> Screensaver, specifically:
- "Advanced" tab - "Power management enabled" (disable it)

> I have tried installing gnome-power-manager, but I can't get it to start
```
ps -ef | grep power-manager
```
...will show you which power manager is running.

---

### Post by opus1 on 2012-10-13
Toz, thanks for the quick reply.  To answer your questions:

This is a fresh xubuntu install.  Not xfce on ubuntu.

You noted you don't see the inhibit option.  I don't either, and what is interesting is it is clearly shown in the screenshot at xfcedocs: [http://docs.xfce.org/xfce/xfce4-power-manager/getting-started]("http://docs.xfce.org/xfce/xfce4-power-manager/getting-started").  I've been trying to figure out if they are showing a newer version than what's in the repositories, but I haven't found a developers page yet.

So... Thanks for the instructions on how to acomplish what I want... but, I wasn't clear in my original post :oops:. I actually know how to do that, I'd like to figure out a way to do this with one click like the gnome-panel inhibit applet (I was so deep in the problem, I forgot to explain it thoroughly enough... ;)).  To quote one of the many posts I've read on this topic: "I want to do this in one click, not 7 (seriously, I counted)".

I did a ```
ps -ef | grep power-manager
``` and got ```
opus        5812  5797  0 09:50 pts/1    00:00:00 grep --color=auto power-manager
``` so, evidently, no power manager is running.  I uninstalled xfce4-power-manager and installed gnome-power-manager, but apparently the gnome one doesn't autostart and issuing a ```
gnome-power-manager
``` gives me a ```
gnome-power-manager: command not found

```  Puzzling!

Thanks for the input, though!  Do you have any other ideas?  Me... I'm still looking.

---

### Post by opus1 on 2012-10-13
it seems there is a newer version (1.2) than what's in the repositories (1.0.11): [http://mail.xfce.org/pipermail/xfce-announce/2012-April/000179.html]("http://mail.xfce.org/pipermail/xfce-announce/2012-April/000179.html") Maybe this is where the screenshot I referred to is from?

however, the xfce goodies website lists only 1.0.10  [http://goodies.xfce.org/projects/applications/xfce4-power-manager]("http://goodies.xfce.org/projects/applications/xfce4-power-manager")

This lack of updated information is a bit frustrating!:confused:

---

### Post by Toz on 2012-10-13
Try re-installing xfce4-power-manager and checking the settings from my post #2.

---

### Post by opus1 on 2012-10-15
OK, I reinstalled the xfce4-power-manager and it is running.  I looked at all the settings you noted in post #2.  I can see how this will keep the computer from going to sleep without disabling the screensaver. 

However, everytime I want to disable/enable the sleep mode, I need to go through these steps?  I can't find a one click "sleep on/sleep off" menu item or applet (like what was in gnome)...

That's my ultimate goal -- to toggle the sleep on and off with as few mouse clicks as possible.

---

### Post by opus1 on 2012-10-21
So, I have decided to try "Caffeine".  I installed it and the "about" menu says: "An application to temporarily prevent the activation of both the screen saver and the "sleep" powersaving mode." Oddly, the preferences are pretty sparse, and I can't see how to make it differentiate between "sleep" and screensaver.  Still, I will set the computer to sleep in 15 minutes and see what happens.  

To further define my problem, here are some use cases.  First let me say that a one-click solution is desired because 1) I'm lazy and 2) my kids and wife are not computer experts (yet) and I would need to write down the 7 steps to acheive what we want.

Use Case 1: We're backing up the file server to "Computer A".  Obviously, we don't want "Computer A" to go to sleep.

Use Case 2: "Computer A" is on and I know I will be ssh'ing into it from "Computer B" upstairs.  Thus, "Computer A" needs to stay awake.

Use Case 3: "Computer A" is in the family room and we have relatives over.  We would like the photo slideshow screensaver to play, but not for "Computer A" to go to sleep.

Caffeine may work for 1 and 2, but depending upon how it handles screensaver vs. sleep, it may not work for 3.  

I've been looking into maybe writing something that keeps sleep from activiating without disturbing the screensaver. I figure I can make an "inhibit" script that, when activated, checks idle time, and after a certain amount of idle time, touches a file (say ".inhibit").  Then, I have a cron job that checks for the existance of ".inhibit" and if it isn't there, issue a pm-suspend.  Ways to check idle time include xprintidle (e.g., [http://stackoverflow.com/questions/222606/detecting-keyboard-mouse-activity-in-linux]("http://stackoverflow.com/questions/222606/detecting-keyboard-mouse-activity-in-linux") and [http://michkhoo.blogspot.com/2009/10/find-idle-time-in-linux.html]("http://michkhoo.blogspot.com/2009/10/find-idle-time-in-linux.html")), w (e.g., [https://coderrr.wordpress.com/2008/04/20/getting-idle-time-in-unix/]("https://coderrr.wordpress.com/2008/04/20/getting-idle-time-in-unix/")) or seeing if xscreensaver is active.

Unfortunately, xprintidle only looks at X activity, so it wouldn't work for use case 2.  Same for checking xscreensaver activity.  I looked at "w", but it looks like the idle column shows "uptime" rather than "idle" time.  Besides, I'm really just trying to re-write the gnome-panel "inhibit applet" all over again!

Maybe caffeine will work.  I'll give it a try and post back.  If anyone has any simpler ideas, please let me know.

I realize I'm nitpicking since I can follow the solution posted by Toz above, but I really would like a one-click solution for my family to use!

---

### Post by opus1 on 2012-10-21
OK, caffeine didn't work as expected.  It kept the screensaver from coming on, but allowed the computer to go to sleep (which is counter to its claim that it would keep the computer from going to sleep).  So it is the exact opposite of what I want.

I guess there is no solution to this problem.  I would love to create a xfce-panel inhibit applet like the one in gnome because I see a lot of posts from xfce users who want it.  Unfortunately, I don't have the programming skills nor the time.

Mark this one as 'unsolved'.

---

### Post by Toz on 2012-10-22
> **opus1 said:**
> OK, I reinstalled the xfce4-power-manager and it is running.  I looked at all the settings you noted in post #2.  I can see how this will keep the computer from going to sleep without disabling the screensaver. 

However, everytime I want to disable/enable the sleep mode, I need to go through these steps?  I can't find a one click "sleep on/sleep off" menu item or applet (like what was in gnome)...

That's my ultimate goal -- to toggle the sleep on and off with as few mouse clicks as possible.

Create the following script, make it executable and assign it to a keyboard shortcut. It will toggle the xfce4-power-manager settings to enable and disable those settings:
```
#!/bin/bash

STATUS=enabled

DISABLED=$(xfconf-query -c xfce4-power-manager -p /xfce4-power-manager/inactivity-on-ac)

[ $DISABLED -eq 0 ] && STATUS=disabled

case $STATUS in

	disabled) #then enable it
	xfconf-query -c xfce4-power-manager -p /xfce4-power-manager/inactivity-on-ac -n -t uint -s 40
	xfconf-query -c xfce4-power-manager -p /xfce4-power-manager/inactivity-on-battery -n -t uint -s 40
	;;

	enabled) #then disable it
	xfconf-query -c xfce4-power-manager -p /xfce4-power-manager/inactivity-on-ac -n -t uint -s 0
	xfconf-query -c xfce4-power-manager -p /xfce4-power-manager/inactivity-on-battery -n -t uint -s 0	
	;;

	*)
	echo "Not a valid condition"
	;;
esac
```

EDIT: After reading your last two posts, I'm not sure this script is enough. There is also the xset group of commands. Maybe these can help create a script that inhibits power saving but not screen saver. Have you seen this thread: [http://forum.xfce.org/viewtopic.php?id=6469]("http://forum.xfce.org/viewtopic.php?id=6469")?

---

### Post by TaDaRa on 2012-11-15
I'll start by qualifying my reply...

My idea is completely unencumbered by the thought process, and might be too simplistic, and I haven't tried it yet, but it's crazy enough that it just might work...

Have two copies of the power managenment config file...  One that disables suspending and one that enables it.  Then, have a script that overwrites the current config file with one or the other, depending on what you want it to do.

When I go to Settings / Power Manager, change a setting, and click Close, I don't know if it's doing something other than writing to the config file.  If it's calling the power management system of the computer and telling it to check out the new settings, my idea won't work.

---

### Post by opus1 on 2013-09-22
I never got around to trying the possible solutions here.  But, I finally had to upgrade all the computers in the house and ran in to suspend issues on all of them (xubuntu 12.04, detailed here: [http://ubuntuforums.org/showthread.php?t=2172157](http://ubuntuforums.org/showthread.php?t=2172157). I came up with a workaround solution to the suspend issue that also happened to solve this issue at the same time.  I documented this here: [http://ubuntuforums.org/showthread.php?t=2176094](http://ubuntuforums.org/showthread.php?t=2176094).  I will post the same procedure here (I hope it's not bad ettiquette to do so...):
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

