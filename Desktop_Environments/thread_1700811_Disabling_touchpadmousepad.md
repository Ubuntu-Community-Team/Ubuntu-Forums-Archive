---
title: "Disabling touchpad/mousepad"
date: 2011-03-05
forum: Desktop Environments
---

### Post by welshmike on 2011-03-05
Thanks to this forum I can disable the mousepad with:
sudo modprobe -r psmouse

I wanted to disable it at startup so I did:
sudo gedit /etc/init.d/rc.local
and added after 
### END INIT INFO
modprobe -r psmouse

However when I log in this fails the first time and I have to log in again.

Where should I have put the modprobe -r psmouse please?

---

### Post by minigeek on 2011-03-05
> **welshmike said:**
> Thanks to this forum I can disable the mousepad with:
sudo modprobe -r psmouse

I wanted to disable it at startup so I did:
sudo gedit /etc/init.d/rc.local
and added after 
### END INIT INFO
modprobe -r psmouse

However when I log in this fails the first time and I have to log in again.

Where should I have put the modprobe -r psmouse please?

Hi

You could try adding this to the crontab

@reboot /sbin/modprobe -r psmouse

---

### Post by welshmike on 2011-03-05
> **minigeek said:**
> Hi

You could try adding this to the crontab

@reboot /sbin/modprobe -r psmouse

Sorry I don't understand. What file do I need to change and what is the content of the line I need to add please.

---

### Post by Copper Bezel on 2011-03-05
The simplest way to set it up as a cron job would be to install the package gnome-schedule , which will appear under Applications -> System Tools -> Scheduled Tasks. Create a new task with that command and set it to "At reboot."

Alternately, you could just list it in your Startup Applications, under Preferences.

---

### Post by Krytarik on 2011-03-06
Or you could just "blacklist" it, so that it doesn't get loaded in the first place. ;-)
Therefore add it to "/etc/modprobe.d/blacklist.conf". If you open the file, you will see the pattern.

Greetings.

---

### Post by wizard10000 on 2011-03-06
Or - you could use syndaemon.  By default it disables the touchpad when there's keyboard activity and re-enables it two seconds after you stop typing.

That's what I use and it works great.

Contents of ~/.config/autostart/syndaemon.desktop - 

```
[Desktop Entry]
Comment[en_US]=
Comment=
Exec=syndaemon -i2
GenericName[en_US]=
GenericName=
Icon=system-run
MimeType=
Name[en_US]=
Name=
Path=
StartupNotify=true
Terminal=false
TerminalOptions=
Type=Application
X-DBUS-ServiceName=
X-DBUS-StartupType=
X-KDE-SubstituteUID=false
X-KDE-Username=
```

You can also run it as a service if you like.

---

### Post by welshmike on 2011-03-06
> **wizard10000 said:**
> Or - you could use syndaemon.  By default it disables the touchpad when there's keyboard activity and re-enables it two seconds after you stop typing.

That's what I use and it works great.

Thanks for your reply. I don't think that is quite what I want because my hand tends to rub the touchpad and moves the cursor to random places on the screen.

---

### Post by welshmike on 2011-03-06
> **Copper Bezel said:**
> The simplest way to set it up as a cron job would be to install the package gnome-schedule , which will appear under Applications -> System Tools -> Scheduled Tasks. Create a new task with that command and set it to "At reboot."

Alternately, you could just list it in your Startup Applications, under Preferences.

Thanks.

I searched for gnome-schedule in Ubuntu Software Centre and found Scheduled tasks, installed it and it appeared in Applications > System Tools > Scheduled Tasks.
In Scheduled Tasks I did New > A task that launches recurrently > Basic > At reboot > Add
...
Edit > Description : Disable touchpad , Command: /sbin/modprobe -r psmouse Default behaviour , Basic : At reboot , Apply

I've no idea what entity was changed by this but am about to find out if I get what I want when I reboot.

Sorry. It didn't work.

---

### Post by wizard10000 on 2011-03-06
> **welshmike said:**
> Thanks for your reply. I don't think that is quite what I want because my hand tends to rub the touchpad and moves the cursor to random places on the screen.

Then syndaemon might be *exactly* what you need  :)

But - your choice, of course.

cheers -

---

