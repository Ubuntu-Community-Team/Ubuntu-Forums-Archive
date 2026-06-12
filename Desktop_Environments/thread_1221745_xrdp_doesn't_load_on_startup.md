---
title: "xrdp doesn't load on startup"
date: 2009-07-24
forum: Desktop Environments
---

### Post by quadratini on 2009-07-24
I'm running xubuntu 9.04 with xrdp 0.4.0 and tightvncserver 1.3.9-4. It works great until I reboot the machine after which I can no longer connect to it via rdp.
 
I verified that xrdp and sesman are running and if I kill both processes and rm var/run/xrdp/xrdp.pid then I can get it back up and running but it doesn't start gnome and it kind of defeats the purpose of having xrdp on there in the first place. 
 
The only way I can get it working again is to completely remove xrdp (using synaptic package manager) and install it back again. Then, like magic, everything works!
 
I would appreciate any help anyone can offer to get xrdp running automatically when the system starts! Help!

---

### Post by ppietryga on 2009-07-24
Hi,
I'm using xrdp on Debian install however it should be easy.

I compiled it from sources, but this is what I have in my configuration.
```

[Globals]
ListenAddress=127.0.0.1
ListenPort=3350
EnableUserWindowManager=1
UserWindowManager=startwm.sh
DefaultWindowManager=startwm.sh

[Security]
AllowRootLogin=0
MaxLoginRetry=4
TerminalServerUsers=tsusers
TerminalServerAdmins=tsadmins

[Sessions]
MaxSessions=10
KillDisconnected=0
IdleTimeLimit=0
DisconnectedTimeLimit=0

[Logging]
LogFile=./sesman.log
LogLevel=DEBUG
EnableSyslog=0
SyslogLevel=DEBUG

[X11rdp]
param1=-bs
param2=-ac

[Xvnc]
param1=-bs
param2=-ac

```

I'm using non-changed /etc/xrdp/xrdp.ini.

And the startwm.sh script mentioned above lies in: 
/usr/local/xrdp/startwm.sh

And it looks like this:
```

#!/bin/sh

# edit this file to run whatever window manager you want
# defaults to running kde


# icewm
if [ "'which icewm-session'" != "" ]; then
 icewm-session
 ecit 0
fi

# for xfce4
#if [ "'which xfce4-session'" != "" ]; then
# xfce4-session
# exit 0
#fi

# gnome
#if [ "'which gnome-session'" != "" ]; then
#  gnome-session
#  exit 0
#fi

# gnome
#which gnome-session
#if [ $? -eq 0 ]; then
#  gnome-session
#  exit 0
#fi

# fluxbox
#if [ "'which fluxbox'" != "" ]; then
#  fluxbox
#  exit 0
#fi

# fall back on xterm
which xterm
if [ $? -eq 0 ]; then
  xterm
  exit 0
fi

```

I'm using icewm for default as this server is quite old, but gnome was running on it while testing for first time.

The xrdp is runing since 21st of January 2009, but had some restarts since then.

Hope it helps.

---

### Post by quadratini on 2009-07-24
Thank you for the quick reply. I checked my ini files and they are similar to yours, except for startwm.sh. Mine looks like this:
 
#!/bin/sh
./etc/X11/Xsession
 
Once the machine starts up, I can kill sesman and xrdp (using sesman --kill and xrdp -kill) and bring them back up again and then xrdp starts working. However, once logged in all I have is a shell window. 
 
I can then run ./etc/xrdp/startwm.sh and gnome comes up. My guess is that xrdp is not reading the startwm.sh file properly. Permissions are set to rwxr-xr-x xrdp/xrdp for this file. Any ideas would be appreciated!
 
Sidenote: This was working fine until I upgraded to xubuntu 9.04 from 8.10. Any ideas what would have changed?
 
Help!

---

### Post by quadratini on 2009-07-27
Just thought I would check in to see if anyone else had any ideas. 
 
I think that Jaunty just isn't ready for xrdp. Sorry guys :(

---

### Post by gorgonvakt on 2009-10-09
> **quadratini said:**
> Just thought I would check in to see if anyone else had any ideas. 
 
I think that Jaunty just isn't ready for xrdp. Sorry guys :(

I happy to tell you that you are wrong. I had the same problems and it seems that the boot is too fast to start both sesman and xrdp in the correct order.

I solved it by removing the splash window at boot so I all the boot-text shown on the screen will make the boot slightly slower.

```

sudo gedit /boot/grub/menu.lst

```

In menu.lst, remove the words "quiet splash" for your preferred startup:

```

An example:

Change

kernel          /vmlinuz-2.6.28-15-generic root=UUID=63abb198-70ea-4251-9b33-929df2a0a34a ro quiet splash 

to 

kernel          /vmlinuz-2.6.28-15-generic root=UUID=63abb198-70ea-4251-9b33-929df2a0a34a ro 

```

\\gorgonvakt

---

### Post by quadratini on 2009-11-03
That totally worked. Nice! 
 
Thank you!

---

