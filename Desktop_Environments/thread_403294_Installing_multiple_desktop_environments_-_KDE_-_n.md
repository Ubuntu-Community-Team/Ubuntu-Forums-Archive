---
title: "Installing multiple desktop environments - KDE - need help"
date: 2007-04-06
forum: Desktop Environments
---

### Post by mangoHead84 on 2007-04-06
Hi,

I hae the regular GNOME version of Ubuntu 6.10 running on my comp. I wanted to try out the KDE desktop environment i.e. create a multiple desktop environment system. So I started Synaptic and marked the 'kubuntu-desktop' package for installation along with all of its dependencies etc....

The download and installation went fine. After restarting the comp I tried to log in to KDE. The screen changed blue and I got a message that said - "Could not start kstartupconfig. Check your installation". 

After clicking on the 'ok' button i got another message - "Your session only lasted less than 10 seconds.............. These errors have been written to the ~/.xsession-errors file"

The contents of the 'xsession-errors' file are as follows-
[INDENT]
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "srdan"
/etc/gdm/Xsession: Beginning session setup...
trying to create local folder /home/srdan/.kde/share: Permission denied
trying to create local folder /home/srdan/.kde/share: Permission denied
trying to create local folder /home/srdan/.kde/share: Permission denied
Xlib:  extension "XFree86-VidModeExtension" missing on display ":0.0".
Traceback (most recent call last):
  File "/usr/bin/displayconfig-restore", line 297, in ?
    main()
  File "/usr/bin/displayconfig-restore", line 268, in main
    hdisplay = mode_line[1]
TypeError: unsubscriptable object
SESSION_MANAGER=local/srdan-desktop:/tmp/.ICE-unix/11377
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
evolution-alarm-notify-Message: Setting timeout for 639 1175904000 1175903361
evolution-alarm-notify-Message:  Sat Apr  7 12:00:00 2007

evolution-alarm-notify-Message:  Sat Apr  7 11:49:21 2007[/INDENT]

so the first problem it encounters is that it cannot create the folders. When I looked at the folder in question '.kde' its permissions are set to root user only, I cannot even see the contents of the folder. Which seems strange to me since the folder is in my home directory.

The other error seems to be the - Xlib:  extension "XFree86-VidModeExtension" missing on display ":0.0" error

Has anyone had this problem before? I would perfer not to have to download and install the whole of KDE again unless it's absolutely necessary. Some help would be much appreciated.

---

### Post by dbbolton on 2007-04-06
you can change the permissions of the folder by launching ```
gksudo nautilus ~
```

then press Ctrl + H to show the hidden folders. then you can right click on .kde and change the permissions.

i really don't know what cause this problem in the first place, though ...

---

### Post by mangoHead84 on 2007-04-06
I changed the permissions for the '.kde' folder as well as the 'share' folder inside of .kde and now it's working fine. I changed the owner of the files from the root account to my own account and in the second box i gave root the same permissions as before. 

Turned out to be a pretty easy fix, but I still don't know why it didn't just set the owner to be my account in the first place. 

Anyway, thank you for the prompt reply dbbolton and the advice. I was expecting to be waiting a few hours at least for a reply, it was great to get one so quick.

---

### Post by dbbolton on 2007-04-06
no problem. i'm glad too see that you got it working !

---

