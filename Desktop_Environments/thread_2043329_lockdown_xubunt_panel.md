---
title: "lockdown xubunt panel"
date: 2012-08-16
forum: Desktop Environments
---

### Post by talkingtek on 2012-08-16
Hello,

I'm testing a Xubuntu 12.04 for a computer lab.  I would like to lock  the panel and disable right click on the desktop and when the computer  log off it will clean up the user profiles like Ubuntu 10.04 on  cleanup.sh script.  Can it be possible to do that on Xubuntu? 

On Previous Ubuntu10.04, I was able to write a script on the *cleanup.sh /usr/local/bin/cleanup.sh with the command: rm -rf /home/user/** and when the computer log off or restart everything on the user profile will setup back to default.

If the same script can use on Xubuntu 12.04 where is the command needed  to go:  For example on Previous Ubuntu Gnome: I can type in */usr/local/bin/cleanup.sh under /etc/gdm/PostSession/Default *and it would the job for me.

Since it's going to be on the lap, I will need the pc to logon automatic too so any help on that would be appreciated.

Thank you,

---

### Post by Toz on 2012-08-16
> **talkingtek said:**
> Hello,

I'm testing a Xubuntu 12.04 for a computer lab.  I would like to lock  the panel and disable right click on the desktop
Have a look at this thread on kiosk mode ([http://forum.xfce.org/viewtopic.php?id=6675]("http://forum.xfce.org/viewtopic.php?id=6675")) 
> and when the computer  log off it will clean up the user profiles like Ubuntu 10.04 on  cleanup.sh script.  Can it be possible to do that on Xubuntu? 

On Previous Ubuntu10.04, I was able to write a script on the *cleanup.sh /usr/local/bin/cleanup.sh with the command: rm -rf /home/user/** and when the computer log off or restart everything on the user profile will setup back to default.

If the same script can use on Xubuntu 12.04 where is the command needed  to go:  For example on Previous Ubuntu Gnome: I can type in */usr/local/bin/cleanup.sh under /etc/gdm/PostSession/Default *and it would the job for me.

Since 12.04 uses lightdm, you need to look at configuring lightdm. According to /usr/share/doc/lightdm/lightdm.conf.gz:
```
zless /usr/share/doc/lightdm/lightdm.conf.gz
```
...it looks like you can use the "session-cleanup-script" configuration option
```
# session-cleanup-script = Script to run when quitting a user session (runs as root)
```
...to run commands on logout.

> Since it's going to be on the lap, I will need the pc to logon automatic too so any help on that would be appreciated.

Thank you,
Add the following to the "[Seat Defaults]" section of /etc/lightdm/lightdm.conf:
```

autologin-user=<YOUR USER>
autologin-user-timeout=0
```

---

### Post by talkingtek on 2012-08-16
Hey, thanks! that's a quick response.  I'll check it out..

---

### Post by talkingtek on 2012-08-16
I was able to lock down the panel, but I experienced something ugly: Here's the code I used:
 						/etc/xdg/xfce4/xfconf/xfce-perchannel-xml/xfce4-panel.xml
<?xml version="1.0" encoding="UTF-8"?>
<channel name="xfce4-panel" version="1.0" locked="*" unlocked="root">
....


the bottom panel wasn't suppose to be there.  I deleted on the main account already, but after a reboot the bottom panel show up again with bunch folders and invalid icons.  What have I done wrong?


thanks

---

### Post by Toz on 2012-08-16
I believe that xubuntu puts it xfce configuration files in /etc/xdg/xdg-xubuntu instead of /etc/xdg/. Try the above again but this time manipulate the files in /etc/xdg/xdg-xubuntu instead.

---

### Post by talkingtek on 2012-08-17
I tried this but no luck:
/etc/xdg/xdg-xubuntu/xfce4/panel/default.xml


<?xml version="1.0" encoding="UTF-8"?>

<channel name="xfce4-panel" version="1.0" locked="*" unlocked="root">

---

### Post by talkingtek on 2012-08-17
zless /usr/share/doc/lightdm/lightdm.conf.gz
#session-cleanup-script?

what do I have to do there?  Can you please give me more detail?  I looked in there but I can't do much.  sorry i'm new to this stuff.

---

### Post by Toz on 2012-08-20
> **talkingtek said:**
> zless /usr/share/doc/lightdm/lightdm.conf.gz
#session-cleanup-script?

what do I have to do there?  Can you please give me more detail?  I looked in there but I can't do much.  sorry i'm new to this stuff.

With lightdm, you can specify a session-cleanup-script in much the same way as you did with gdm using /etc/gdm/PostSession/Default. Something like:
```
session-cleanup-script=/usr/local/bin/cleanup.sh
```
...added to your /etc/lightdm/lightdm.conf should work to cleanup the session.

Also, have a look at this file: /usr/share/doc/xfdesktop4-data/README.kiosk, for more info about setting up kiosk mode.

---

### Post by talkingtek on 2012-08-24
Finally got it work except one piece that I'm still struggle.  I was able to setup the thing logon automatic when the pc restart, but I need the script to log back automatic when someone click on logout.

See on gdm I was able to do that by /sbin/gdm restart on /etc/gdm/PostSession/Default but where in Xubuntu?

Also I have an issue to start Xubuntu by this command sudo service lightdm restart.  when I submit the command, I got into a black screen and hang in there until I push ctrl, alt, del. or ctrl, alt + F1 and type in the command the 2nd time.

I'm kind of stuck, any way that you can help me?

thanks..

---

### Post by Toz on 2012-08-24
What does your /etc/lightdm/lightdm.conf file look like? Are you using the "autologin-user-timeout" parameter? (set to 0).

---

