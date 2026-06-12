---
title: "Multiseat - disable to logit twice after update to 18.06"
date: 2018-08-21
forum: Desktop Environments
---

### Post by hyp2 on 2018-08-21
Hallo,
after update to 18.04 from 16.04 I am not able login twice as same user. First login is ok, but  second seat is not OK a system login is looping. I am using xfce, but same situation is on ubuntu.
file .xsession-errors
```
dbus-update-activation-environment: setting DBUS_SESSION_BUS_ADDRESS=unix:path=$
dbus-update-activation-environment: setting XDG_RUNTIME_DIR=/run/user/1000
dbus-update-activation-environment: setting XAUTHORITY=/home/vh/.Xauthority
dbus-update-activation-environment: setting XDG_SESSION_PATH=/org/freedesktop/D$
dbus-update-activation-environment: setting XDG_CONFIG_DIRS=/etc/xdg/xdg-xfce:/$
dbus-update-activation-environment: setting PATH=/home/vh/bin:/home/vh/.local/b$
dbus-update-activation-environment: setting LD_PRELOAD=libgtk3-nocsd.so.0
dbus-update-activation-environment: setting _=/usr/bin/dbus-update-activation-e$
xfce4-session: Another session manager is already running
```
and file auth.log
```
9:45:16 Server polkitd(authority=local): Operator of unix-session:c3 successfully authenticated as unix-user:vh to gain ONE-SHOT authorization for action com.ubuntu.apport.apport-gtk-root for unix-process:1681:1577 [update-notifier] (owned by unix-user:vh)
Aug 18 09:45:16 Server pkexec: pam_unix(polkit-1:session): session opened for user root by (uid=1000)
Aug 18 09:45:16 Server pkexec[3031]: vh: Executing command [USER=root] [TTY=unknown] [CWD=/home/vh] [COMMAND=/usr/share/apport/apport-gtk]
Aug 18 09:52:45 Server sudo:       vh : TTY=pts/2 ; PWD=/home/vh ; USER=root ; COMMAND=/bin/nano
Aug 18 09:52:45 Server sudo: pam_unix(sudo:session): session opened for user root by (uid=0)
Aug 18 09:52:50 Server sudo: pam_unix(sudo:session): session closed for user root
Aug 18 09:52:55 Server sudo:       vh : TTY=pts/2 ; PWD=/home/vh ; USER=root ; COMMAND=/usr/bin/gedit
Aug 18 09:52:55 Server sudo: pam_unix(sudo:session): session opened for user root by (uid=0)
Aug 18 09:53:26 Server sudo: pam_unix(sudo:session): session closed for user root
Aug 18 09:53:28 Server sudo:       vh : TTY=pts/2 ; PWD=/home/vh ; USER=root ; COMMAND=/bin/nano
Aug 18 09:53:28 Server sudo: pam_unix(sudo:session): session opened for user root by (uid=0)
Aug 18 09:55:04 Server sudo: pam_unix(sudo:session): session closed for user root
Aug 18 09:55:06 Server sudo:       vh : TTY=pts/2 ; PWD=/home/vh ; USER=root ; COMMAND=/usr/bin/gedit
Aug 18 09:55:06 Server sudo: pam_unix(sudo:session): session opened for user root by (uid=0)
Aug 18 09:56:48 Server lightdm: pam_unix(lightdm:session): session opened for user vh by (uid=0)
Aug 18 09:56:48 Server systemd-logind[900]: New session c10 of user vh.
Aug 18 09:56:48 Server systemd-logind[900]: Removed session c9.
Aug 18 09:56:48 Server lightdm: pam_unix(lightdm:session): session closed for user vh
Aug 18 09:56:48 Server lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Aug 18 09:56:48 Server lightdm: PAM adding faulty module: pam_kwallet.so
Aug 18 09:56:48 Server lightdm: PAM unable to dlopen(pam_kwallet5.so): /lib/security/pam_kwallet5.so: cannot open shared object file: No such file or directory
Aug 18 09:56:48 Server lightdm: PAM adding faulty module: pam_kwallet5.so
Aug 18 09:56:48 Server lightdm: pam_unix(lightdm-greeter:session): session opened for user lightdm by (uid=0)
Aug 18 09:56:48 Server systemd-logind[900]: New session c11 of user lightdm.
Aug 18 09:56:48 Server systemd: pam_unix(systemd-user:session): session opened for user lightdm by (uid=0)
Aug 18 09:56:48 Server lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Aug 18 09:56:48 Server lightdm: PAM adding faulty module: pam_kwallet.so
Aug 18 09:56:48 Server lightdm: PAM unable to dlopen(pam_kwallet5.so): /lib/security/pam_kwallet5.so: cannot open shared object file: No such file or directory
Aug 18 09:56:48 Server lightdm: PAM adding faulty module: pam_kwallet5.so
Aug 18 09:56:48 Server lightdm: pam_succeed_if(lightdm:auth): incomplete condition detected
Aug 18 09:56:58 Server systemd-logind[900]: Removed session c10.
```
I dont know where could be mistake. In 16.04 everything work.

---

