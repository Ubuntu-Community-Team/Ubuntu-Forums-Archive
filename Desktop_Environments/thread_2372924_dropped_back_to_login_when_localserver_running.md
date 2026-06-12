---
title: "dropped back to login when localserver running"
date: 2017-09-30
forum: Desktop Environments
---

### Post by rushyx on 2017-09-30
Hello dear forum members

I have what I consider a strange problem that I've been trying to solve for some time. From a clean install of Ubuntu 16.04 LTS all seems to be working well, login and out access the internet etc. Next I install apache2 as I need to run a localhost to develop my web projects offline. I get the Apache welcome page up ok from the index.html in /var/www/html   - all good so far

Now I copy over a test web projects to this folder /var/www/html and it comes up fine in Firefox as localhost. (This is nothing special just a set of html only files I've used for ages to test.) Great!    Here is the punch - as soon as I reboot the system and login to my account I note that on the desktop the speaker & bluetooth icon are greyed out. After a few seconds I am dumped back to the login screen. Any further attempt to login fails and dumps me back to login screen. 

I've tried checking the .Xauthority file, changing privs and deleting it to no avail.  I note the .xsession_error has the errors below so i can see my indicators are getting killed which is probably related. I'm looking for some ideas of how to troubleshoot this? 

Many thanks for any ideas! - Paul

```
openConnection: connect: No such file or directory
cannot connect to brltty at :0
upstart: gnome-session (Unity) main process (1310) terminated with status 1
upstart: logrotate main process (1174) killed by TERM signal
upstart: upstart-dbus-session-bridge main process (1221) terminated with status 1
upstart: bamfdaemon main process (1301) killed by TERM signal
upstart: indicator-bluetooth main process (1452) killed by TERM signal
upstart: indicator-datetime main process (1456) killed by TERM signal
upstart: indicator-printers main process (1459) killed by TERM signal
upstart: indicator-session main process (1460) killed by TERM signal
upstart: indicator-application main process (1461) killed by TERM signal
upstart: Disconnected from notified D-Bus bus
```

[B]I've had no replies and no luck solving this. As soon as I copy my project files to the apache root /var/www/html the next reboot will start the login looping. Can anyone give me some guidance to troubleshoot Apache? Thanks!
[/B]

---

### Post by rushyx on 2017-10-04
Just to show how strange errors can be - I seem to have solved this and it was a knock on effect of a completely unrelated problem in the file system. The root fs partition on my disc was mis-configured. gparted warned me that 44G of free space was unavailable  on my 200G SSD and I needed to run the gparted "check" on it. After I did that an allowed it to resize the partition so all space is available,  I have not had any further occurrence of this problem. The most surprising thing - I had this mis-configured root partition for many months with no other problems on a system in daily use. I guess that at some stage as the file system grew it has created a corruption elsewhere in the system. I just hope that this "remedy" has not moved the corruption elesewhere and it will rear it's head again later. Time will tell, but right now I can press on with the development.

---

