---
title: "Kernel 4.10 upgrade, can't log in, default video"
date: 2017-07-21
forum: Desktop Environments
---

### Post by DigiAngel on 2017-07-21
Nothing in the logs, login and kicks me back out.  Flawless with 4.8.  Specs:

GTX 980, 4G RAM
i7-4790K @4GHz
16G ram
OS is running on a Samsung SSD 850 Pro

---

### Post by #&amp;thj^% on 2017-07-21
> **DigiAngel said:**
> Nothing in the logs, login and kicks me back out.  Flawless with 4.8.  Specs:

GTX 980, 4G RAM
i7-4790K @4GHz
16G ram
OS is running on a Samsung SSD 850 Pro

Probably left overs or renamed configs.
Post back from the terminal;
```
cd /etc/X11
ls
```
Run one line at a time.
EDIT: Also have you tried with "nomodeset" when booting form grub?

---

### Post by DigiAngel on 2017-07-21
Thanks....again, 4.8 works fine.
```

drwxr-xr-x 2 root root  4096 Jun 15  2016 app-defaults
drwxr-xr-x 2 root root  4096 May 21  2016 cursors
-rw-r--r-- 1 root root    18 Aug  4  2015 default-display-manager
drwxr-xr-x 4 root root  4096 Aug  4  2015 fonts
drwxr-xr-x 3 root root  4096 Jun 15  2016 ja_JP.eucJP
drwxr-xr-x 3 root root  4096 Jun 15  2016 ja_JP.UTF-8
-rw-r--r-- 1 root root 17394 Dec  3  2009 rgb.txt
drwxr-xr-x 3 root root  4096 Feb 15 04:34 xinit
drwxr-xr-x 2 root root  4096 Jan 15  2014 xkb
-rw-r--r-- 1 root root   269 Dec  4  2015 xorg.conf.failsafe
-rwxr-xr-x 1 root root   709 Apr  1  2010 Xreset
drwxr-xr-x 2 root root  4096 May 21  2016 Xreset.d
drwxr-xr-x 2 root root  4096 May 21  2016 Xresources
-rwxr-xr-x 1 root root  3730 Oct  8  2014 Xsession
drwxr-xr-x 2 root root  4096 May 17 18:07 Xsession.d
-rw-r--r-- 1 root root   265 Jul  1  2008 Xsession.options
drwxr-xr-x 2 root root  4096 May 21  2016 xsm
-rw-r--r-- 1 root root   601 Aug  4  2015 Xwrapper.config
```


More info...I have ssh access:

```
Jul 21 17:47:35 gamebox systemd[1]: Started User Manager for UID 1000.
Jul 21 17:47:48 gamebox pulseaudio[1742]: [pulseaudio] bluez5-util.c: GetManagedObjects() failed: org.freedesktop.DBus.Error.TimedOut: Failed to activate service 'org.bluez': timed out
Jul 21 17:47:49 gamebox systemd-timesyncd[813]: Synchronized to time server 91.189.91.157:123 (ntp.ubuntu.com).
Jul 21 17:48:06 gamebox systemd[1]: Starting Stop ureadahead data collection...
Jul 21 17:48:06 gamebox rsyslogd-2359: action 'action 4' resumed (module 'builtin:omfwd') [v8.16.0 try [http://www.rsyslog.com/e/2359](http://www.rsyslog.com/e/2359) ]
Jul 21 17:48:06 gamebox systemd[1]: Stopped Read required files in advance.
Jul 21 17:48:06 gamebox systemd[1]: Started Stop ureadahead data collection.
Jul 21 17:48:45 gamebox org.gtk.vfs.Daemon[1644]: A connection to the bus can't be made
Jul 21 17:48:45 gamebox systemd[1]: Started Session c3 of user user.
Jul 21 17:48:45 gamebox org.ayatana.bamf[2235]: bamfdaemon start/running, process 2305
Jul 21 17:48:46 gamebox org.a11y.atspi.Registry[2382]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Jul 21 17:48:46 gamebox gnome-session[2371]: gnome-session-is-accelerated: No hardware 3D support.
Jul 21 17:48:46 gamebox gnome-session[2371]: gnome-session-check-accelerated: Helper exited with code 256
Jul 21 17:48:46 gamebox gnome-session[2371]: gnome-session-binary[2371]: CRITICAL: We failed, but the fail whale is dead. Sorry....
Jul 21 17:48:46 gamebox gnome-session-binary[2371]: CRITICAL: We failed, but the fail whale is dead. Sorry....
Jul 21 17:48:46 gamebox lightdm[1196]: ** (lightdm:1196): CRITICAL **: session_get_login1_session_id: assertion 'session != NULL' failed
Jul 21 17:48:46 gamebox lightdm[1196]: /etc/modprobe.d is not a file
Jul 21 17:48:46 gamebox lightdm[1196]: message repeated 4 times: [ /etc/modprobe.d is not a file]
Jul 21 17:48:46 gamebox lightdm[1196]: update-alternatives: error: no alternatives for x86_64-linux-gnu_gfxcore_conf
Jul 21 17:48:47 gamebox systemd[1]: Started Session c4 of user lightdm.
Jul 21 17:48:47 gamebox org.a11y.atspi.Registry[2473]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Jul 21 17:48:47 gamebox dbus[983]: [system] Activating via systemd: service name='org.bluez' unit='dbus-org.bluez.service'
Jul 21 17:23:24 gamebox systemd: pam_unix(systemd-user:session): session closed for user lightdm
Jul 21 17:48:45 gamebox lightdm: pam_unix(lightdm-greeter:session): session closed for user lightdm
Jul 21 17:48:45 gamebox lightdm: pam_unix(lightdm:session): session opened for user user by (uid=0)
Jul 21 17:48:46 gamebox lightdm: pam_unix(lightdm:session): session closed for user user
Jul 21 17:48:46 gamebox lightdm[1196]: ** (lightdm:1196): CRITICAL **: session_get_login1_session_id: assertion 'session != NULL' failed
Jul 21 17:48:46 gamebox lightdm[1196]: /etc/modprobe.d is not a file
Jul 21 17:48:46 gamebox lightdm[1196]: message repeated 4 times: [ /etc/modprobe.d is not a file]
Jul 21 17:48:46 gamebox lightdm[1196]: update-alternatives: error: no alternatives for x86_64-linux-gnu_gfxcore_conf
Jul 21 17:48:47 gamebox lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Jul 21 17:48:47 gamebox lightdm: PAM adding faulty module: pam_kwallet.so
Jul 21 17:48:47 gamebox lightdm: PAM unable to dlopen(pam_kwallet5.so): /lib/security/pam_kwallet5.so: cannot open shared object file: No such file or directory
Jul 21 17:48:47 gamebox lightdm: PAM adding faulty module: pam_kwallet5.so
Jul 21 17:48:47 gamebox lightdm: pam_unix(lightdm-greeter:session): session opened for user lightdm by (uid=0)
Jul 21 17:48:47 gamebox systemd-logind[996]: New session c4 of user lightdm.
Jul 21 17:48:47 gamebox systemd[1]: Started Session c4 of user lightdm.
Jul 21 17:48:47 gamebox lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Jul 21 17:48:47 gamebox lightdm: PAM adding faulty module: pam_kwallet.so
Jul 21 17:48:47 gamebox lightdm: PAM unable to dlopen(pam_kwallet5.so): /lib/security/pam_kwallet5.so: cannot open shared object file: No such file or directory
Jul 21 17:48:47 gamebox lightdm: PAM adding faulty module: pam_kwallet5.so
Jul 21 17:48:47 gamebox lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "user"
Jul 21 17:50:27 gamebox systemd[1]: Stopping Session c2 of user lightdm.
Jul 21 17:50:27 gamebox systemd[1]: Stopping Session c4 of user lightdm.
Jul 21 17:50:27 gamebox systemd: pam_unix(systemd-user:session): session closed for user lightdm
```

---

### Post by #&amp;thj^% on 2017-07-21
This is something I have seen before:
```
Jul 21 17:48:46 gamebox gnome-session[2371]: gnome-session-is-accelerated: No hardware 3D support.
Jul 21 17:48:46 gamebox gnome-session[2371]: gnome-session-check-accelerated: Helper exited with code 256
Jul 21 17:48:46 gamebox gnome-session[2371]: gnome-session-binary[2371]: CRITICAL: We failed, but the fail whale is dead. Sorry....
Jul 21 17:48:46 gamebox gnome-session-binary[2371]: CRITICAL: We failed, but the fail whale is dead. Sorry....
```
First Report: [https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1274013](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1274013)
Here is the Old Bug report:[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1251281](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1251281)

The only work around I found was install another DE (XFCE)
**I would in your case uninstall the offending Kernel.**

---

### Post by DigiAngel on 2017-07-21
Sound advice...appreciate the look see thank you.

---

