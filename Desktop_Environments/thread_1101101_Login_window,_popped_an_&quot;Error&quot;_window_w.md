---
title: "Login window, popped an &quot;Error&quot; window with no message"
date: 2009-03-19
forum: Desktop Environments
---

### Post by cqhcp on 2009-03-19
In the login window, after input the password and Enter, popped an Error window with no message. I search the message in system log, but I can't find the error message. With this problem, the system hold when authenticate. The system need authenticate, when unlock the configure in the NetworkManager, but I haven't input the password, system pop an error message, said an error have occurred. In the "User Setting" window, also has this problem.

My mother language is not English, maybe the problem is not description clearly. 

Hao, Congping, come from china, thanks.

---

### Post by pytheas22 on 2009-03-19
I'm not sure I really understand your question.  You might want to try posting in the [Chinese forums for Ubuntu]("http://forum.ubuntu.org.cn/").

---

### Post by cqhcp on 2009-03-20
> **pytheas22 said:**
> I'm not sure I really understand your question.  You might want to try posting in the [Chinese forums for Ubuntu]("http://forum.ubuntu.org.cn/").

Yes, I had posted, 3 days ago, nobody give me any suggestion.

---

### Post by pytheas22 on 2009-03-20
> Yes, I had posted, 3 days ago, nobody give me any suggestion.

In that case, could you please switch your system temporarily to English, then copy here the error messages that you receive?  That will give me a better understanding of the problem.

---

### Post by cqhcp on 2009-03-20
> **pytheas22 said:**
> In that case, could you please switch your system temporarily to English, then copy here the error messages that you receive?  That will give me a better understanding of the problem.
I always use the ubuntu system in English environment, and I had try to switch system to Chinese environment, it's the same problem, after input the password and Enter, it's popped an Error window with no message(the message body is blank). Also, I had create an new user, then use the new user to login, it's the same problem. Maybe need reinstall some package? but witch package? I don't know.

Anyway, thanks for your suggestion.

---

### Post by pytheas22 on 2009-03-20
Please post the error messages (or a screenshot of them) in English.  I just need to see what the error message is so that I can know more specifically what's wrong.

---

### Post by cqhcp on 2009-03-24
> **pytheas22 said:**
> Please post the error messages (or a screenshot of them) in English.  I just need to see what the error message is so that I can know more specifically what's wrong.

Ok,
There are three issues, and they are occurred at the same time, so, I think, they are the same problem.
1.When login to GNOME, after input password and enter, popped an Error window with no message, no title. Before login to system, the PrintScreen button can't be use, so, I don't know how the print a screenshot before login.
2.When I use the "Unlock" in NetworkManager or Users Setting, after input the password and enter, popped and error message "Could not authenticate. An unexpected error has occurred."  
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=107456&stc=1&d=1237882135[/IMG]
3.In the terminal, when I use the sudo command, after input password and enter, terminal print an Error message.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=107457&stc=1&d=1237882135[/IMG]

I had triad these step, but error occurred still:
1.login use English language, or Chinese language.
2.create an new user, and use the new user to login.
3.remove the compiz package completely (this problem occurred after installed compiz, so, I think maybe it will be work after compiz package removed).
4.modify "/etc/init.d/rc", set CONCURRENCY=none
And I had triad some other ways in Google search.

---

### Post by pytheas22 on 2009-03-24
I think the problem is described in this [bug report]("https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/25931?comments=all").  It is caused because some system services do not start in the proper order.

The solution is to make sure that gdm is given priority 30 on system startup.  You can do that by typing these commands:
```

sudo mv /etc/rc2.d/*gdm /etc/rc2.d/30gdm
sudo mv /etc/rc3.d/*gdm /etc/rc3.d/30gdm
sudo mv /etc/rc4.d/*gdm /etc/rc4.d/30gdm
sudo mv /etc/rc5.d/*gdm /etc/rc5.d/30gdm
```

Then reboot.  Hopefully the problem will not occur.

If that doesn't help, please post the output of the command:
```

ls -al /etc/rc*.d
```

---

### Post by cqhcp on 2009-03-25
First run these commands
```

ls -l /etc/rc2.d/*gdm
ls -l /etc/rc3.d/*gdm
ls -l /etc/rc4.d/*gdm
ls -l /etc/rc5.d/*gdm

```
And the result is :
```

lrwxrwxrwx 1 root root 13 2008-01-24 22:32 /etc/rc2.d/S30gdm -> ../init.d/gdm
lrwxrwxrwx 1 root root 13 2008-01-24 22:32 /etc/rc3.d/S30gdm -> ../init.d/gdm
lrwxrwxrwx 1 root root 13 2008-01-24 22:32 /etc/rc4.d/S30gdm -> ../init.d/gdm
lrwxrwxrwx 1 root root 13 2008-01-24 22:32 /etc/rc5.d/S30gdm -> ../init.d/gdm

```


Then, I run these commands you give me:
```

sudo mv /etc/rc2.d/*gdm /etc/rc2.d/30gdm
sudo mv /etc/rc3.d/*gdm /etc/rc3.d/30gdm
sudo mv /etc/rc4.d/*gdm /etc/rc4.d/30gdm
sudo mv /etc/rc5.d/*gdm /etc/rc5.d/30gdm

```
Then, reboot the system. After reboot, the system can't start X system. The error message is "Set mode 1280 * 1024 failed...",and so on. In the terminal, login to system, then run command "startx", the X system started successful. I had tried two times.

Run the command 
```

ls -al /etc/rc*.d

```
The result is:
```

/etc/rc0.d:
total 16
drwxr-xr-x   2 root root 4096 2009-03-24 15:44 .
drwxr-xr-x 157 root root 8192 2009-03-25 14:43 ..
lrwxrwxrwx   1 root root   13 2008-01-24 22:32 K01gdm -> ../init.d/gdm
lrwxrwxrwx   1 root root   17 2008-01-24 22:32 K01usplash -> ../init.d/usplash
lrwxrwxrwx   1 root root   13 2009-03-20 10:30 K14mpd -> ../init.d/mpd
lrwxrwxrwx   1 root root   22 2008-01-24 22:32 K16avahi-daemon -> ../init.d/avahi-daemon
lrwxrwxrwx   1 root root   16 2008-01-24 22:32 K16dhcdbd -> ../init.d/dhcdbd
lrwxrwxrwx   1 root root   15 2008-01-29 14:32 K19samba -> ../init.d/samba
lrwxrwxrwx   1 root root   18 2009-02-19 16:59 K19sendmail -> ../init.d/sendmail
lrwxrwxrwx   1 root root   18 2009-03-06 14:21 K20ajaxterm -> ../init.d/ajaxterm
lrwxrwxrwx   1 root root   16 2008-01-24 22:32 K20apport -> ../init.d/apport
lrwxrwxrwx   1 root root   19 2009-03-11 09:58 K20ftp-proxy -> ../init.d/ftp-proxy
lrwxrwxrwx   1 root root   13 2009-03-16 10:01 K20inn -> ../init.d/inn
lrwxrwxrwx   1 root root   20 2009-03-03 13:56 K20nbd-server -> ../init.d/nbd-server
lrwxrwxrwx   1 root root   17 2009-03-16 11:20 K20sysstat -> ../init.d/sysstat
lrwxrwxrwx   1 root root   13 2008-01-28 11:57 K20vdr -> ../init.d/vdr
lrwxrwxrwx   1 root root   16 2009-02-19 16:04 K20xinetd -> ../init.d/xinetd
lrwxrwxrwx   1 root root   20 2009-02-11 05:45 K25hwclock.sh -> ../init.d/hwclock.sh
lrwxrwxrwx   1 root root   20 2008-01-24 22:32 K50alsa-utils -> ../init.d/alsa-utils
lrwxrwxrwx   1 root root   26 2008-01-24 22:32 K59mountoverflowtmp -> ../init.d/mountoverflowtmp
lrwxrwxrwx   1 root root   18 2009-02-19 15:00 K79quotarpc -> ../init.d/quotarpc
lrwxrwxrwx   1 root root   15 2009-02-19 15:00 K85quota -> ../init.d/quota
lrwxrwxrwx   1 root root   21 2008-01-24 22:32 K99laptop-mode -> ../init.d/laptop-mode
-rw-r--r--   1 root root  355 2009-01-23 23:01 README
lrwxrwxrwx   1 root root   41 2008-01-24 22:32 S01linux-restricted-modules-common -> ../init.d/linux-restricted-modules-common
lrwxrwxrwx   1 root root   22 2008-01-24 22:32 S15wpa-ifupdown -> ../init.d/wpa-ifupdown
lrwxrwxrwx   1 root root   18 2008-01-24 22:32 S20sendsigs -> ../init.d/sendsigs
lrwxrwxrwx   1 root root   17 2008-01-24 22:32 S30urandom -> ../init.d/urandom
lrwxrwxrwx   1 root root   22 2008-01-24 22:32 S31umountnfs.sh -> ../init.d/umountnfs.sh
lrwxrwxrwx   1 root root   18 2008-01-24 22:32 S40umountfs -> ../init.d/umountfs
lrwxrwxrwx   1 root root   20 2008-01-24 22:32 S60umountroot -> ../init.d/umountroot
lrwxrwxrwx   1 root root   14 2008-01-24 22:32 S90halt -> ../init.d/halt

/etc/rc1.d:
total 16
drwxr-xr-x   2 root root 4096 2009-03-24 15:44 .
drwxr-xr-x 157 root root 8192 2009-03-25 14:43 ..
lrwxrwxrwx   1 root root   13 2008-01-24 22:32 K01gdm -> ../init.d/gdm
lrwxrwxrwx   1 root root   17 2008-01-24 22:32 K01usplash -> ../init.d/usplash
lrwxrwxrwx   1 root root   17 2008-01-24 22:32 K11anacron -> ../init.d/anacron
lrwxrwxrwx   1 root root   13 2008-01-24 22:32 K11atd -> ../init.d/atd
lrwxrwxrwx   1 root root   14 2008-01-24 22:32 K11cron -> ../init.d/cron
lrwxrwxrwx   1 root root   13 2009-03-20 10:30 K14mpd -> ../init.d/mpd
lrwxrwxrwx   1 root root   20 2009-02-11 06:08 K15pulseaudio -> ../init.d/pulseaudio
lrwxrwxrwx   1 root root   22 2008-01-24 22:32 K16avahi-daemon -> ../init.d/avahi-daemon
lrwxrwxrwx   1 root root   16 2008-01-24 22:32 K16dhcdbd -> ../init.d/dhcdbd
lrwxrwxrwx   1 root root   13 2009-02-11 08:19 K16hal -> ../init.d/hal
lrwxrwxrwx   1 root root   16 2008-01-24 22:32 K19cupsys -> ../init.d/cupsys
lrwxrwxrwx   1 root root   15 2008-01-29 14:32 K19samba -> ../init.d/samba
lrwxrwxrwx   1 root root   18 2009-02-19 16:59 K19sendmail -> ../init.d/sendmail
lrwxrwxrwx   1 root root   14 2009-03-16 10:56 K20acct -> ../init.d/acct
lrwxrwxrwx   1 root root   22 2008-01-24 22:32 K20acpi-support -> ../init.d/acpi-support
lrwxrwxrwx   1 root root   18 2009-03-06 14:21 K20ajaxterm -> ../init.d/ajaxterm
lrwxrwxrwx   1 root root   14 2008-01-24 22:32 K20apmd -> ../init.d/apmd
lrwxrwxrwx   1 root root   16 2008-01-24 22:32 K20apport -> ../init.d/apport
lrwxrwxrwx   1 root root   19 2009-03-11 09:58 K20ftp-proxy -> ../init.d/ftp-proxy
lrwxrwxrwx   1 root root   22 2008-01-24 22:32 K20hotkey-setup -> ../init.d/hotkey-setup
lrwxrwxrwx   1 root root   13 2009-03-16 10:01 K20inn -> ../init.d/inn
lrwxrwxrwx   1 root root   17 2008-01-24 22:32 K20makedev -> ../init.d/makedev
lrwxrwxrwx   1 root root   20 2009-03-03 13:56 K20nbd-server -> ../init.d/nbd-server
lrwxrwxrwx   1 root root   23 2008-01-24 22:32 K20nvidia-kernel -> ../init.d/nvidia-kernel
lrwxrwxrwx   1 root root   19 2008-01-24 22:32 K20powernowd -> ../init.d/powernowd
lrwxrwxrwx   1 root root   15 2008-01-24 22:32 K20rsync -> ../init.d/rsync
lrwxrwxrwx   1 root root   17 2009-03-16 11:20 K20sysstat -> ../init.d/sysstat
lrwxrwxrwx   1 root root   19 2009-03-03 13:56 K20tftpd-hpa -> ../init.d/tftpd-hpa
lrwxrwxrwx   1 root root   13 2008-01-28 11:57 K20vdr -> ../init.d/vdr
lrwxrwxrwx   1 root root   16 2009-02-19 16:04 K20xinetd -> ../init.d/xinetd
lrwxrwxrwx   1 root root   15 2008-01-24 22:32 K21acpid -> ../init.d/acpid
lrwxrwxrwx   1 root root   13 2009-02-11 08:11 K39ufw -> ../init.d/ufw
lrwxrwxrwx   1 root root   22 2009-03-03 13:56 K40dhcp3-server -> ../init.d/dhcp3-server
lrwxrwxrwx   1 root root   19 2008-01-24 22:32 K74bluetooth -> ../init.d/bluetooth
lrwxrwxrwx   1 root root   18 2009-02-19 15:00 K79quotarpc -> ../init.d/quotarpc
lrwxrwxrwx   1 root root   13 2009-03-03 13:56 K84ssh -> ../init.d/ssh
lrwxrwxrwx   1 root root   14 2009-02-11 08:18 K88dbus -> ../init.d/dbus
lrwxrwxrwx   1 root root   15 2008-01-24 22:32 K89klogd -> ../init.d/klogd
lrwxrwxrwx   1 root root   18 2008-01-24 22:32 K90sysklogd -> ../init.d/sysklogd
lrwxrwxrwx   1 root root   21 2008-01-24 22:32 K99laptop-mode -> ../init.d/laptop-mode
lrwxrwxrwx   1 root root   19 2009-02-11 08:19 K99policykit -> ../init.d/policykit
-rw-r--r--   1 root root  371 2009-01-23 23:01 README
lrwxrwxrwx   1 root root   19 2008-01-24 22:32 S30killprocs -> ../init.d/killprocs
lrwxrwxrwx   1 root root   16 2008-01-24 22:32 S90single -> ../init.d/single

/etc/rc2.d:
total 16
drwxr-xr-x   2 root root 4096 2009-03-25 14:37 .
drwxr-xr-x 157 root root 8192 2009-03-25 14:43 ..
lrwxrwxrwx   1 root root   13 2008-01-24 22:32 30gdm -> ../init.d/gdm
lrwxrwxrwx   1 root root   18 2009-02-25 18:58 K19sendmail -> ../init.d/sendmail
-rw-r--r--   1 root root  556 2009-01-23 23:01 README
lrwxrwxrwx   1 root root   19 2009-02-11 08:19 S01policykit -> ../init.d/policykit
lrwxrwxrwx   1 root root   17 2008-01-24 22:32 S05vbesave -> ../init.d/vbesave
lrwxrwxrwx   1 root root   15 2008-01-24 22:32 S10acpid -> ../init.d/acpid
lrwxrwxrwx   1 root root   25 2008-01-24 22:32 S10powernowd.early -> ../init.d/powernowd.early
lrwxrwxrwx   1 root root   18 2008-01-24 22:32 S10sysklogd -> ../init.d/sysklogd
lrwxrwxrwx   1 root root   34 2008-01-24 22:32 S10xserver-xorg-input-wacom -> ../init.d/xserver-xorg-input-wacom
lrwxrwxrwx   1 root root   15 2008-01-24 22:32 S11klogd -> ../init.d/klogd
lrwxrwxrwx   1 root root   14 2009-02-11 08:18 S12dbus -> ../init.d/dbus
lrwxrwxrwx   1 root root   13 2009-03-03 13:56 S16ssh -> ../init.d/ssh
lrwxrwxrwx   1 root root   22 2008-01-24 22:32 S18avahi-daemon -> ../init.d/avahi-daemon
lrwxrwxrwx   1 root root   16 2008-01-24 22:32 S19cupsys -> ../init.d/cupsys
lrwxrwxrwx   1 root root   14 2009-03-16 10:56 S20acct -> ../init.d/acct
lrwxrwxrwx   1 root root   18 2009-03-06 14:21 S20ajaxterm -> ../init.d/ajaxterm
lrwxrwxrwx   1 root root   14 2008-01-24 22:32 S20apmd -> ../init.d/apmd
lrwxrwxrwx   1 root root   16 2008-01-24 22:32 S20apport -> ../init.d/apport
lrwxrwxrwx   1 root root   19 2009-03-11 09:58 S20ftp-proxy -> ../init.d/ftp-proxy
lrwxrwxrwx   1 root root   22 2008-01-24 22:32 S20hotkey-setup -> ../init.d/hotkey-setup
lrwxrwxrwx   1 root root   13 2009-03-16 10:01 S20inn -> ../init.d/inn
lrwxrwxrwx   1 root root   17 2008-01-24 22:32 S20makedev -> ../init.d/makedev
lrwxrwxrwx   1 root root   20 2009-03-03 13:56 S20nbd-server -> ../init.d/nbd-server
lrwxrwxrwx   1 root root   23 2008-01-24 22:32 S20nvidia-kernel -> ../init.d/nvidia-kernel
lrwxrwxrwx   1 root root   19 2008-01-24 22:32 S20powernowd -> ../init.d/powernowd
lrwxrwxrwx   1 root root   15 2008-01-24 22:32 S20rsync -> ../init.d/rsync
lrwxrwxrwx   1 root root   15 2008-01-29 14:32 S20samba -> ../init.d/samba
lrwxrwxrwx   1 root root   17 2009-03-16 11:20 S20sysstat -> ../init.d/sysstat
lrwxrwxrwx   1 root root   19 2009-03-03 13:56 S20tftpd-hpa -> ../init.d/tftpd-hpa
lrwxrwxrwx   1 root root   13 2008-01-28 11:57 S20vdr -> ../init.d/vdr
lrwxrwxrwx   1 root root   16 2009-02-19 16:04 S20xinetd -> ../init.d/xinetd
lrwxrwxrwx   1 root root   18 2009-02-19 15:00 S21quotarpc -> ../init.d/quotarpc
lrwxrwxrwx   1 root root   16 2008-01-24 22:32 S24dhcdbd -> ../init.d/dhcdbd
lrwxrwxrwx   1 root root   13 2009-02-11 08:19 S24hal -> ../init.d/hal
lrwxrwxrwx   1 root root   19 2008-01-24 22:32 S25bluetooth -> ../init.d/bluetooth
lrwxrwxrwx   1 root root   20 2009-02-11 06:08 S25pulseaudio -> ../init.d/pulseaudio
lrwxrwxrwx   1 root root   13 2009-03-20 10:30 S30mpd -> ../init.d/mpd
lrwxrwxrwx   1 root root   22 2009-03-03 13:56 S40dhcp3-server -> ../init.d/dhcp3-server
lrwxrwxrwx   1 root root   17 2008-01-24 22:32 S89anacron -> ../init.d/anacron
lrwxrwxrwx   1 root root   13 2008-01-24 22:32 S89atd -> ../init.d/atd
lrwxrwxrwx   1 root root   14 2008-01-24 22:32 S89cron -> ../init.d/cron
lrwxrwxrwx   1 root root   24 2008-01-30 16:26 S90binfmt-support -> ../init.d/binfmt-support
lrwxrwxrwx   1 root root   17 2008-01-24 22:32 S98usplash -> ../init.d/usplash
lrwxrwxrwx   1 root root   22 2008-01-24 22:32 S99acpi-support -> ../init.d/acpi-support
lrwxrwxrwx   1 root root   21 2008-01-24 22:32 S99laptop-mode -> ../init.d/laptop-mode
lrwxrwxrwx   1 root root   18 2008-01-24 22:32 S99rc.local -> ../init.d/rc.local
lrwxrwxrwx   1 root root   19 2008-01-24 22:32 S99rmnologin -> ../init.d/rmnologin
lrwxrwxrwx   1 root root   24 2009-03-18 09:28 S99stop-bootchart -> ../init.d/stop-bootchart
lrwxrwxrwx   1 root root   24 2008-01-24 22:32 S99stop-readahead -> ../init.d/stop-readahead

/etc/rc3.d:
total 16
drwxr-xr-x   2 root root 4096 2009-03-25 14:37 .
drwxr-xr-x 157 root root 8192 2009-03-25 14:43 ..
lrwxrwxrwx   1 root root   13 2008-01-24 22:32 30gdm -> ../init.d/gdm
lrwxrwxrwx   1 root root   18 2009-02-25 18:58 K19sendmail -> ../init.d/sendmail
-rw-r--r--   1 root root  556 2009-01-23 23:01 README
lrwxrwxrwx   1 root root   19 2009-02-11 08:19 S01policykit -> ../init.d/policykit
lrwxrwxrwx   1 root root   17 2008-01-24 22:32 S05vbesave -> ../init.d/vbesave
lrwxrwxrwx   1 root root   15 2008-01-24 22:32 S10acpid -> ../init.d/acpid
lrwxrwxrwx   1 root root   18 2008-01-24 22:32 S10sysklogd -> ../init.d/sysklogd
lrwxrwxrwx   1 root root   34 2008-01-24 22:32 S10xserver-xorg-input-wacom -> ../init.d/xserver-xorg-input-wacom
lrwxrwxrwx   1 root root   15 2008-01-24 22:32 S11klogd -> ../init.d/klogd
lrwxrwxrwx   1 root root   14 2009-02-11 08:18 S12dbus -> ../init.d/dbus
lrwxrwxrwx   1 root root   13 2009-03-03 13:56 S16ssh -> ../init.d/ssh
lrwxrwxrwx   1 root root   22 2008-01-24 22:32 S18avahi-daemon -> ../init.d/avahi-daemon
lrwxrwxrwx   1 root root   16 2008-01-24 22:32 S19cupsys -> ../init.d/cupsys
lrwxrwxrwx   1 root root   14 2009-03-16 10:56 S20acct -> ../init.d/acct
lrwxrwxrwx   1 root root   18 2009-03-06 14:21 S20ajaxterm -> ../init.d/ajaxterm
lrwxrwxrwx   1 root root   14 2008-01-24 22:32 S20apmd -> ../init.d/apmd
lrwxrwxrwx   1 root root   16 2008-01-24 22:32 S20apport -> ../init.d/apport
lrwxrwxrwx   1 root root   19 2009-03-11 09:58 S20ftp-proxy -> ../init.d/ftp-proxy
lrwxrwxrwx   1 root root   22 2008-01-24 22:32 S20hotkey-setup -> ../init.d/hotkey-setup
lrwxrwxrwx   1 root root   13 2009-03-16 10:01 S20inn -> ../init.d/inn
lrwxrwxrwx   1 root root   17 2008-01-24 22:32 S20makedev -> ../init.d/makedev
lrwxrwxrwx   1 root root   20 2009-03-03 13:56 S20nbd-server -> ../init.d/nbd-server
lrwxrwxrwx   1 root root   23 2008-01-24 22:32 S20nvidia-kernel -> ../init.d/nvidia-kernel
lrwxrwxrwx   1 root root   19 2008-01-24 22:32 S20powernowd -> ../init.d/powernowd
lrwxrwxrwx   1 root root   15 2008-01-24 22:32 S20rsync -> ../init.d/rsync
lrwxrwxrwx   1 root root   15 2008-01-29 14:32 S20samba -> ../init.d/samba
lrwxrwxrwx   1 root root   17 2009-03-16 11:20 S20sysstat -> ../init.d/sysstat
lrwxrwxrwx   1 root root   19 2009-03-03 13:56 S20tftpd-hpa -> ../init.d/tftpd-hpa
lrwxrwxrwx   1 root root   13 2008-01-28 11:57 S20vdr -> ../init.d/vdr
lrwxrwxrwx   1 root root   16 2009-02-19 16:04 S20xinetd -> ../init.d/xinetd
lrwxrwxrwx   1 root root   18 2009-02-19 15:00 S21quotarpc -> ../init.d/quotarpc
lrwxrwxrwx   1 root root   16 2008-01-24 22:32 S24dhcdbd -> ../init.d/dhcdbd
lrwxrwxrwx   1 root root   13 2009-02-11 08:19 S24hal -> ../init.d/hal
lrwxrwxrwx   1 root root   19 2008-01-24 22:32 S25bluetooth -> ../init.d/bluetooth
lrwxrwxrwx   1 root root   20 2009-02-11 06:08 S25pulseaudio -> ../init.d/pulseaudio
lrwxrwxrwx   1 root root   13 2009-03-20 10:30 S30mpd -> ../init.d/mpd
lrwxrwxrwx   1 root root   22 2009-03-03 13:56 S40dhcp3-server -> ../init.d/dhcp3-server
lrwxrwxrwx   1 root root   17 2008-01-24 22:32 S89anacron -> ../init.d/anacron
lrwxrwxrwx   1 root root   13 2008-01-24 22:32 S89atd -> ../init.d/atd
lrwxrwxrwx   1 root root   14 2008-01-24 22:32 S89cron -> ../init.d/cron
lrwxrwxrwx   1 root root   24 2008-01-30 16:26 S90binfmt-support -> ../init.d/binfmt-support
lrwxrwxrwx   1 root root   17 2008-01-24 22:32 S98usplash -> ../init.d/usplash
lrwxrwxrwx   1 root root   22 2008-01-24 22:32 S99acpi-support -> ../init.d/acpi-support
lrwxrwxrwx   1 root root   21 2008-01-24 22:32 S99laptop-mode -> ../init.d/laptop-mode
lrwxrwxrwx   1 root root   18 2008-01-24 22:32 S99rc.local -> ../init.d/rc.local
lrwxrwxrwx   1 root root   19 2008-01-24 22:32 S99rmnologin -> ../init.d/rmnologin
lrwxrwxrwx   1 root root   24 2009-03-18 09:28 S99stop-bootchart -> ../init.d/stop-bootchart

/etc/rc4.d:
total 16
drwxr-xr-x   2 root root 4096 2009-03-25 14:37 .
drwxr-xr-x 157 root root 8192 2009-03-25 14:43 ..
lrwxrwxrwx   1 root root   13 2008-01-24 22:32 30gdm -> ../init.d/gdm
lrwxrwxrwx   1 root root   18 2009-02-25 18:58 K19sendmail -> ../init.d/sendmail
-rw-r--r--   1 root root  556 2009-01-23 23:01 README
lrwxrwxrwx   1 root root   19 2009-02-11 08:19 S01policykit -> ../init.d/policykit
lrwxrwxrwx   1 root root   17 2008-01-24 22:32 S05vbesave -> ../init.d/vbesave
lrwxrwxrwx   1 root root   15 2008-01-24 22:32 S10acpid -> ../init.d/acpid
lrwxrwxrwx   1 root root   18 2008-01-24 22:32 S10sysklogd -> ../init.d/sysklogd
lrwxrwxrwx   1 root root   34 2008-01-24 22:32 S10xserver-xorg-input-wacom -> ../init.d/xserver-xorg-input-wacom
lrwxrwxrwx   1 root root   15 2008-01-24 22:32 S11klogd -> ../init.d/klogd
lrwxrwxrwx   1 root root   14 2009-02-11 08:18 S12dbus -> ../init.d/dbus
lrwxrwxrwx   1 root root   13 2009-03-03 13:56 S16ssh -> ../init.d/ssh
lrwxrwxrwx   1 root root   22 2008-01-24 22:32 S18avahi-daemon -> ../init.d/avahi-daemon
lrwxrwxrwx   1 root root   16 2008-01-24 22:32 S19cupsys -> ../init.d/cupsys
lrwxrwxrwx   1 root root   14 2009-03-16 10:56 S20acct -> ../init.d/acct
lrwxrwxrwx   1 root root   18 2009-03-06 14:21 S20ajaxterm -> ../init.d/ajaxterm
lrwxrwxrwx   1 root root   14 2008-01-24 22:32 S20apmd -> ../init.d/apmd
lrwxrwxrwx   1 root root   16 2008-01-24 22:32 S20apport -> ../init.d/apport
lrwxrwxrwx   1 root root   19 2009-03-11 09:58 S20ftp-proxy -> ../init.d/ftp-proxy
lrwxrwxrwx   1 root root   22 2008-01-24 22:32 S20hotkey-setup -> ../init.d/hotkey-setup
lrwxrwxrwx   1 root root   13 2009-03-16 10:01 S20inn -> ../init.d/inn
lrwxrwxrwx   1 root root   17 2008-01-24 22:32 S20makedev -> ../init.d/makedev
lrwxrwxrwx   1 root root   20 2009-03-03 13:56 S20nbd-server -> ../init.d/nbd-server
lrwxrwxrwx   1 root root   23 2008-01-24 22:32 S20nvidia-kernel -> ../init.d/nvidia-kernel
lrwxrwxrwx   1 root root   19 2008-01-24 22:32 S20powernowd -> ../init.d/powernowd
lrwxrwxrwx   1 root root   15 2008-01-24 22:32 S20rsync -> ../init.d/rsync
lrwxrwxrwx   1 root root   15 2008-01-29 14:32 S20samba -> ../init.d/samba
lrwxrwxrwx   1 root root   17 2009-03-16 11:20 S20sysstat -> ../init.d/sysstat
lrwxrwxrwx   1 root root   19 2009-03-03 13:56 S20tftpd-hpa -> ../init.d/tftpd-hpa
lrwxrwxrwx   1 root root   13 2008-01-28 11:57 S20vdr -> ../init.d/vdr
lrwxrwxrwx   1 root root   16 2009-02-19 16:04 S20xinetd -> ../init.d/xinetd
lrwxrwxrwx   1 root root   18 2009-02-19 15:00 S21quotarpc -> ../init.d/quotarpc
lrwxrwxrwx   1 root root   16 2008-01-24 22:32 S24dhcdbd -> ../init.d/dhcdbd
lrwxrwxrwx   1 root root   13 2009-02-11 08:19 S24hal -> ../init.d/hal
lrwxrwxrwx   1 root root   19 2008-01-24 22:32 S25bluetooth -> ../init.d/bluetooth
lrwxrwxrwx   1 root root   20 2009-02-11 06:08 S25pulseaudio -> ../init.d/pulseaudio
lrwxrwxrwx   1 root root   13 2009-03-20 10:30 S30mpd -> ../init.d/mpd
lrwxrwxrwx   1 root root   22 2009-03-03 13:56 S40dhcp3-server -> ../init.d/dhcp3-server
lrwxrwxrwx   1 root root   17 2008-01-24 22:32 S89anacron -> ../init.d/anacron
lrwxrwxrwx   1 root root   13 2008-01-24 22:32 S89atd -> ../init.d/atd
lrwxrwxrwx   1 root root   14 2008-01-24 22:32 S89cron -> ../init.d/cron
lrwxrwxrwx   1 root root   24 2008-01-30 16:26 S90binfmt-support -> ../init.d/binfmt-support
lrwxrwxrwx   1 root root   17 2008-01-24 22:32 S98usplash -> ../init.d/usplash
lrwxrwxrwx   1 root root   22 2008-01-24 22:32 S99acpi-support -> ../init.d/acpi-support
lrwxrwxrwx   1 root root   21 2008-01-24 22:32 S99laptop-mode -> ../init.d/laptop-mode
lrwxrwxrwx   1 root root   18 2008-01-24 22:32 S99rc.local -> ../init.d/rc.local
lrwxrwxrwx   1 root root   19 2008-01-24 22:32 S99rmnologin -> ../init.d/rmnologin
lrwxrwxrwx   1 root root   24 2009-03-18 09:28 S99stop-bootchart -> ../init.d/stop-bootchart

/etc/rc5.d:
total 16
drwxr-xr-x   2 root root 4096 2009-03-25 14:38 .
drwxr-xr-x 157 root root 8192 2009-03-25 14:43 ..
lrwxrwxrwx   1 root root   13 2008-01-24 22:32 30gdm -> ../init.d/gdm
lrwxrwxrwx   1 root root   18 2009-02-25 18:58 K19sendmail -> ../init.d/sendmail
-rw-r--r--   1 root root  556 2009-01-23 23:01 README
lrwxrwxrwx   1 root root   19 2009-02-11 08:19 S01policykit -> ../init.d/policykit
lrwxrwxrwx   1 root root   17 2008-01-24 22:32 S05vbesave -> ../init.d/vbesave
lrwxrwxrwx   1 root root   15 2008-01-24 22:32 S10acpid -> ../init.d/acpid
lrwxrwxrwx   1 root root   18 2008-01-24 22:32 S10sysklogd -> ../init.d/sysklogd
lrwxrwxrwx   1 root root   34 2008-01-24 22:32 S10xserver-xorg-input-wacom -> ../init.d/xserver-xorg-input-wacom
lrwxrwxrwx   1 root root   15 2008-01-24 22:32 S11klogd -> ../init.d/klogd
lrwxrwxrwx   1 root root   14 2009-02-11 08:18 S12dbus -> ../init.d/dbus
lrwxrwxrwx   1 root root   13 2009-03-03 13:56 S16ssh -> ../init.d/ssh
lrwxrwxrwx   1 root root   22 2008-01-24 22:32 S18avahi-daemon -> ../init.d/avahi-daemon
lrwxrwxrwx   1 root root   16 2008-01-24 22:32 S19cupsys -> ../init.d/cupsys
lrwxrwxrwx   1 root root   14 2009-03-16 10:56 S20acct -> ../init.d/acct
lrwxrwxrwx   1 root root   18 2009-03-06 14:21 S20ajaxterm -> ../init.d/ajaxterm
lrwxrwxrwx   1 root root   14 2008-01-24 22:32 S20apmd -> ../init.d/apmd
lrwxrwxrwx   1 root root   16 2008-01-24 22:32 S20apport -> ../init.d/apport
lrwxrwxrwx   1 root root   19 2009-03-11 09:58 S20ftp-proxy -> ../init.d/ftp-proxy
lrwxrwxrwx   1 root root   22 2008-01-24 22:32 S20hotkey-setup -> ../init.d/hotkey-setup
lrwxrwxrwx   1 root root   13 2009-03-16 10:01 S20inn -> ../init.d/inn
lrwxrwxrwx   1 root root   17 2008-01-24 22:32 S20makedev -> ../init.d/makedev
lrwxrwxrwx   1 root root   20 2009-03-03 13:56 S20nbd-server -> ../init.d/nbd-server
lrwxrwxrwx   1 root root   23 2008-01-24 22:32 S20nvidia-kernel -> ../init.d/nvidia-kernel
lrwxrwxrwx   1 root root   19 2008-01-24 22:32 S20powernowd -> ../init.d/powernowd
lrwxrwxrwx   1 root root   15 2008-01-24 22:32 S20rsync -> ../init.d/rsync
lrwxrwxrwx   1 root root   15 2008-01-29 14:32 S20samba -> ../init.d/samba
lrwxrwxrwx   1 root root   17 2009-03-16 11:20 S20sysstat -> ../init.d/sysstat
lrwxrwxrwx   1 root root   19 2009-03-03 13:56 S20tftpd-hpa -> ../init.d/tftpd-hpa
lrwxrwxrwx   1 root root   13 2008-01-28 11:57 S20vdr -> ../init.d/vdr
lrwxrwxrwx   1 root root   16 2009-02-19 16:04 S20xinetd -> ../init.d/xinetd
lrwxrwxrwx   1 root root   18 2009-02-19 15:00 S21quotarpc -> ../init.d/quotarpc
lrwxrwxrwx   1 root root   16 2008-01-24 22:32 S24dhcdbd -> ../init.d/dhcdbd
lrwxrwxrwx   1 root root   13 2009-02-11 08:19 S24hal -> ../init.d/hal
lrwxrwxrwx   1 root root   19 2008-01-24 22:32 S25bluetooth -> ../init.d/bluetooth
lrwxrwxrwx   1 root root   20 2009-02-11 06:08 S25pulseaudio -> ../init.d/pulseaudio
lrwxrwxrwx   1 root root   13 2009-03-20 10:30 S30mpd -> ../init.d/mpd
lrwxrwxrwx   1 root root   22 2009-03-03 13:56 S40dhcp3-server -> ../init.d/dhcp3-server
lrwxrwxrwx   1 root root   17 2008-01-24 22:32 S89anacron -> ../init.d/anacron
lrwxrwxrwx   1 root root   13 2008-01-24 22:32 S89atd -> ../init.d/atd
lrwxrwxrwx   1 root root   14 2008-01-24 22:32 S89cron -> ../init.d/cron
lrwxrwxrwx   1 root root   24 2008-01-30 16:26 S90binfmt-support -> ../init.d/binfmt-support
lrwxrwxrwx   1 root root   17 2008-01-24 22:32 S98usplash -> ../init.d/usplash
lrwxrwxrwx   1 root root   22 2008-01-24 22:32 S99acpi-support -> ../init.d/acpi-support
lrwxrwxrwx   1 root root   21 2008-01-24 22:32 S99laptop-mode -> ../init.d/laptop-mode
lrwxrwxrwx   1 root root   18 2008-01-24 22:32 S99rc.local -> ../init.d/rc.local
lrwxrwxrwx   1 root root   19 2008-01-24 22:32 S99rmnologin -> ../init.d/rmnologin
lrwxrwxrwx   1 root root   24 2009-03-18 09:28 S99stop-bootchart -> ../init.d/stop-bootchart

/etc/rc6.d:
total 16
drwxr-xr-x   2 root root 4096 2009-03-24 15:44 .
drwxr-xr-x 157 root root 8192 2009-03-25 14:43 ..
lrwxrwxrwx   1 root root   13 2008-01-24 22:32 K01gdm -> ../init.d/gdm
lrwxrwxrwx   1 root root   17 2008-01-24 22:32 K01usplash -> ../init.d/usplash
lrwxrwxrwx   1 root root   13 2009-03-20 10:30 K14mpd -> ../init.d/mpd
lrwxrwxrwx   1 root root   22 2008-01-24 22:32 K16avahi-daemon -> ../init.d/avahi-daemon
lrwxrwxrwx   1 root root   16 2008-01-24 22:32 K16dhcdbd -> ../init.d/dhcdbd
lrwxrwxrwx   1 root root   15 2008-01-29 14:32 K19samba -> ../init.d/samba
lrwxrwxrwx   1 root root   18 2009-02-19 16:59 K19sendmail -> ../init.d/sendmail
lrwxrwxrwx   1 root root   18 2009-03-06 14:21 K20ajaxterm -> ../init.d/ajaxterm
lrwxrwxrwx   1 root root   16 2008-01-24 22:32 K20apport -> ../init.d/apport
lrwxrwxrwx   1 root root   19 2009-03-11 09:58 K20ftp-proxy -> ../init.d/ftp-proxy
lrwxrwxrwx   1 root root   13 2009-03-16 10:01 K20inn -> ../init.d/inn
lrwxrwxrwx   1 root root   20 2009-03-03 13:56 K20nbd-server -> ../init.d/nbd-server
lrwxrwxrwx   1 root root   17 2009-03-16 11:20 K20sysstat -> ../init.d/sysstat
lrwxrwxrwx   1 root root   13 2008-01-28 11:57 K20vdr -> ../init.d/vdr
lrwxrwxrwx   1 root root   16 2009-02-19 16:04 K20xinetd -> ../init.d/xinetd
lrwxrwxrwx   1 root root   20 2009-02-11 05:45 K25hwclock.sh -> ../init.d/hwclock.sh
lrwxrwxrwx   1 root root   20 2008-01-24 22:32 K50alsa-utils -> ../init.d/alsa-utils
lrwxrwxrwx   1 root root   26 2008-01-24 22:32 K59mountoverflowtmp -> ../init.d/mountoverflowtmp
lrwxrwxrwx   1 root root   18 2009-02-19 15:00 K79quotarpc -> ../init.d/quotarpc
lrwxrwxrwx   1 root root   15 2009-02-19 15:00 K85quota -> ../init.d/quota
lrwxrwxrwx   1 root root   21 2008-01-24 22:32 K99laptop-mode -> ../init.d/laptop-mode
-rw-r--r--   1 root root  353 2009-01-23 23:01 README
lrwxrwxrwx   1 root root   41 2008-01-24 22:32 S01linux-restricted-modules-common -> ../init.d/linux-restricted-modules-common
lrwxrwxrwx   1 root root   22 2008-01-24 22:32 S15wpa-ifupdown -> ../init.d/wpa-ifupdown
lrwxrwxrwx   1 root root   18 2008-01-24 22:32 S20sendsigs -> ../init.d/sendsigs
lrwxrwxrwx   1 root root   17 2008-01-24 22:32 S30urandom -> ../init.d/urandom
lrwxrwxrwx   1 root root   22 2008-01-24 22:32 S31umountnfs.sh -> ../init.d/umountnfs.sh
lrwxrwxrwx   1 root root   18 2008-01-24 22:32 S40umountfs -> ../init.d/umountfs
lrwxrwxrwx   1 root root   20 2008-01-24 22:32 S60umountroot -> ../init.d/umountroot
lrwxrwxrwx   1 root root   16 2008-01-24 22:32 S90reboot -> ../init.d/reboot

/etc/rcS.d:
total 16
drwxr-xr-x   2 root root 4096 2009-02-19 15:00 .
drwxr-xr-x 157 root root 8192 2009-03-25 14:43 ..
-rw-r--r--   1 root root  785 2009-01-23 23:01 README
lrwxrwxrwx   1 root root   24 2008-01-24 22:32 S01mountkernfs.sh -> ../init.d/mountkernfs.sh
lrwxrwxrwx   1 root root   19 2008-01-24 22:32 S01readahead -> ../init.d/readahead
lrwxrwxrwx   1 root root   21 2008-01-24 22:32 S02hostname.sh -> ../init.d/hostname.sh
lrwxrwxrwx   1 root root   24 2008-01-24 22:32 S06keyboard-setup -> ../init.d/keyboard-setup
lrwxrwxrwx   1 root root   41 2008-01-24 22:32 S07linux-restricted-modules-common -> ../init.d/linux-restricted-modules-common
lrwxrwxrwx   1 root root   25 2009-02-11 05:45 S08hwclockfirst.sh -> ../init.d/hwclockfirst.sh
lrwxrwxrwx   1 root root   18 2008-01-24 22:32 S08loopback -> ../init.d/loopback
lrwxrwxrwx   1 root root   14 2008-01-24 22:32 S10udev -> ../init.d/udev
lrwxrwxrwx   1 root root   20 2009-02-11 05:45 S11hwclock.sh -> ../init.d/hwclock.sh
lrwxrwxrwx   1 root root   26 2008-01-24 22:32 S11mountdevsubfs.sh -> ../init.d/mountdevsubfs.sh
lrwxrwxrwx   1 root root   21 2008-01-24 22:32 S13pcmciautils -> ../init.d/pcmciautils
lrwxrwxrwx   1 root root   27 2008-01-24 22:32 S15module-init-tools -> ../init.d/module-init-tools
lrwxrwxrwx   1 root root   16 2009-02-11 05:57 S17procps -> ../init.d/procps
lrwxrwxrwx   1 root root   22 2008-01-24 22:32 S20checkroot.sh -> ../init.d/checkroot.sh
lrwxrwxrwx   1 root root   17 2008-01-24 22:32 S22mtab.sh -> ../init.d/mtab.sh
lrwxrwxrwx   1 root root   16 2008-01-24 22:32 S25brltty -> ../init.d/brltty
lrwxrwxrwx   1 root root   20 2008-01-24 22:32 S30checkfs.sh -> ../init.d/checkfs.sh
lrwxrwxrwx   1 root root   21 2008-01-24 22:32 S35mountall.sh -> ../init.d/mountall.sh
lrwxrwxrwx   1 root root   15 2009-02-19 15:00 S35quota -> ../init.d/quota
lrwxrwxrwx   1 root root   31 2008-01-24 22:32 S36mountall-bootclean.sh -> ../init.d/mountall-bootclean.sh
lrwxrwxrwx   1 root root   18 2008-01-24 22:32 S37apparmor -> ../init.d/apparmor
lrwxrwxrwx   1 root root   26 2008-01-24 22:32 S37mountoverflowtmp -> ../init.d/mountoverflowtmp
lrwxrwxrwx   1 root root   21 2008-01-24 22:32 S37udev-finish -> ../init.d/udev-finish
lrwxrwxrwx   1 root root   27 2008-01-24 22:32 S39readahead-desktop -> ../init.d/readahead-desktop
lrwxrwxrwx   1 root root   13 2009-02-11 08:11 S39ufw -> ../init.d/ufw
lrwxrwxrwx   1 root root   20 2008-01-24 22:32 S40networking -> ../init.d/networking
lrwxrwxrwx   1 root root   20 2008-01-24 22:32 S45waitnfs.sh -> ../init.d/waitnfs.sh
lrwxrwxrwx   1 root root   27 2008-01-24 22:32 S46libpam-foreground -> ../init.d/libpam-foreground
lrwxrwxrwx   1 root root   31 2008-01-24 22:32 S46mountnfs-bootclean.sh -> ../init.d/mountnfs-bootclean.sh
lrwxrwxrwx   1 root root   23 2008-01-24 22:32 S49console-setup -> ../init.d/console-setup
lrwxrwxrwx   1 root root   19 2008-01-24 22:32 S55dns-clean -> ../init.d/dns-clean
lrwxrwxrwx   1 root root   18 2008-01-24 22:32 S55pppd-dns -> ../init.d/pppd-dns
lrwxrwxrwx   1 root root   24 2009-02-11 06:08 S70screen-cleanup -> ../init.d/screen-cleanup
lrwxrwxrwx   1 root root   20 2008-01-24 22:32 S70x11-common -> ../init.d/x11-common
lrwxrwxrwx   1 root root   21 2008-01-24 22:32 S80bootmisc.sh -> ../init.d/bootmisc.sh
lrwxrwxrwx   1 root root   17 2008-01-24 22:32 S85urandom -> ../init.d/urandom
lrwxrwxrwx   1 root root   27 2008-01-24 22:32 S90console-screen.sh -> ../init.d/console-screen.sh

```

---

### Post by pytheas22 on 2009-03-25
Sorry that X broke, but after logging in manually by typing 'startx', do you still receive the error messages?  Or are they fixed?

---

### Post by cqhcp on 2009-03-25
> **pytheas22 said:**
> Sorry that X broke, but after logging in manually by typing 'startx', do you still receive the error messages?  Or are they fixed?
After logging in manually by typing 'startx', gnome started without error message, desktop displayed. In the 'Network Setting' and 'Users Settings' window, the 'Unlock' button is disabled, can't be click. In the terminal, when run 'sudo' command, display an 'Error' string also.
Every time boot system, 'Setting mode 1280 * 1024 failed .....' will occur. So, I rename '30gdm' to 'S30gdm', login window start ok, but with 'Error' message also, like before.

---

### Post by pytheas22 on 2009-03-25
hmmm...which version of Ubuntu are you using?  8.04?

Also, if you change 'S30gdm' to 'S41gdm' in the /etc/rc2.d, /etc/rc3.d, /etc/rc4.d and /etc/rc5.d directories, does it make a difference?

---

### Post by cqhcp on 2009-03-26
> **pytheas22 said:**
> hmmm...which version of Ubuntu are you using?  8.04?

Also, if you change 'S30gdm' to 'S41gdm' in the /etc/rc2.d, /etc/rc3.d, /etc/rc4.d and /etc/rc5.d directories, does it make a difference?

My Ubuntu version is 8.04.
I had change 'S30gdm' to 'S41gdm' in the /etc/rc2.d, /etc/rc3.d, /etc/rc4.d and /etc/rc5.d directories, then reboot. But it's also like before, no difference.

---

### Post by pytheas22 on 2009-03-27
Sorry for the slow response.  I was waiting until I was able to take a look at my own Ubuntu 8.04 machine to see what the startup services are like there.

Have you applied all Ubuntu updates to your computer?  The documents I'm reading suggest that this bug should have been fixed for Ubuntu 8.04 by Ubuntu updates.  You can update the machine by typing:
```

sudo apt-get update; sudo apt-get upgrade
```

On my Ubuntu 8.04 computer, this is what the startup services look like:

```
$ ls -l /etc/rc*.d/
/etc/rc0.d/:
total 4
lrwxrwxrwx 1 root root  13 2008-10-22 08:55 K01gdm -> ../init.d/gdm
lrwxrwxrwx 1 root root  17 2008-10-22 08:55 K01usplash -> ../init.d/usplash
lrwxrwxrwx 1 root root  17 2009-02-18 14:31 K09apache2 -> ../init.d/apache2
lrwxrwxrwx 1 root root  16 2008-10-22 08:55 K16dhcdbd -> ../init.d/dhcdbd
lrwxrwxrwx 1 root root  16 2008-10-22 08:55 K20apport -> ../init.d/apport
lrwxrwxrwx 1 root root  22 2008-10-22 08:55 K20avahi-daemon -> ../init.d/avahi-daemon
lrwxrwxrwx 1 root root  28 2008-12-10 13:42 K20dkms_autoinstaller -> ../init.d/dkms_autoinstaller
lrwxrwxrwx 1 root root  15 2009-02-11 14:40 K20exim4 -> ../init.d/exim4
lrwxrwxrwx 1 root root  16 2009-02-06 16:13 K20jabber -> ../init.d/jabber
lrwxrwxrwx 1 root root  21 2008-12-10 13:57 K20libvirt-bin -> ../init.d/libvirt-bin
lrwxrwxrwx 1 root root  18 2009-02-13 16:38 K20openfire -> ../init.d/openfire
lrwxrwxrwx 1 root root  17 2009-03-25 15:15 K20vboxdrv -> ../init.d/vboxdrv
lrwxrwxrwx 1 root root  24 2009-03-25 15:15 K20virtualbox-ose -> ../init.d/virtualbox-ose
lrwxrwxrwx 1 root root  17 2008-11-12 14:38 K20winbind -> ../init.d/winbind
lrwxrwxrwx 1 root root  15 2009-02-25 13:53 K21mysql -> ../init.d/mysql
lrwxrwxrwx 1 root root  19 2009-02-25 13:53 K22mysql-ndb -> ../init.d/mysql-ndb
lrwxrwxrwx 1 root root  23 2009-02-25 13:53 K23mysql-ndb-mgm -> ../init.d/mysql-ndb-mgm
lrwxrwxrwx 1 root root  20 2008-10-22 08:55 K25hwclock.sh -> ../init.d/hwclock.sh
lrwxrwxrwx 1 root root  13 2008-10-22 08:55 K39ufw -> ../init.d/ufw
lrwxrwxrwx 1 root root  20 2008-10-22 08:55 K50alsa-utils -> ../init.d/alsa-utils
lrwxrwxrwx 1 root root  26 2008-10-22 08:55 K59mountoverflowtmp -> ../init.d/mountoverflowtmp
lrwxrwxrwx 1 root root  21 2008-10-22 08:55 K99laptop-mode -> ../init.d/laptop-mode
-rw-r--r-- 1 root root 355 2008-04-19 01:05 README
lrwxrwxrwx 1 root root  41 2008-10-22 08:55 S01linux-restricted-modules-common -> ../init.d/linux-restricted-modules-common
lrwxrwxrwx 1 root root  22 2008-10-22 08:55 S15wpa-ifupdown -> ../init.d/wpa-ifupdown
lrwxrwxrwx 1 root root  18 2008-10-22 08:55 S20sendsigs -> ../init.d/sendsigs
lrwxrwxrwx 1 root root  17 2008-10-22 08:55 S30urandom -> ../init.d/urandom
lrwxrwxrwx 1 root root  22 2008-10-22 08:55 S31umountnfs.sh -> ../init.d/umountnfs.sh
lrwxrwxrwx 1 root root  18 2008-10-22 08:55 S40umountfs -> ../init.d/umountfs
lrwxrwxrwx 1 root root  20 2008-10-22 08:55 S60umountroot -> ../init.d/umountroot
lrwxrwxrwx 1 root root  16 2009-02-13 15:32 S89casper -> ../init.d/casper
lrwxrwxrwx 1 root root  14 2008-10-22 08:55 S90halt -> ../init.d/halt

/etc/rc1.d/:
total 4
lrwxrwxrwx 1 root root  13 2008-10-22 08:55 K01gdm -> ../init.d/gdm
lrwxrwxrwx 1 root root  17 2008-10-22 08:55 K01usplash -> ../init.d/usplash
lrwxrwxrwx 1 root root  17 2009-02-18 14:31 K09apache2 -> ../init.d/apache2
lrwxrwxrwx 1 root root  17 2008-10-22 08:55 K11anacron -> ../init.d/anacron
lrwxrwxrwx 1 root root  13 2008-10-22 08:55 K11atd -> ../init.d/atd
lrwxrwxrwx 1 root root  14 2008-10-22 08:55 K11cron -> ../init.d/cron
lrwxrwxrwx 1 root root  20 2008-10-22 08:55 K15pulseaudio -> ../init.d/pulseaudio
lrwxrwxrwx 1 root root  16 2008-10-22 08:55 K16dhcdbd -> ../init.d/dhcdbd
lrwxrwxrwx 1 root root  13 2008-10-22 08:55 K16hal -> ../init.d/hal
lrwxrwxrwx 1 root root  22 2008-10-22 08:55 K20acpi-support -> ../init.d/acpi-support
lrwxrwxrwx 1 root root  14 2008-10-22 08:55 K20apmd -> ../init.d/apmd
lrwxrwxrwx 1 root root  16 2008-10-22 08:55 K20apport -> ../init.d/apport
lrwxrwxrwx 1 root root  22 2008-10-22 08:55 K20avahi-daemon -> ../init.d/avahi-daemon
lrwxrwxrwx 1 root root  28 2008-12-10 13:42 K20dkms_autoinstaller -> ../init.d/dkms_autoinstaller
lrwxrwxrwx 1 root root  15 2009-02-11 14:40 K20exim4 -> ../init.d/exim4
lrwxrwxrwx 1 root root  22 2008-10-22 08:55 K20hotkey-setup -> ../init.d/hotkey-setup
lrwxrwxrwx 1 root root  16 2009-02-06 16:13 K20jabber -> ../init.d/jabber
lrwxrwxrwx 1 root root  13 2008-12-10 13:57 K20kvm -> ../init.d/kvm
lrwxrwxrwx 1 root root  21 2008-12-10 13:57 K20libvirt-bin -> ../init.d/libvirt-bin
lrwxrwxrwx 1 root root  23 2008-10-22 08:55 K20nvidia-kernel -> ../init.d/nvidia-kernel
lrwxrwxrwx 1 root root  18 2009-02-13 16:38 K20openfire -> ../init.d/openfire
lrwxrwxrwx 1 root root  19 2008-10-22 08:55 K20powernowd -> ../init.d/powernowd
lrwxrwxrwx 1 root root  15 2008-10-22 08:55 K20rsync -> ../init.d/rsync
lrwxrwxrwx 1 root root  17 2009-03-25 15:15 K20vboxdrv -> ../init.d/vboxdrv
lrwxrwxrwx 1 root root  24 2009-03-25 15:15 K20virtualbox-ose -> ../init.d/virtualbox-ose
lrwxrwxrwx 1 root root  17 2008-11-12 14:38 K20winbind -> ../init.d/winbind
lrwxrwxrwx 1 root root  15 2008-10-22 08:55 K21acpid -> ../init.d/acpid
lrwxrwxrwx 1 root root  15 2009-02-25 13:53 K21mysql -> ../init.d/mysql
lrwxrwxrwx 1 root root  19 2009-02-25 13:53 K22mysql-ndb -> ../init.d/mysql-ndb
lrwxrwxrwx 1 root root  23 2009-02-25 13:53 K23mysql-ndb-mgm -> ../init.d/mysql-ndb-mgm
lrwxrwxrwx 1 root root  13 2008-10-22 08:55 K39ufw -> ../init.d/ufw
lrwxrwxrwx 1 root root  19 2008-10-22 08:55 K74bluetooth -> ../init.d/bluetooth
lrwxrwxrwx 1 root root  16 2008-10-22 08:55 K80cupsys -> ../init.d/cupsys
lrwxrwxrwx 1 root root  13 2009-02-13 17:02 K84ssh -> ../init.d/ssh
lrwxrwxrwx 1 root root  14 2008-10-22 08:55 K88dbus -> ../init.d/dbus
lrwxrwxrwx 1 root root  15 2008-10-22 08:55 K89klogd -> ../init.d/klogd
lrwxrwxrwx 1 root root  18 2008-10-22 08:55 K90sysklogd -> ../init.d/sysklogd
lrwxrwxrwx 1 root root  21 2008-10-22 08:55 K99laptop-mode -> ../init.d/laptop-mode
lrwxrwxrwx 1 root root  19 2008-10-22 08:55 K99policykit -> ../init.d/policykit
-rw-r--r-- 1 root root 371 2008-04-19 01:05 README
lrwxrwxrwx 1 root root  19 2008-10-22 08:55 S30killprocs -> ../init.d/killprocs
lrwxrwxrwx 1 root root  16 2008-10-22 08:55 S90single -> ../init.d/single

/etc/rc2.d/:
total 4
-rw-r--r-- 1 root root 556 2008-04-19 01:05 README
lrwxrwxrwx 1 root root  19 2008-10-22 08:55 S01policykit -> ../init.d/policykit
lrwxrwxrwx 1 root root  17 2008-10-22 08:55 S05vbesave -> ../init.d/vbesave
lrwxrwxrwx 1 root root  15 2008-10-22 08:55 S10acpid -> ../init.d/acpid
lrwxrwxrwx 1 root root  25 2008-10-22 08:55 S10powernowd.early -> ../init.d/powernowd.early
lrwxrwxrwx 1 root root  18 2008-10-22 08:55 S10sysklogd -> ../init.d/sysklogd
lrwxrwxrwx 1 root root  34 2008-10-22 08:55 S10xserver-xorg-input-wacom -> ../init.d/xserver-xorg-input-wacom
lrwxrwxrwx 1 root root  15 2008-10-22 08:55 S11klogd -> ../init.d/klogd
lrwxrwxrwx 1 root root  14 2008-10-22 08:55 S12dbus -> ../init.d/dbus
lrwxrwxrwx 1 root root  13 2009-02-13 17:02 S16ssh -> ../init.d/ssh
lrwxrwxrwx 1 root root  23 2009-02-25 13:53 S17mysql-ndb-mgm -> ../init.d/mysql-ndb-mgm
lrwxrwxrwx 1 root root  22 2008-10-22 08:55 S18avahi-daemon -> ../init.d/avahi-daemon
lrwxrwxrwx 1 root root  19 2009-02-25 13:53 S18mysql-ndb -> ../init.d/mysql-ndb
lrwxrwxrwx 1 root root  15 2009-02-25 13:53 S19mysql -> ../init.d/mysql
lrwxrwxrwx 1 root root  14 2008-10-22 08:55 S20apmd -> ../init.d/apmd
lrwxrwxrwx 1 root root  16 2008-10-22 08:55 S20apport -> ../init.d/apport
lrwxrwxrwx 1 root root  16 2008-10-22 08:55 S20cupsys -> ../init.d/cupsys
lrwxrwxrwx 1 root root  28 2008-12-10 13:42 S20dkms_autoinstaller -> ../init.d/dkms_autoinstaller
lrwxrwxrwx 1 root root  15 2009-02-11 14:40 S20exim4 -> ../init.d/exim4
lrwxrwxrwx 1 root root  22 2008-10-22 08:55 S20hotkey-setup -> ../init.d/hotkey-setup
lrwxrwxrwx 1 root root  16 2009-02-06 16:13 S20jabber -> ../init.d/jabber
lrwxrwxrwx 1 root root  13 2008-12-10 13:57 S20kvm -> ../init.d/kvm
lrwxrwxrwx 1 root root  21 2008-12-10 13:57 S20libvirt-bin -> ../init.d/libvirt-bin
lrwxrwxrwx 1 root root  23 2008-10-22 08:55 S20nvidia-kernel -> ../init.d/nvidia-kernel
lrwxrwxrwx 1 root root  18 2009-02-13 16:38 S20openfire -> ../init.d/openfire
lrwxrwxrwx 1 root root  19 2008-10-22 08:55 S20powernowd -> ../init.d/powernowd
lrwxrwxrwx 1 root root  15 2008-10-22 08:55 S20rsync -> ../init.d/rsync
lrwxrwxrwx 1 root root  17 2009-03-25 15:15 S20vboxdrv -> ../init.d/vboxdrv
lrwxrwxrwx 1 root root  24 2009-03-25 15:15 S20virtualbox-ose -> ../init.d/virtualbox-ose
lrwxrwxrwx 1 root root  17 2008-11-12 14:38 S20winbind -> ../init.d/winbind
lrwxrwxrwx 1 root root  16 2008-10-22 08:55 S24dhcdbd -> ../init.d/dhcdbd
lrwxrwxrwx 1 root root  13 2008-10-22 08:55 S24hal -> ../init.d/hal
lrwxrwxrwx 1 root root  19 2008-10-22 08:55 S25bluetooth -> ../init.d/bluetooth
lrwxrwxrwx 1 root root  20 2008-10-22 08:55 S25pulseaudio -> ../init.d/pulseaudio
lrwxrwxrwx 1 root root  18 2009-02-13 15:33 S29ubiquity -> ../init.d/ubiquity
lrwxrwxrwx 1 root root  13 2008-10-22 08:55 S30gdm -> ../init.d/gdm
lrwxrwxrwx 1 root root  17 2008-10-22 08:55 S89anacron -> ../init.d/anacron
lrwxrwxrwx 1 root root  13 2008-10-22 08:55 S89atd -> ../init.d/atd
lrwxrwxrwx 1 root root  14 2008-10-22 08:55 S89cron -> ../init.d/cron
lrwxrwxrwx 1 root root  24 2008-11-12 14:38 S90binfmt-support -> ../init.d/binfmt-support
lrwxrwxrwx 1 root root  17 2009-02-18 14:31 S91apache2 -> ../init.d/apache2
lrwxrwxrwx 1 root root  17 2008-10-22 08:55 S98usplash -> ../init.d/usplash
lrwxrwxrwx 1 root root  22 2008-10-22 08:55 S99acpi-support -> ../init.d/acpi-support
lrwxrwxrwx 1 root root  21 2008-10-22 08:55 S99laptop-mode -> ../init.d/laptop-mode
lrwxrwxrwx 1 root root  18 2008-10-22 08:55 S99rc.local -> ../init.d/rc.local
lrwxrwxrwx 1 root root  19 2008-10-22 08:55 S99rmnologin -> ../init.d/rmnologin
lrwxrwxrwx 1 root root  24 2008-10-22 08:55 S99stop-readahead -> ../init.d/stop-readahead

/etc/rc3.d/:
total 4
-rw-r--r-- 1 root root 556 2008-04-19 01:05 README
lrwxrwxrwx 1 root root  19 2008-10-22 08:55 S01policykit -> ../init.d/policykit
lrwxrwxrwx 1 root root  17 2008-10-22 08:55 S05vbesave -> ../init.d/vbesave
lrwxrwxrwx 1 root root  15 2008-10-22 08:55 S10acpid -> ../init.d/acpid
lrwxrwxrwx 1 root root  18 2008-10-22 08:55 S10sysklogd -> ../init.d/sysklogd
lrwxrwxrwx 1 root root  34 2008-10-22 08:55 S10xserver-xorg-input-wacom -> ../init.d/xserver-xorg-input-wacom
lrwxrwxrwx 1 root root  15 2008-10-22 08:55 S11klogd -> ../init.d/klogd
lrwxrwxrwx 1 root root  14 2008-10-22 08:55 S12dbus -> ../init.d/dbus
lrwxrwxrwx 1 root root  13 2009-02-13 17:02 S16ssh -> ../init.d/ssh
lrwxrwxrwx 1 root root  23 2009-02-25 13:53 S17mysql-ndb-mgm -> ../init.d/mysql-ndb-mgm
lrwxrwxrwx 1 root root  22 2008-10-22 08:55 S18avahi-daemon -> ../init.d/avahi-daemon
lrwxrwxrwx 1 root root  19 2009-02-25 13:53 S18mysql-ndb -> ../init.d/mysql-ndb
lrwxrwxrwx 1 root root  15 2009-02-25 13:53 S19mysql -> ../init.d/mysql
lrwxrwxrwx 1 root root  14 2008-10-22 08:55 S20apmd -> ../init.d/apmd
lrwxrwxrwx 1 root root  16 2008-10-22 08:55 S20apport -> ../init.d/apport
lrwxrwxrwx 1 root root  16 2008-10-22 08:55 S20cupsys -> ../init.d/cupsys
lrwxrwxrwx 1 root root  28 2008-12-10 13:42 S20dkms_autoinstaller -> ../init.d/dkms_autoinstaller
lrwxrwxrwx 1 root root  15 2009-02-11 14:40 S20exim4 -> ../init.d/exim4
lrwxrwxrwx 1 root root  22 2008-10-22 08:55 S20hotkey-setup -> ../init.d/hotkey-setup
lrwxrwxrwx 1 root root  16 2009-02-06 16:13 S20jabber -> ../init.d/jabber
lrwxrwxrwx 1 root root  13 2008-12-10 13:57 S20kvm -> ../init.d/kvm
lrwxrwxrwx 1 root root  21 2008-12-10 13:57 S20libvirt-bin -> ../init.d/libvirt-bin
lrwxrwxrwx 1 root root  23 2008-10-22 08:55 S20nvidia-kernel -> ../init.d/nvidia-kernel
lrwxrwxrwx 1 root root  18 2009-02-13 16:38 S20openfire -> ../init.d/openfire
lrwxrwxrwx 1 root root  19 2008-10-22 08:55 S20powernowd -> ../init.d/powernowd
lrwxrwxrwx 1 root root  15 2008-10-22 08:55 S20rsync -> ../init.d/rsync
lrwxrwxrwx 1 root root  17 2009-03-25 15:15 S20vboxdrv -> ../init.d/vboxdrv
lrwxrwxrwx 1 root root  24 2009-03-25 15:15 S20virtualbox-ose -> ../init.d/virtualbox-ose
lrwxrwxrwx 1 root root  17 2008-11-12 14:38 S20winbind -> ../init.d/winbind
lrwxrwxrwx 1 root root  16 2008-10-22 08:55 S24dhcdbd -> ../init.d/dhcdbd
lrwxrwxrwx 1 root root  13 2008-10-22 08:55 S24hal -> ../init.d/hal
lrwxrwxrwx 1 root root  19 2008-10-22 08:55 S25bluetooth -> ../init.d/bluetooth
lrwxrwxrwx 1 root root  20 2008-10-22 08:55 S25pulseaudio -> ../init.d/pulseaudio
lrwxrwxrwx 1 root root  18 2009-02-13 15:33 S29ubiquity -> ../init.d/ubiquity
lrwxrwxrwx 1 root root  13 2008-10-22 08:55 S30gdm -> ../init.d/gdm
lrwxrwxrwx 1 root root  17 2008-10-22 08:55 S89anacron -> ../init.d/anacron
lrwxrwxrwx 1 root root  13 2008-10-22 08:55 S89atd -> ../init.d/atd
lrwxrwxrwx 1 root root  14 2008-10-22 08:55 S89cron -> ../init.d/cron
lrwxrwxrwx 1 root root  24 2008-11-12 14:38 S90binfmt-support -> ../init.d/binfmt-support
lrwxrwxrwx 1 root root  17 2009-02-18 14:31 S91apache2 -> ../init.d/apache2
lrwxrwxrwx 1 root root  17 2008-10-22 08:55 S98usplash -> ../init.d/usplash
lrwxrwxrwx 1 root root  22 2008-10-22 08:55 S99acpi-support -> ../init.d/acpi-support
lrwxrwxrwx 1 root root  21 2008-10-22 08:55 S99laptop-mode -> ../init.d/laptop-mode
lrwxrwxrwx 1 root root  18 2008-10-22 08:55 S99rc.local -> ../init.d/rc.local
lrwxrwxrwx 1 root root  19 2008-10-22 08:55 S99rmnologin -> ../init.d/rmnologin

/etc/rc4.d/:
total 4
-rw-r--r-- 1 root root 556 2008-04-19 01:05 README
lrwxrwxrwx 1 root root  19 2008-10-22 08:55 S01policykit -> ../init.d/policykit
lrwxrwxrwx 1 root root  17 2008-10-22 08:55 S05vbesave -> ../init.d/vbesave
lrwxrwxrwx 1 root root  15 2008-10-22 08:55 S10acpid -> ../init.d/acpid
lrwxrwxrwx 1 root root  18 2008-10-22 08:55 S10sysklogd -> ../init.d/sysklogd
lrwxrwxrwx 1 root root  34 2008-10-22 08:55 S10xserver-xorg-input-wacom -> ../init.d/xserver-xorg-input-wacom
lrwxrwxrwx 1 root root  15 2008-10-22 08:55 S11klogd -> ../init.d/klogd
lrwxrwxrwx 1 root root  14 2008-10-22 08:55 S12dbus -> ../init.d/dbus
lrwxrwxrwx 1 root root  13 2009-02-13 17:02 S16ssh -> ../init.d/ssh
lrwxrwxrwx 1 root root  23 2009-02-25 13:53 S17mysql-ndb-mgm -> ../init.d/mysql-ndb-mgm
lrwxrwxrwx 1 root root  22 2008-10-22 08:55 S18avahi-daemon -> ../init.d/avahi-daemon
lrwxrwxrwx 1 root root  19 2009-02-25 13:53 S18mysql-ndb -> ../init.d/mysql-ndb
lrwxrwxrwx 1 root root  15 2009-02-25 13:53 S19mysql -> ../init.d/mysql
lrwxrwxrwx 1 root root  14 2008-10-22 08:55 S20apmd -> ../init.d/apmd
lrwxrwxrwx 1 root root  16 2008-10-22 08:55 S20apport -> ../init.d/apport
lrwxrwxrwx 1 root root  16 2008-10-22 08:55 S20cupsys -> ../init.d/cupsys
lrwxrwxrwx 1 root root  28 2008-12-10 13:42 S20dkms_autoinstaller -> ../init.d/dkms_autoinstaller
lrwxrwxrwx 1 root root  15 2009-02-11 14:40 S20exim4 -> ../init.d/exim4
lrwxrwxrwx 1 root root  22 2008-10-22 08:55 S20hotkey-setup -> ../init.d/hotkey-setup
lrwxrwxrwx 1 root root  16 2009-02-06 16:13 S20jabber -> ../init.d/jabber
lrwxrwxrwx 1 root root  13 2008-12-10 13:57 S20kvm -> ../init.d/kvm
lrwxrwxrwx 1 root root  21 2008-12-10 13:57 S20libvirt-bin -> ../init.d/libvirt-bin
lrwxrwxrwx 1 root root  23 2008-10-22 08:55 S20nvidia-kernel -> ../init.d/nvidia-kernel
lrwxrwxrwx 1 root root  18 2009-02-13 16:38 S20openfire -> ../init.d/openfire
lrwxrwxrwx 1 root root  19 2008-10-22 08:55 S20powernowd -> ../init.d/powernowd
lrwxrwxrwx 1 root root  15 2008-10-22 08:55 S20rsync -> ../init.d/rsync
lrwxrwxrwx 1 root root  17 2009-03-25 15:15 S20vboxdrv -> ../init.d/vboxdrv
lrwxrwxrwx 1 root root  24 2009-03-25 15:15 S20virtualbox-ose -> ../init.d/virtualbox-ose
lrwxrwxrwx 1 root root  17 2008-11-12 14:38 S20winbind -> ../init.d/winbind
lrwxrwxrwx 1 root root  16 2008-10-22 08:55 S24dhcdbd -> ../init.d/dhcdbd
lrwxrwxrwx 1 root root  13 2008-10-22 08:55 S24hal -> ../init.d/hal
lrwxrwxrwx 1 root root  19 2008-10-22 08:55 S25bluetooth -> ../init.d/bluetooth
lrwxrwxrwx 1 root root  20 2008-10-22 08:55 S25pulseaudio -> ../init.d/pulseaudio
lrwxrwxrwx 1 root root  18 2009-02-13 15:33 S29ubiquity -> ../init.d/ubiquity
lrwxrwxrwx 1 root root  13 2008-10-22 08:55 S30gdm -> ../init.d/gdm
lrwxrwxrwx 1 root root  17 2008-10-22 08:55 S89anacron -> ../init.d/anacron
lrwxrwxrwx 1 root root  13 2008-10-22 08:55 S89atd -> ../init.d/atd
lrwxrwxrwx 1 root root  14 2008-10-22 08:55 S89cron -> ../init.d/cron
lrwxrwxrwx 1 root root  24 2008-11-12 14:38 S90binfmt-support -> ../init.d/binfmt-support
lrwxrwxrwx 1 root root  17 2009-02-18 14:31 S91apache2 -> ../init.d/apache2
lrwxrwxrwx 1 root root  17 2008-10-22 08:55 S98usplash -> ../init.d/usplash
lrwxrwxrwx 1 root root  22 2008-10-22 08:55 S99acpi-support -> ../init.d/acpi-support
lrwxrwxrwx 1 root root  21 2008-10-22 08:55 S99laptop-mode -> ../init.d/laptop-mode
lrwxrwxrwx 1 root root  18 2008-10-22 08:55 S99rc.local -> ../init.d/rc.local
lrwxrwxrwx 1 root root  19 2008-10-22 08:55 S99rmnologin -> ../init.d/rmnologin

/etc/rc5.d/:
total 4
-rw-r--r-- 1 root root 556 2008-04-19 01:05 README
lrwxrwxrwx 1 root root  19 2008-10-22 08:55 S01policykit -> ../init.d/policykit
lrwxrwxrwx 1 root root  17 2008-10-22 08:55 S05vbesave -> ../init.d/vbesave
lrwxrwxrwx 1 root root  15 2008-10-22 08:55 S10acpid -> ../init.d/acpid
lrwxrwxrwx 1 root root  18 2008-10-22 08:55 S10sysklogd -> ../init.d/sysklogd
lrwxrwxrwx 1 root root  34 2008-10-22 08:55 S10xserver-xorg-input-wacom -> ../init.d/xserver-xorg-input-wacom
lrwxrwxrwx 1 root root  15 2008-10-22 08:55 S11klogd -> ../init.d/klogd
lrwxrwxrwx 1 root root  14 2008-10-22 08:55 S12dbus -> ../init.d/dbus
lrwxrwxrwx 1 root root  13 2009-02-13 17:02 S16ssh -> ../init.d/ssh
lrwxrwxrwx 1 root root  23 2009-02-25 13:53 S17mysql-ndb-mgm -> ../init.d/mysql-ndb-mgm
lrwxrwxrwx 1 root root  22 2008-10-22 08:55 S18avahi-daemon -> ../init.d/avahi-daemon
lrwxrwxrwx 1 root root  19 2009-02-25 13:53 S18mysql-ndb -> ../init.d/mysql-ndb
lrwxrwxrwx 1 root root  15 2009-02-25 13:53 S19mysql -> ../init.d/mysql
lrwxrwxrwx 1 root root  14 2008-10-22 08:55 S20apmd -> ../init.d/apmd
lrwxrwxrwx 1 root root  16 2008-10-22 08:55 S20apport -> ../init.d/apport
lrwxrwxrwx 1 root root  16 2008-10-22 08:55 S20cupsys -> ../init.d/cupsys
lrwxrwxrwx 1 root root  28 2008-12-10 13:42 S20dkms_autoinstaller -> ../init.d/dkms_autoinstaller
lrwxrwxrwx 1 root root  15 2009-02-11 14:40 S20exim4 -> ../init.d/exim4
lrwxrwxrwx 1 root root  22 2008-10-22 08:55 S20hotkey-setup -> ../init.d/hotkey-setup
lrwxrwxrwx 1 root root  16 2009-02-06 16:13 S20jabber -> ../init.d/jabber
lrwxrwxrwx 1 root root  13 2008-12-10 13:57 S20kvm -> ../init.d/kvm
lrwxrwxrwx 1 root root  21 2008-12-10 13:57 S20libvirt-bin -> ../init.d/libvirt-bin
lrwxrwxrwx 1 root root  23 2008-10-22 08:55 S20nvidia-kernel -> ../init.d/nvidia-kernel
lrwxrwxrwx 1 root root  18 2009-02-13 16:38 S20openfire -> ../init.d/openfire
lrwxrwxrwx 1 root root  19 2008-10-22 08:55 S20powernowd -> ../init.d/powernowd
lrwxrwxrwx 1 root root  15 2008-10-22 08:55 S20rsync -> ../init.d/rsync
lrwxrwxrwx 1 root root  17 2009-03-25 15:15 S20vboxdrv -> ../init.d/vboxdrv
lrwxrwxrwx 1 root root  24 2009-03-25 15:15 S20virtualbox-ose -> ../init.d/virtualbox-ose
lrwxrwxrwx 1 root root  17 2008-11-12 14:38 S20winbind -> ../init.d/winbind
lrwxrwxrwx 1 root root  16 2008-10-22 08:55 S24dhcdbd -> ../init.d/dhcdbd
lrwxrwxrwx 1 root root  13 2008-10-22 08:55 S24hal -> ../init.d/hal
lrwxrwxrwx 1 root root  19 2008-10-22 08:55 S25bluetooth -> ../init.d/bluetooth
lrwxrwxrwx 1 root root  20 2008-10-22 08:55 S25pulseaudio -> ../init.d/pulseaudio
lrwxrwxrwx 1 root root  18 2009-02-13 15:33 S29ubiquity -> ../init.d/ubiquity
lrwxrwxrwx 1 root root  13 2008-10-22 08:55 S30gdm -> ../init.d/gdm
lrwxrwxrwx 1 root root  17 2008-10-22 08:55 S89anacron -> ../init.d/anacron
lrwxrwxrwx 1 root root  13 2008-10-22 08:55 S89atd -> ../init.d/atd
lrwxrwxrwx 1 root root  14 2008-10-22 08:55 S89cron -> ../init.d/cron
lrwxrwxrwx 1 root root  24 2008-11-12 14:38 S90binfmt-support -> ../init.d/binfmt-support
lrwxrwxrwx 1 root root  17 2009-02-18 14:31 S91apache2 -> ../init.d/apache2
lrwxrwxrwx 1 root root  17 2008-10-22 08:55 S98usplash -> ../init.d/usplash
lrwxrwxrwx 1 root root  22 2008-10-22 08:55 S99acpi-support -> ../init.d/acpi-support
lrwxrwxrwx 1 root root  21 2008-10-22 08:55 S99laptop-mode -> ../init.d/laptop-mode
lrwxrwxrwx 1 root root  18 2008-10-22 08:55 S99rc.local -> ../init.d/rc.local
lrwxrwxrwx 1 root root  19 2008-10-22 08:55 S99rmnologin -> ../init.d/rmnologin

/etc/rc6.d/:
total 4
lrwxrwxrwx 1 root root  13 2008-10-22 08:55 K01gdm -> ../init.d/gdm
lrwxrwxrwx 1 root root  17 2008-10-22 08:55 K01usplash -> ../init.d/usplash
lrwxrwxrwx 1 root root  17 2009-02-18 14:31 K09apache2 -> ../init.d/apache2
lrwxrwxrwx 1 root root  16 2008-10-22 08:55 K16dhcdbd -> ../init.d/dhcdbd
lrwxrwxrwx 1 root root  16 2008-10-22 08:55 K20apport -> ../init.d/apport
lrwxrwxrwx 1 root root  22 2008-10-22 08:55 K20avahi-daemon -> ../init.d/avahi-daemon
lrwxrwxrwx 1 root root  28 2008-12-10 13:42 K20dkms_autoinstaller -> ../init.d/dkms_autoinstaller
lrwxrwxrwx 1 root root  15 2009-02-11 14:40 K20exim4 -> ../init.d/exim4
lrwxrwxrwx 1 root root  16 2009-02-06 16:13 K20jabber -> ../init.d/jabber
lrwxrwxrwx 1 root root  21 2008-12-10 13:57 K20libvirt-bin -> ../init.d/libvirt-bin
lrwxrwxrwx 1 root root  18 2009-02-13 16:38 K20openfire -> ../init.d/openfire
lrwxrwxrwx 1 root root  17 2009-03-25 15:15 K20vboxdrv -> ../init.d/vboxdrv
lrwxrwxrwx 1 root root  24 2009-03-25 15:15 K20virtualbox-ose -> ../init.d/virtualbox-ose
lrwxrwxrwx 1 root root  17 2008-11-12 14:38 K20winbind -> ../init.d/winbind
lrwxrwxrwx 1 root root  15 2009-02-25 13:53 K21mysql -> ../init.d/mysql
lrwxrwxrwx 1 root root  19 2009-02-25 13:53 K22mysql-ndb -> ../init.d/mysql-ndb
lrwxrwxrwx 1 root root  23 2009-02-25 13:53 K23mysql-ndb-mgm -> ../init.d/mysql-ndb-mgm
lrwxrwxrwx 1 root root  20 2008-10-22 08:55 K25hwclock.sh -> ../init.d/hwclock.sh
lrwxrwxrwx 1 root root  13 2008-10-22 08:55 K39ufw -> ../init.d/ufw
lrwxrwxrwx 1 root root  20 2008-10-22 08:55 K50alsa-utils -> ../init.d/alsa-utils
lrwxrwxrwx 1 root root  26 2008-10-22 08:55 K59mountoverflowtmp -> ../init.d/mountoverflowtmp
lrwxrwxrwx 1 root root  21 2008-10-22 08:55 K99laptop-mode -> ../init.d/laptop-mode
-rw-r--r-- 1 root root 353 2008-04-19 01:05 README
lrwxrwxrwx 1 root root  41 2008-10-22 08:55 S01linux-restricted-modules-common -> ../init.d/linux-restricted-modules-common
lrwxrwxrwx 1 root root  22 2008-10-22 08:55 S15wpa-ifupdown -> ../init.d/wpa-ifupdown
lrwxrwxrwx 1 root root  18 2008-10-22 08:55 S20sendsigs -> ../init.d/sendsigs
lrwxrwxrwx 1 root root  17 2008-10-22 08:55 S30urandom -> ../init.d/urandom
lrwxrwxrwx 1 root root  22 2008-10-22 08:55 S31umountnfs.sh -> ../init.d/umountnfs.sh
lrwxrwxrwx 1 root root  18 2008-10-22 08:55 S40umountfs -> ../init.d/umountfs
lrwxrwxrwx 1 root root  20 2008-10-22 08:55 S60umountroot -> ../init.d/umountroot
lrwxrwxrwx 1 root root  16 2009-02-13 15:32 S89casper -> ../init.d/casper
lrwxrwxrwx 1 root root  16 2008-10-22 08:55 S90reboot -> ../init.d/reboot

/etc/rcS.d/:
total 4
-rw-r--r-- 1 root root 785 2008-04-19 01:05 README
lrwxrwxrwx 1 root root  24 2008-10-22 08:55 S01mountkernfs.sh -> ../init.d/mountkernfs.sh
lrwxrwxrwx 1 root root  19 2008-10-22 08:55 S01readahead -> ../init.d/readahead
lrwxrwxrwx 1 root root  21 2008-10-22 08:55 S02hostname.sh -> ../init.d/hostname.sh
lrwxrwxrwx 1 root root  24 2008-10-22 08:55 S06keyboard-setup -> ../init.d/keyboard-setup
lrwxrwxrwx 1 root root  41 2008-10-22 08:55 S07linux-restricted-modules-common -> ../init.d/linux-restricted-modules-common
lrwxrwxrwx 1 root root  25 2008-10-22 08:55 S08hwclockfirst.sh -> ../init.d/hwclockfirst.sh
lrwxrwxrwx 1 root root  18 2008-10-22 08:55 S08loopback -> ../init.d/loopback
lrwxrwxrwx 1 root root  14 2008-10-22 08:55 S10udev -> ../init.d/udev
lrwxrwxrwx 1 root root  20 2008-10-22 08:55 S11hwclock.sh -> ../init.d/hwclock.sh
lrwxrwxrwx 1 root root  26 2008-10-22 08:55 S11mountdevsubfs.sh -> ../init.d/mountdevsubfs.sh
lrwxrwxrwx 1 root root  21 2008-10-22 08:55 S13pcmciautils -> ../init.d/pcmciautils
lrwxrwxrwx 1 root root  27 2008-10-22 08:55 S15module-init-tools -> ../init.d/module-init-tools
lrwxrwxrwx 1 root root  16 2008-10-22 08:55 S17procps -> ../init.d/procps
lrwxrwxrwx 1 root root  22 2008-10-22 05:04 S18lupin-sysctl -> ../init.d/lupin-sysctl
lrwxrwxrwx 1 root root  22 2008-10-22 08:55 S20checkroot.sh -> ../init.d/checkroot.sh
lrwxrwxrwx 1 root root  17 2008-10-22 08:55 S22mtab.sh -> ../init.d/mtab.sh
lrwxrwxrwx 1 root root  16 2008-10-22 08:55 S25brltty -> ../init.d/brltty
lrwxrwxrwx 1 root root  20 2008-10-22 08:55 S30checkfs.sh -> ../init.d/checkfs.sh
lrwxrwxrwx 1 root root  21 2008-10-22 08:55 S35mountall.sh -> ../init.d/mountall.sh
lrwxrwxrwx 1 root root  31 2008-10-22 08:55 S36mountall-bootclean.sh -> ../init.d/mountall-bootclean.sh
lrwxrwxrwx 1 root root  18 2008-10-22 08:55 S37apparmor -> ../init.d/apparmor
lrwxrwxrwx 1 root root  26 2008-10-22 08:55 S37mountoverflowtmp -> ../init.d/mountoverflowtmp
lrwxrwxrwx 1 root root  21 2008-10-22 08:55 S37udev-finish -> ../init.d/udev-finish
lrwxrwxrwx 1 root root  27 2008-10-22 08:55 S39readahead-desktop -> ../init.d/readahead-desktop
lrwxrwxrwx 1 root root  13 2008-10-22 08:55 S39ufw -> ../init.d/ufw
lrwxrwxrwx 1 root root  20 2008-10-22 08:55 S40networking -> ../init.d/networking
lrwxrwxrwx 1 root root  20 2008-10-22 08:55 S45waitnfs.sh -> ../init.d/waitnfs.sh
lrwxrwxrwx 1 root root  31 2008-10-22 08:55 S46mountnfs-bootclean.sh -> ../init.d/mountnfs-bootclean.sh
lrwxrwxrwx 1 root root  23 2008-10-22 08:55 S49console-setup -> ../init.d/console-setup
lrwxrwxrwx 1 root root  19 2008-10-22 08:55 S55dns-clean -> ../init.d/dns-clean
lrwxrwxrwx 1 root root  18 2008-10-22 08:55 S55pppd-dns -> ../init.d/pppd-dns
lrwxrwxrwx 1 root root  24 2008-10-22 08:55 S70screen-cleanup -> ../init.d/screen-cleanup
lrwxrwxrwx 1 root root  20 2008-10-22 08:55 S70x11-common -> ../init.d/x11-common
lrwxrwxrwx 1 root root  21 2008-10-22 08:55 S80bootmisc.sh -> ../init.d/bootmisc.sh
lrwxrwxrwx 1 root root  17 2008-10-22 08:55 S85urandom -> ../init.d/urandom
lrwxrwxrwx 1 root root  27 2008-10-22 08:55 S90console-screen.sh -> ../init.d/console-screen.sh
```

There are some differences between my startup list and yours (some of the differences are caused by additional applications that I have installed, but some others have different startup priorities even though they're the same service).  You could try seeing if changing your list to look like mine would make a difference.  But you may also break your system this way, so be prepared to reinstall if you take this approach.

---

