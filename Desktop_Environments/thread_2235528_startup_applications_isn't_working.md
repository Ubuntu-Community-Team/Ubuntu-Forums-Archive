---
title: "startup applications isn't working"
date: 2014-07-21
forum: Desktop Environments
---

### Post by ship22 on 2014-07-21
Any ideas on why this fails?

Ubuntu 14.04 LTS

:~$ cat .config/autostart/xscreensaver.desktop 
[Desktop Entry]
Type=Application
Exec=/usr/bin/xscreensaver -nosplash &
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[en_US]=xscreensaver
Name=xscreensaver
Comment[en_US]=
Comment=

It worked for a short bit.. then ceased to work.  Runs fine manually.

If this is just Unity failure, is there a way to accomplish the same thing using rc files?

---

### Post by ubudog on 2014-07-21
Not sure why that itself is failing, but I'd suggest you use /etc/rc.local for this.  Open it up in a text editor as root, and add
> /usr/bin/xscreensaver -nosplash &

before the 'exit 0'.

Hope that does it!  :-)

---

### Post by Dennis N on 2014-07-21
Mine (in the same location) looks like this in Ubuntu 12.04. I think it was created by Ubuntu when I added xscreensaver to startup applications. I remember entering the command and the comment in the dialog.

```
[Desktop Entry]
Type=Application
Exec=xscreensaver -no-splash
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[en_US]=Xscreensaver
Name=Xscreensaver
Comment[en_US]=xscreensaver program
Comment=xscreensaver program

```

---

### Post by ship22 on 2014-07-21
I did try that but xscreensaver won't run as root. I'm not sure if there is a simple way to run it from there.  I guess I could make an init.d/service file for it but I seem to be going down some ridiculous rabbit holes just to run xscreensaver... usually a sure sign I'm missing something profoundly obvious.

---

### Post by ubudog on 2014-07-21
You could have it run as your user, I believe, by editing your crontab.

```
crontab -e -u <username>
```

Then, at the bottom, add:
> @reboot /usr/bin/xscreensaver -nosplash &

and save the file.  On the next start it should be running.

---

