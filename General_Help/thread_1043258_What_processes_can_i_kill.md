---
title: "What processes can i kill"
date: 2009-01-18
forum: General Help
---

### Post by timboellis on 2009-01-18
I am trying everything to slim down my server so what of these can i remove without it causing issues

The server is a web server, PHP, MYSQL, Apache with FTP thats it[PHP]D    	Owner    	Started    	Command   
1 	root 	15:21 	/sbin/init
   2470 	root 	15:22 	/sbin/udevd --daemon
   3800 	root 	15:22 	/sbin/getty 38400 tty4
   3801 	root 	15:22 	/sbin/getty 38400 tty5
   3803 	root 	15:22 	/sbin/getty 38400 tty2
   3804 	root 	15:22 	/sbin/getty 38400 tty3
   3805 	root 	15:22 	/sbin/getty 38400 tty1
   3808 	root 	15:22 	/sbin/getty 38400 tty6
   3976 	root 	15:22 	/usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
   4082 	syslog 	15:22 	/sbin/syslogd -u syslog
   4131 	root 	15:22 	/bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
   4133 	klog 	15:22 	/sbin/klogd -P /var/run/klogd/kmsg
   4154 	messagebus 	15:22 	/usr/bin/dbus-daemon --system
   4170 	root 	15:22 	/usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
   4184 	root 	15:22 	/usr/sbin/NetworkManagerDispatcher --pid-file /var/run/NetworkManager/NetworkMan ...
   4197 	root 	15:22 	/usr/bin/system-tools-backends
      4198 	root 	15:22 	dbus-daemon --session --print-address --nofork
   4217 	haldaemon 	15:22 	/usr/sbin/hald
      4218 	root 	15:22 	hald-runner
         4275 	haldaemon 	15:23 	hald-addon-keyboard: listening on /dev/input/event2
         4281 	haldaemon 	15:23 	hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
   4743 	root 	15:23 	/usr/sbin/gdm
      4749 	root 	15:23 	/usr/sbin/gdm
         4799 	root 	15:23 	/usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
         5546 	server 	15:23 	x-session-manager
            5852 	server 	15:23 	/usr/bin/ssh-agent x-session-manager
            6635 	server 	15:23 	/usr/bin/metacity --sm-client-id=default0
            6639 	server 	15:23 	gnome-panel --sm-client-id default1
            6640 	server 	15:23 	nautilus --no-default-window --sm-client-id default2
            6766 	server 	15:24 	vino-session --sm-client-id default5
            6785 	server 	15:24 	nm-applet --sm-disable
   5092 	root 	15:23 	/usr/sbin/cupsd
   
      6437 	avahi 	15:23 	avahi-daemon: chroot helper
   6510 	root 	15:23 	/usr/sbin/dhcdbd --system
      6669 	dhcp 	15:23 	/sbin/dhclient -1 -lf /var/lib/dhcp3/dhclient.eth0.leases -pf /var/run/dhclient. ...
   6550 	root 	15:23 	/usr/sbin/hcid -x -s
      6563 	root 	15:23 	/usr/lib/bluetooth/bluetoothd-service-input
      6579 	root 	15:23 	/usr/lib/bluetooth/bluetoothd-service-audio
   6561 	server 	15:23 	/usr/bin/gnome-keyring-daemon
   6564 	server 	15:23 	dbus-daemon --fork --print-address 18 --print-pid 20 --session
   6566 	server 	15:23 	/usr/lib/gnome-control-center/gnome-settings-daemon
   6656 	daemon 	15:23 	/usr/sbin/atd
   6672 	server 	15:23 	gnome-volume-manager --sm-client-id default4
   6675 	server 	15:23 	/usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-f ...
   6692 	server 	15:23 	/usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
   6704 	server 	15:23 	gnome-screensaver
   6717 	root 	15:24 	/usr/sbin/cron
   6795 	server 	15:24 	
2 	root 	15:21 	[kthreadd]
   3 	root 	15:21 	[migration/0]
   4 	root 	15:21 	[ksoftirqd/0]
   5 	root 	15:21 	[watchdog/0]
   6 	root 	15:21 	[events/0]
   7 	root 	15:21 	[khelper]
   26 	root 	15:21 	[kblockd/0]
   27 	root 	15:21 	[kacpid]
   28 	root 	15:21 	[kacpi_notify]
   62 	root 	15:21 	[kseriod]
   91 	root 	15:21 	[pdflush]
   92 	root 	15:21 	[pdflush]
   93 	root 	15:21 	[kswapd0]
   145 	root 	15:21 	[aio/0]
   1985 	root 	15:22 	[ksuspend_usbd]
   1986 	root 	15:22 	[khubd]
   2102 	root 	15:22 	[ata/0]
   2103 	root 	15:22 	[ata_aux]
   2265 	root 	15:22 	[kjournald]
   4026 	root 	15:22 	[kondemand/0]
   6572 	root 	15:23 	[krfcommd][/PHP]

---

### Post by binbash on 2009-01-18
what kind of server is this? bluetooth gnome-screen saver etc?Remove the gui first.

---

### Post by rsambuca on 2009-01-18
Yeah, if it is just a server, definitely get rid of gnome and gdm.  Getting rid of all the gnome stuff will help you out.

---

