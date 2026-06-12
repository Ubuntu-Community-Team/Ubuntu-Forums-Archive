---
title: "D630 Gutsy xorg issue"
date: 2007-10-23
forum: Dell  Ubuntu Support
---

### Post by slyboots on 2007-10-23
Hi.

When i use Firefox with tabs. When i change between the tabs the firefox work slowly and i see that xorg is on 100% of use at the moment of changing. The same by changing the tabs on gnome-terminal.
Other system programs and features are functional OK.

I have replaced the xorg with other xorg with dpkg-reconfigure xserver-xorg, but still same. I have set off my compiz and Nvidia drivers but same was occurring after that.

I think that is caused by the changing the name of the tab on the top of window... i don't now why..... any idea what can help ?


I use Gutsy on Dell Latitude D630:

My lspci:

```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 135M (rev a1)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)


```

---

### Post by dacap06 on 2007-10-30
According to CNET, the base D630 specs are:
 --  Processor  Intel Core 2 Duo T7100 64 bit processor / 1.8 GHz, 800 MHz FSB with Mobile Intel GM965 Express controller chipset, 2 MB L2 cache.
--  RAM 1 stick of 512 MB (4 GB max) DDR II SDRAM - 667 MHz
That's certainly plenty of hardware horsepower and enough RAM to be comfortable.

I don't think this is an issue with Xorg or with inefficient code in Firefox.  I run the 32 bit Gutsy on the older and much slower Dell Inspiron 5100 laptop, with 512 MB of memory and a desktop P4 CPU and Gutsy/Firefox responsiveness is downright snappy, as was 7.04 Feisty's responsiveness before I upgraded and Mandriva's responsiveness before that.  

The question is -- what is causing your slow responsiveness?  There are two things that commonly cause this kind of behavior:  misconfiguration and swapping.  To diagnose the problem I need more information.  Would you answer the following questions, please?

1. What applications are running when you experience this problem?  Use "ps -aef" command in a terminal window to simply list all of them.  Don't be surprised at the number.  The ps command tells me I have 100 processes running as I type this message  (I used ps -aef | wc -l  to count them).

2. How much memory do you have, and how big is your swap partition? Are you sure swap is turned on?

3. How is Firefox configured?  Are you using a proxy or making a direct connection?  How much cache is Firefox using?  What is the preferred language, and what language are you using in xorg?

4. Are you using laptop power control?  If so, what happens if you turn it off, or turn off CPU throttling?

5. Are you running 32 bit Gutsy or 64 bit Gutsy?

6. Is display response similarly slow for other applications?  What happens when you run a different heavyweight application, like one of the OOo applications?

7. Which Xorg are you using now?  Is it accelerated (although the unaccelerated xorg in my 5100 is still snappy).



Set up Firefox so that you are displaying only two tabs, and use a couple of pages here in ubuntuforums.org.  In a terminal window, run the "top" command

8.  What do the top 5 lines say?

9. When you click a different tab in Firefox, what does top show as the top few processes that are occupying most of the CPU, and roughly what fraction of CPU utilizations does each use?

10. Change the top command to order the process list by memory use instead of CPU use (enter O, followed by N, followed by <cr>).  What task uses the most memory, and how much does it use?  My Firefox with 5 tabs uses 21.8% of memory.

---

### Post by slyboots on 2007-10-30
Hi dacap06.
Thanks for you trying to help me.
My config is Intel Core 2 Duo T7300 2.00 GHz, 2GB ram 667Mhz, 2GB swap (active), Nvidia Quadro NVS 135M 256MB (not integrated) CPU frequency 400MHz, PCI-E 16x.

1. # ps -aef | wc -l  
# 132 

2.
```

sly@zer0:~$ ps -aef
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 23:39 ?        00:00:01 /sbin/init
root         2     0  0 23:39 ?        00:00:00 [kthreadd]
root         3     2  0 23:39 ?        00:00:00 [migration/0]
root         4     2  0 23:39 ?        00:00:00 [ksoftirqd/0]
root         5     2  0 23:39 ?        00:00:00 [watchdog/0]
root         6     2  0 23:39 ?        00:00:00 [migration/1]
root         7     2  0 23:39 ?        00:00:00 [ksoftirqd/1]
root         8     2  0 23:39 ?        00:00:00 [watchdog/1]
root         9     2  0 23:39 ?        00:00:00 [events/0]
root        10     2  0 23:39 ?        00:00:00 [events/1]
root        11     2  0 23:39 ?        00:00:00 [khelper]
root        31     2  0 23:39 ?        00:00:00 [kblockd/0]
root        32     2  0 23:39 ?        00:00:00 [kblockd/1]
root        33     2  0 23:39 ?        00:00:00 [kacpid]
root        34     2  0 23:39 ?        00:00:00 [kacpi_notify]
root       192     2  0 23:39 ?        00:00:00 [kseriod]
root       220     2  0 23:39 ?        00:00:00 [pdflush]
root       221     2  0 23:39 ?        00:00:00 [pdflush]
root       222     2  0 23:39 ?        00:00:00 [kswapd0]
root       273     2  0 23:39 ?        00:00:00 [aio/0]
root       274     2  0 23:39 ?        00:00:00 [aio/1]
root      1349     2  0 23:39 ?        00:00:00 [ksnapd]
root      1652     2  3 23:39 ?        00:00:30 [kcryptd/0]
root      1653     2  3 23:39 ?        00:00:30 [kcryptd/1]
root      2239     2  0 23:39 ?        00:00:00 [ksuspend_usbd]
root      2240     2  0 23:39 ?        00:00:00 [khubd]
root      2317     2  0 23:39 ?        00:00:00 [ata/0]
root      2318     2  0 23:39 ?        00:00:00 [ata/1]
root      2319     2  0 23:39 ?        00:00:00 [ata_aux]
root      2338     2  0 23:39 ?        00:00:00 [khpsbpkt]
root      2419     2  0 23:39 ?        00:00:00 [scsi_eh_0]
root      2420     2  0 23:39 ?        00:00:00 [scsi_eh_1]
root      2427     2  0 23:39 ?        00:00:00 [scsi_eh_2]
root      2428     2  0 23:39 ?        00:00:00 [scsi_eh_3]
root      2449     2  0 23:39 ?        00:00:00 [knodemgrd_0]
root      2716     2  0 23:39 ?        00:00:00 [kjournald]
root      2937     1  0 23:39 ?        00:00:00 /sbin/udevd --daemon
root      3992     2  0 23:39 ?        00:00:00 [pccardd]
root      4002     2  0 23:39 ?        00:00:00 [kpsmoused]
root      4137     2  0 23:39 ?        00:00:00 [iwl4965/0]
root      4138     2  0 23:39 ?        00:00:00 [iwl4965/1]
root      4153     2  0 23:39 ?        00:00:00 [iwl4965]
root      4631     2  0 23:41 ?        00:00:00 [kjournald]
root      4634     1  0 23:41 ?        00:00:00 /sbin/mount.ntfs /dev/sda2 /media/sda2 -o rw,umask=007,gid=46
root      4870     1  0 23:41 tty4     00:00:00 /sbin/getty 38400 tty4
root      4871     1  0 23:41 tty5     00:00:00 /sbin/getty 38400 tty5
root      4875     1  0 23:41 tty2     00:00:00 /sbin/getty 38400 tty2
root      4876     1  0 23:41 tty3     00:00:00 /sbin/getty 38400 tty3
root      4877     1  0 23:41 tty1     00:00:00 /sbin/getty 38400 tty1
root      4878     1  0 23:41 tty6     00:00:00 /sbin/getty 38400 tty6
root      5088     1  0 23:41 ?        00:00:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      5116     2  0 23:41 ?        00:00:00 [kondemand/0]
root      5117     2  0 23:41 ?        00:00:00 [kondemand/1]
syslog    5206     1  0 23:41 ?        00:00:00 /sbin/syslogd -u syslog
root      5263     1  0 23:41 ?        00:00:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      5265     1  0 23:41 ?        00:00:00 /sbin/klogd -P /var/run/klogd/kmsg
103       5286     1  0 23:41 ?        00:00:00 /usr/bin/dbus-daemon --system
root      5302     1  0 23:41 ?        00:00:00 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
root      5316     1  0 23:41 ?        00:00:00 /usr/sbin/NetworkManagerDispatcher --pid-file /var/run/NetworkManager/NetworkManagerDispatcher.pid
root      5329     1  0 23:41 ?        00:00:00 /usr/bin/system-tools-backends
root      5330  5329  0 23:41 ?        00:00:00 dbus-daemon --session --print-address --nofork
107       5349     1  0 23:41 ?        00:00:00 /usr/sbin/hald
root      5350  5349  0 23:41 ?        00:00:00 hald-runner
107       5411  5350  0 23:41 ?        00:00:00 hald-addon-keyboard: listening on /dev/input/event1
root      5413  5350  0 23:41 ?        00:00:00 /usr/lib/hal/hald-addon-cpufreq
107       5414  5350  0 23:41 ?        00:00:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
107       5415  5350  0 23:41 ?        00:00:00 hald-addon-keyboard: listening on /dev/input/event5
107       5416  5350  0 23:41 ?        00:00:00 hald-addon-keyboard: listening on /dev/input/event6
107       5417  5350  0 23:41 ?        00:00:00 hald-addon-keyboard: listening on /dev/input/event7
root      5422     1  0 23:41 ?        00:00:00 /usr/sbin/cupsd
root      5473     1  0 23:41 ?        00:00:00 /usr/sbin/battery-stats-collector --syslog --output /var/log/battery-stats --interval=60 --flush=10 --ignore-missing-b
107       5484  5350  0 23:41 ?        00:00:00 hald-addon-storage: polling /dev/scd0 (every 2 sec)
gkrellmd  5553     1  6 23:41 ?        00:00:49 /usr/bin/gkrellmd
root      5570     1  0 23:41 ?        00:00:00 /usr/sbin/console-kit-daemon
avahi     5657     1  0 23:41 ?        00:00:00 avahi-daemon: running [zer0.local]
avahi     5658  5657  0 23:41 ?        00:00:00 avahi-daemon: chroot helper
root      5672     1  0 23:41 ?        00:00:00 /usr/sbin/dhcdbd --system
root      5692     1  0 23:41 ?        00:00:00 /usr/sbin/hcid -x -s
root      5709  5692  0 23:41 ?        00:00:00 /usr/lib/bluetooth/bluetoothd-service-audio
root      5710  5692  0 23:41 ?        00:00:00 /usr/lib/bluetooth/bluetoothd-service-input
root      5725     2  0 23:41 ?        00:00:00 [krfcommd]
root      5746     1  0 23:41 ?        00:00:00 /usr/sbin/gdm
root      5753  5746  0 23:41 ?        00:00:00 /usr/sbin/gdm
root      5760  5753  4 23:41 tty7     00:00:36 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
daemon    5806     1  0 23:41 ?        00:00:00 /usr/sbin/atd
root      5820     1  0 23:41 ?        00:00:00 /usr/sbin/cron
sly       5963     1  0 23:43 ?        00:00:00 /usr/bin/gnome-keyring-daemon -d
sly       5966  5753  0 23:43 ?        00:00:00 /usr/bin/gnome-session
sly       6006  5966  0 23:43 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/gnome-session
sly       6008     1  0 23:43 ?        00:00:00 /usr/lib/libgconf2-4/gconfd-2 6
sly       6012     1  0 23:43 ?        00:00:00 dbus-daemon --fork --print-address 17 --print-pid 19 --session
sly       6014     1  0 23:43 ?        00:00:00 /usr/lib/gnome-control-center/gnome-settings-daemon
sly       6020  5966  0 23:43 ?        00:00:01 gnome-panel --sm-client-id default1
sly       6022  5966  0 23:43 ?        00:00:01 nautilus --no-default-window --sm-client-id default2
sly       6026     1  0 23:43 ?        00:00:00 gnome-volume-manager --sm-client-id default4
sly       6028     1  0 23:43 ?        00:00:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=16
sly       6034  5966  0 23:43 ?        00:00:00 vino-session --sm-client-id default5
sly       6036     1  0 23:43 ?        00:00:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
sly       6037  5966  0 23:43 ?        00:00:00 bluetooth-applet
sly       6039  5966  0 23:43 ?        00:00:00 update-notifier
sly       6047  5966  5 23:43 ?        00:00:41 gkrellm
sly       6048  5966  0 23:43 ?        00:00:00 /usr/bin/python /usr/local/bin/fusion-icon
sly       6049  5966  0 23:43 ?        00:00:00 /usr/lib/evolution/2.12/evolution-alarm-notify
sly       6054  5966  0 23:43 ?        00:00:00 trackerd
sly       6081  5966  0 23:43 ?        00:00:00 nm-applet --sm-disable
sly       6083  5966  0 23:43 ?        00:00:00 python /usr/share/system-config-printer/applet.py
sly       6092     1  0 23:43 ?        00:00:00 gnome-power-manager
sly       6097     1  0 23:43 ?        00:00:00 gnome-screensaver
sly       6146     1  0 23:43 ?        00:00:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=19
sly       6162     1  0 23:43 ?        00:00:00 /usr/lib/evolution/2.12/evolution-exchange-storage --oaf-activate-iid=OAFIID:GNOME_Evolution_Exchange_Connector_CalFac
sly       6166     1  0 23:43 ?        00:00:00 /usr/lib/nautilus-cd-burner/mapping-daemon
sly       6171     1  0 23:43 ?        00:00:00 /usr/lib/evolution/evolution-data-server-1.12 --oaf-activate-iid=OAFIID:GNOME_Evolution_DataServer_CalFactory:1.2 --oa
root      6173     1  0 23:43 ?        00:00:00 /sbin/wpa_supplicant -g /var/run/wpa_supplicant-global3
sly       6191  6048  5 23:43 ?        00:00:38 compiz --replace --sm-disable --ignore-desktop-hints ccp --loose-binding
sly       6218     1  0 23:43 ?        00:00:00 /usr/lib/gnome-applets/multiload-applet-2 --oaf-activate-iid=OAFIID:GNOME_MultiLoadApplet_Factory --oaf-ior-fd=25
dhcp      6231  5672  0 23:43 ?        00:00:00 /sbin/dhclient -1 -lf /var/lib/dhcp3/dhclient.wlan0.leases -pf /var/run/dhclient.wlan0.pid -q -e dhc_dbus=31 -d wlan0
sly       6237  6191  0 23:43 ?        00:00:00 /bin/sh -c emerald --replace
sly       6238  6237  0 23:43 ?        00:00:00 emerald --replace
sly       6254     1  0 23:43 ?        00:00:00 /usr/lib/fast-user-switch-applet/fast-user-switch-applet --oaf-activate-iid=OAFIID:GNOME_FastUserSwitchApplet_Factory
sly       6256     1  0 23:43 ?        00:00:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=35
sly       6258     1  0 23:43 ?        00:00:01 /usr/bin/python /usr/lib/deskbar-applet/deskbar-applet --oaf-activate-iid=OAFIID:Deskbar_Applet_Factory --oaf-ior-fd=4
sly       6632  6191  0 23:51 ?        00:00:00 /bin/sh -c gnome-terminal
sly       6633  6632  0 23:51 ?        00:00:00 gnome-terminal
sly       6635  6633  0 23:51 ?        00:00:00 gnome-pty-helper
sly       6636  6633  0 23:51 pts/0    00:00:00 bash
sly       6667     1  0 23:51 ?        00:00:00 /bin/sh /usr/bin/firefox
sly       6679  6667  0 23:51 ?        00:00:00 /bin/sh /usr/lib/firefox/run-mozilla.sh /usr/lib/firefox/firefox-bin
sly       6683  6679  6 23:51 ?        00:00:12 /usr/lib/firefox/firefox-bin
sly       6812  6633  0 23:53 pts/1    00:00:00 bash
sly       6886  6812  0 23:55 pts/1    00:00:00 ps -aef


```

2.
swap partition is turned on, i have 2 GB 667MHz Ram

3.
Some plugins are in firefox, but without plugins and when i remove the config and run only clean install of firefox still all same, I am connected directly, My prefered language is englisch and xorg is using the same. The cache of Firefox is 80MB and was cleared.

4.
I am using power control that is defould in Gutsy Gibon, but i turned all off in bios too becouse i have maked a research and without power save mode is all the same.

5.
The system is 32bit.

6.
Other aplications are functionaly ok and xorg is not used too much like by the firefox and gnome-terminal tabs. Other aplications are used normaly without any performance issues.

7.
I have the defould xorg from Ubuntu 7.10 after install

8.
i have try to make a new xorg with dpkg-reconfigure xorg and try different configurations. 

9.
**top:**
```

 5760 root      15   0 81268  38m 8284 S   31  1.9   1:35.60 Xorg                                                                                                     
 6191 sly       15   0 63412  28m  10m S    9  1.4   1:34.33 compiz                                                                                                   
 6683 sly       15   0  212m  75m  22m S    6  3.7   0:53.80 firefox-bin                                                                                              
 6047 sly       16   0 34048  13m 9404 S    6  0.7   1:19.98 gkrellm                                                                                                  
 5553 gkrellmd  16   0 11160 1192  980 S    4  0.1   1:33.01 gkrellmd                                                                                                 
 6020 sly       15   0 51876  18m  13m S    2  0.9   0:02.67 gnome-panel                                                                                              
 6238 sly       15   0 17560 9832 6544 S    0  0.5   0:01.54 emerald                                                                                                  
 6633 sly       15   0 81068  21m  12m S    0  1.1   0:01.28 gnome-terminal                                                                                           
 7278 sly       15   0  2368 1180  876 R    0  0.1   0:00.07 top                         

```

10.

```

 1.9 80936  5760 root      15   0  38m 8284 S   36   1:44.78 Xorg                                                                                                     
 1.4 63416  6191 sly       15   0  28m  10m S   13   1:37.41 compiz                                                                                                   
 0.1 11160  5553 gkrellmd  15   0 1192  980 S    7   1:38.82 gkrellmd                                                                                                 
 0.7 34048  6047 sly       15   0  13m 9404 S    6   1:25.30 gkrellm                                                                                                  
 3.7  212m  6683 sly       15   0  75m  22m S    4   0:57.51 firefox-bin                                                                                              
 0.9 51876  6020 sly       15   0  18m  13m S    1   0:02.82 gnome-panel                                                                                              
 0.2 16676  6097 sly       15   0 4968 3940 S    1   0:01.10 gnome-screensav                                                                                          
 0.4 19808  6218 sly       16   0 8148 6844 S    0   0:01.15 multiload-apple                                                                                          
 0.5 17596  6238 sly       15   0 9868 6544 S    0   0:01.76 emerald                                                                                                  
 1.1 81240  6633 sly       15   0  21m  12m S    0   0:01.57 gnome-terminal                                                                                           
 0.1  2368  7278 sly       15   0 1184  880 R    0   0:00.30 top                                                                                                      
 0.1  2948     1 root      18   0 1856  532 S    0   0:01.98 init          

```

[B]I have make a litle research. The xorg is not the soure i think too. The issue is occuring by Emerald (compiz fusion). When i change to GTK window manager -> i see a litle usage of xorg in top, but it not freeze the system. 

After some research via Google i found this [http://www.nvnews.net/vbulletin/showthread.php?t=96778](http://www.nvnews.net/vbulletin/showthread.php?t=96778)
it is looking like my issues. I have reinstalled the compiz fusion to the newest version (Git) but same issue is occuring. I use the Nvidia driver from restricted drivers. The verion is 100.14.19 installed with the restricted drivers control after install of Gutsy.

Many thanks for future help.

[/B]

---

### Post by dacap06 on 2007-10-30
I looked through the information that you reported and everything looks normal.  I agree with you - Compiz Fusion is the likely problem.   Your best bet is to turn it off for now.  

An alternative is to install the package "xdebconfigurator" and use it to change the X11 configuration.  Maybe you can find a different xorg configuration that will help. Before you run xdebconfigurator, be sure to save /etc/X11/xorg.conf to a backup file.  If you hammer your configuration and X won't start, you can copy the old version back over the hammered version and get back your X-windows.

Good luck!

---

### Post by slyboots on 2007-10-31
Thansk for info. I will check it. Some aditional info. The issue is occuring mostly when i write a mail i Thunderbird or when i get access to different folders in mc or via command prompt in gnome-terminal or when i change the tabs in firefox. I see that by the writing the mail for example is changing the summary of name in the title bar and that is causing big usage of Xorg and same is occuring by change of tab, becouse the title bar is changing too.

---

### Post by phelge on 2007-10-31
Slyboots, I think I have the same problem. There are a lot of threads about slowness with xorg, firefox, compiz,...but I didn't really find my current problem. Slowness for me occurs :
- with firefox tab switching, I see the cpu of xorg process climbing to 60% or more
- the same with epiphany and opera
- disabling compiz/emerald do not improve
- disabling nvidia driver and using nv driver instead do not improve
- with compiz enabled and emerald disabled , it's clearly better but tab switching still makes xorg eating 20/25% of cpu

On the other hand, switching tabs of gnome-term do not eat cpu.

My computer is a brand new laptop HP 8710w, with nvidia quadro FX1600 (~8700gt).

---

### Post by dacap06 on 2007-10-31
Slyboots and Phledge:

I noticed something you will find useful -- I don't think you are running the correct video driver.  I only just now noticed that you both have nvidia quadro display cards.

Neither the nv nor the nvidia driver in the repository is the correct driver for the quadro series of cards, and the quadro driver is not in the repository.  Using either the nv or the nvidia driver with the quadro card causes all kinds of wierdness with resolutions and slowness of operation.  I know this from personal experience with a quadro card in a machine at work.

Before you make any changes, make a backup copy of /etc/X11/xorg.conf (for example, "sudo cp /etc/X11/xorg.conf  /etc/X11/xorg.conf.saved-slow-version") so that you can restore it from the command line if something goes hideously wrong.

Once you have your backup, you'll need to download the driver direct from nvidia and follow their instructions for running the install script.  You can enter the information for your card in a browser at [this URL here]("http://www.nvidia.com/Download/index.aspx?lang=en-us") and begin the download process.

After you do the installation, WHATEVER YOU DO don't change the card driver!

Good luck!

---

### Post by phelge on 2007-11-01
Thanks for the tip. I did it but no improvment.

---

### Post by dacap06 on 2007-11-01
Phelge,

No improvement?  Ouch.  I'm out of ideas.

Sorry,

DaCAP

---

