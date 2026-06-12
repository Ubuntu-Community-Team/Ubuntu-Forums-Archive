---
title: "Freeing up RAM"
date: 2005-12-04
forum: Desktop Environments
---

### Post by SuperMike on 2005-12-04
I'm not in good financial shape this Christmas. I'm going to have to wait on the extra RAM. What is safe to unload from Ubuntu on my PC without having that much of a detrimental effect? I do run PostgreSQL, PHP, and Apache here, but I only fire those services up when I need them.

For instance, I don't need all these getty's, but I am not certain how to set them not to load on bootup. I really only need perhaps 2 gettys.

Are there also other services I can unload and load only every once in awhile? For instance, if I could have the Ubuntu service that checks for new updates only activate on a schedule once every day, perhaps that would free up RAM?

Note also that I use absolutely no KDE-based apps that I'm aware of.  That is, unless Inkscape is KDE-based. I only use Inkscape every once in a great while.


Here's my pstree dump:

[1minit,1[0m         
  &#9500;&#9472;acpid,15951 -c /etc/acpi/events -s /var/run/acpid.socket
  &#9500;&#9472;apache2,15974 -k start -DSSL
  &#9474;   &#9500;&#9472;apache2,15982 -k start -DSSL
  &#9474;   &#9500;&#9472;apache2,15983 -k start -DSSL
  &#9474;   &#9500;&#9472;apache2,15984 -k start -DSSL
  &#9474;   &#9500;&#9472;apache2,15985 -k start -DSSL
  &#9474;   &#9492;&#9472;apache2,15986 -k start -DSSL
  &#9500;&#9472;atd,7242
  &#9500;&#9472;bonobo-activati,10904 --ac-activate --ior-output-fd=18
  &#9500;&#9472;clock-applet,10988 --oaf-activate-iid=OAFIID:GNOME_ClockApplet_Factory --oaf-ior-fd=38
  &#9500;&#9472;cron,7255
  &#9500;&#9472;cupsd,16064 -F
  &#9500;&#9472;dbus-daemon,6267 --system
  &#9500;&#9472;dbus-daemon,10892 --fork --print-pid 8 --print-address 6 --session
  &#9500;&#9472;dbus-launch,10893 --exit-with-session x-session-manager
  &#9500;&#9472;dd,6252 bs 1 if /proc/kmsg of /var/run/klogd/kmsg
  &#9500;&#9472;esd,10900 -nobeeps
  &#9500;&#9472;(events/0,3)
  &#9500;&#9472;firefox-bin,27585 -a firefox
  &#9500;&#9472;freshclam,6900 -d --quiet
  &#9500;&#9472;gam_server,10914
  &#9500;&#9472;gconfd-2,10895 5
  &#9500;&#9472;gdm,6681
  &#9474;   &#9492;&#9472;gdm,6686
  &#9474;       &#9500;&#9472;Xorg,6770 :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
  &#9474;       &#9492;&#9472;x-session-manag,10839
  &#9474;           &#9492;&#9472;ssh-agent,10889 /usr/bin/dbus-launch --exit-with-session x-session-manager
  &#9500;&#9472;getty,7314 38400 tty1
  &#9500;&#9472;getty,7315 38400 tty2
  &#9500;&#9472;getty,7317 38400 tty4
  &#9500;&#9472;getty,7318 38400 tty5
  &#9500;&#9472;getty,7319 38400 tty6
  &#9500;&#9472;gnome-cups-icon,10999 --sm-client-id default3
  &#9500;&#9472;gnome-keyring-d,10898
  &#9500;&#9472;gnome-panel,10939 --sm-client-id default1
  &#9500;&#9472;gnome-pty-helpe,7783
  &#9500;&#9472;gnome-pty-helpe,5250
  &#9500;&#9472;gnome-pty-helpe,11035
  &#9500;&#9472;gnome-pty-helpe,11157
  &#9500;&#9472;gnome-pty-helpe,12098
  &#9500;&#9472;gnome-pty-helpe,12123
  &#9500;&#9472;gnome-pty-helpe,20315
  &#9500;&#9472;gnome-pty-helpe,20781
  &#9500;&#9472;gnome-pty-helpe,22155
  &#9500;&#9472;gnome-pty-helpe,24583
  &#9500;&#9472;gnome-pty-helpe,5679
  &#9500;&#9472;gnome-pty-helpe,19130
  &#9500;&#9472;gnome-pty-helpe,25758
  &#9500;&#9472;gnome-pty-helpe,27862
  &#9500;&#9472;gnome-settings-,10909 --oaf-activate-iid=OAFIID:GNOME_SettingsDaemon --oaf-ior-fd=25
  &#9500;&#9472;[1mgnome-terminal,27954[0m
  &#9474;   &#9500;&#9472;[1mbash,27957[0m
  &#9474;   &#9474;   &#9492;&#9472;[1msu,27967[0m
  &#9474;   &#9474;       &#9492;&#9472;[1mbash,27970[0m
  &#9474;   &#9474;           &#9492;&#9472;[1mpstree,27973[0m -pah
  &#9474;   &#9492;&#9472;gnome-pty-helpe,27956
  &#9500;&#9472;gnome-vfs-daemo,10956 --oaf-activate-iid=OAFIID:GNOME_VFS_Daemon_Factory --oaf-ior-fd=31
  &#9500;&#9472;gnome-volume-ma,10943 --sm-client-id default4
  &#9500;&#9472;hald,6280
  &#9474;   &#9500;&#9472;hald-addon-acpi,6285
  &#9474;   &#9500;&#9472;hald-addon-stor,6299
  &#9474;   &#9492;&#9472;hald-addon-stor,8218
  &#9500;&#9472;hcid,7194
  &#9500;&#9472;hpiod,6802
  &#9500;&#9472;inetd,6936
  &#9500;&#9472;(kgameportd,5203)
  &#9500;&#9472;(khelper,4)
  &#9500;&#9472;(khubd,1812)
  &#9500;&#9472;(kjournald,2869)
  &#9500;&#9472;(kjournald,4696)
  &#9500;&#9472;klogd,6254 -P /var/run/klogd/kmsg
  &#9500;&#9472;(krfcommd,7210)
  &#9500;&#9472;(kseriod,684)
  &#9500;&#9472;(ksoftirqd/0,2)
  &#9500;&#9472;(kswapd0,98)
  &#9500;&#9472;(kthread,5)
  &#9474;   &#9500;&#9472;(aio/0,99)
  &#9474;   &#9500;&#9472;(kacpid,7)
  &#9474;   &#9500;&#9472;(kblockd/0,68)
  &#9474;   &#9500;&#9472;(pdflush,97)
  &#9474;   &#9492;&#9472;(pdflush,23766)
  &#9500;&#9472;login,12658 --     
  &#9474;   &#9492;&#9472;bash,23778
  &#9474;       &#9492;&#9472;top,23784
  &#9500;&#9472;mapping-daemon,10976
  &#9500;&#9472;master,7037
  &#9474;   &#9500;&#9472;pickup,26786 -l -t fifo -u -c
  &#9474;   &#9492;&#9472;qmgr,7043 -l -t fifo -u -c
  &#9500;&#9472;metacity,10906 --sm-client-id=default0
  &#9500;&#9472;mixer_applet2,10986 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=37
  &#9500;&#9472;nautilus,10941 --no-default-window --sm-client-id default2
  &#9500;&#9472;notification-ar,10983 --oaf-activate-iid=OAFIID:GNOME_NotificationAreaApplet_Factory --oaf-ior-fd=35
  &#9500;&#9472;notification-da,11001
  &#9500;&#9472;postmaster,7066 -c unix_socket_directory=/var/run/postgresql -D /var/lib/postgresql/7.4/main
  &#9474;   &#9492;&#9472;postmaster,7069                                                                                  
  &#9474;       &#9492;&#9472;postmaster,7070                                                                               
  &#9500;&#9472;python,6814 /usr/sbin/hpssd
  &#9500;&#9472;(scsi_eh_0,1851)
  &#9500;&#9472;(scsi_eh_1,1855)
  &#9500;&#9472;(scsi_eh_2,8115)
  &#9500;&#9472;sdpd,7200
  &#9500;&#9472;syslogd,16416 -u syslog
  &#9500;&#9472;tor,7179
  &#9500;&#9472;trashapplet,10990 --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=39
  &#9500;&#9472;udevd,2991 --daemon
  &#9500;&#9472;update-notifier,10960 --sm-client-id default7
  &#9500;&#9472;(usb-storage,1856)
  &#9500;&#9472;(usb-storage,8116)
  &#9500;&#9472;wnck-applet,10974 --oaf-activate-iid=OAFIID:GNOME_Wncklet_Factory --oaf-ior-fd=33
  &#9492;&#9472;xscreensaver,10926 -nosplash

---

### Post by amohanty on 2005-12-04
Have you looked at this:

[http://ubuntuforums.org/showthread.php?t=89491&highlight=sysv-rc-conf](http://ubuntuforums.org/showthread.php?t=89491&highlight=sysv-rc-conf)

AM

---

