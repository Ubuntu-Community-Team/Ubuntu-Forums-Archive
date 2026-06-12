---
title: "cron job will not execute"
date: 2009-02-23
forum: General Help
---

### Post by efplaya on 2009-02-23
I have been having trouble getting the command 'xset dpms force off' to execute from cron. My goal is to write a script that checks how long i have been idle and turns off my monitor using that command. When i tested cron out i typed crontab -e and i put

*/10 * * * * /usr/bin/xset dpms force off

in there. The cron job ran every 10 minutes but did not execute this command to turn off the monitor. I have tried everything, running on root and putting root in as one of the users along with creating environmental variables by saying 'path=/usr/bin'.
Can anyone who is familiar with cron jobs please help me out and let me know what i'm doing wrong? All i want is for cron to execute that one line...

---

### Post by mike2357 on 2009-02-23
Cron needs a way to communicate with the world of xwindows.  I think your cron command should be run by you (i.e. a regular user) rather than root.  Try putting your xset command in a script, but before calling xset, insert the following commands:

#Just exit if I'm not logged in
who | grep $LOGNAME > /dev/null 2>&1
if [ $? -ne 0 ] 
then
     exit    
fi

# Set DBUS, needed for cron to know about user session . . .
export $(xargs -n 1 -0 echo </proc/$(pidof x-session-manager)/environ |
grep -Z DBUS_SESSION_BUS_ADDRESS=)

Rather than using a script run from cron, have you tried accessing System -> Preferences -> Power Management and changing the settings there?

---

### Post by efplaya on 2009-02-23
Well thats the problem, is that gnome power manager stopped turning off my display i think it is a bug with nvidia/compiz... Thanks for your suggestion i will try it tonight when i get home. I dont know why GPM stopped turning the display off...

---

### Post by efplaya on 2009-02-23
Nope i dont know why but that doesnt work either. Why is it so hard for cron to shut off the monitor!

---

