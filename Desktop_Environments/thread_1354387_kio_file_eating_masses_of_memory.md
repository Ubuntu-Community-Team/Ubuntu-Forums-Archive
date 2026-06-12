---
title: "kio_file eating masses of memory"
date: 2009-12-13
forum: Desktop Environments
---

### Post by IanBall on 2009-12-13
Hi,

I've had this problem for the last couple of days now with no apparent explanation.  My machine has masses of it's memory eaten up by kio_file, the last look it had taken 3.2Gb from  my 4Gb ram.  The machine itself is 64 bit (from cpu info: AMD Athlon(tm) 64 X2 Dual Core Processor 5200+)
One post ([http://ubuntuforums.org/showthread.php?t=1129676](http://ubuntuforums.org/showthread.php?t=1129676)) suggested it's caused by ktorrent, however I haven't had ktorrent running, so that can't be the cause.  It did eventually die, or maybe it was killed by the kernel, however it slowed my machine to an unusable state.  Does anyone have any ideas what's going on, or should I file a bug regarding yet another problem in the KDE4 disaster?

top - 01:56:49 up 3 days,  8:32,  1 user,  load average: 5.34, 3.19, 1.74
Tasks: 178 total,   1 running, 177 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.8%us,  1.5%sy,  0.0%ni, 48.2%id, 49.3%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   4060760k total,  4032576k used,    28184k free,     2660k buffers
Swap:  4104504k total,  1832760k used,  2271744k free,    28720k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
14937 ian       20   0 3576m 2.7g    8 D    0 70.5  34:47.95 kio_file
 6120 ian       20   0 1240m 225m 3288 S    0  5.7  19:58.54 konqueror
14347 ian       20   0  613m  79m 1964 S    0  2.0  19:50.90 firefox
 1481 root      20   0  677m  48m 3304 S    0  1.2  24:46.37 Xorg
20597 ian       20   0  277m  15m  11m D    2  0.4   0:00.26 kate
 2227 ian       20   0  359m  13m 7040 S    0  0.3   7:28.67 compiz.real
 2231 ian       20   0  347m  12m 1336 S    0  0.3   1:08.16 gnome-panel
 2233 ian       20   0  557m  12m  968 S    0  0.3   4:35.11 nautilus
 2592 ian       20   0  682m  10m 1124 S    0  0.3   0:03.72 knotify4
 2326 ian       20   0  465m  10m 2540 S    0  0.3   1:03.20 konsole
12733 ian       20   0  217m 8824  208 S    0  0.2   1:24.64 npviewer.bin
17509 root      20   0  361m 5312  300 S    0  0.1   0:00.81 VirtualBox
 2587 ian       20   0  569m 4412 1128 S    0  0.1   0:27.97 kded4
 2066 ian       20   0  201m 4164 1192 S    0  0.1   0:01.31 gnome-session
 7500 ian       20   0  269m 3372 1040 S    0  0.1   0:00.37 kglobalaccel
 2275 ian       20   0  207m 2828  916 S    0  0.1   0:33.03 gtk-window-deco
 2134 ian       20   0  301m 2596 1004 S    0  0.1   0:26.26 gnome-settings-
 6204 ian       20   0  269m 2536 1056 S    0  0.1   0:00.63 kwalletd


top - 01:57:31 up 3 days,  8:33,  1 user,  load average: 3.83, 3.08, 1.76
Tasks: 178 total,   1 running, 177 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.1%us,  1.8%sy,  0.0%ni, 48.5%id, 47.4%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   4060760k total,  4032256k used,    28504k free,      256k buffers
Swap:  4104504k total,  1906388k used,  2198116k free,    18048k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
14937 ian       20   0 3576m 2.9g    8 D    3 74.6  34:48.44 kio_file
 6120 ian       20   0 1240m 221m 3592 S    0  5.6  19:58.88 konqueror
14347 ian       20   0  613m  77m 2232 S    1  2.0  19:51.19 firefox
 1481 root      20   0  677m  51m 3536 S    1  1.3  24:46.96 Xorg
20597 ian       20   0  362m  18m 6556 S    0  0.5   0:00.91 kate
 2231 ian       20   0  347m  14m 3400 S    0  0.4   1:08.23 gnome-panel
 2227 ian       20   0  359m  13m 7276 S    1  0.3   7:29.06 compiz.real
 2233 ian       20   0  557m  11m  856 S    0  0.3   4:35.11 nautilus
 2326 ian       20   0  465m  11m 3152 S    1  0.3   1:03.48 konsole
 2592 ian       20   0  682m  10m  924 S    0  0.3   0:03.72 knotify4
12733 ian       20   0  217m 9104  492 S    0  0.2   1:24.70 npviewer.bin
17509 root      20   0  361m 5268  312 S    0  0.1   0:00.81 VirtualBox
 2275 ian       20   0  207m 4244 2084 S    0  0.1   0:33.08 gtk-window-deco
 2587 ian       20   0  569m 4208  992 S    0  0.1   0:27.97 kded4
 2066 ian       20   0  201m 3740  772 S    0  0.1   0:01.31 gnome-session
 7500 ian       20   0  269m 3144  872 S    0  0.1   0:00.39 kglobalaccel
 2151 ian       20   0  200m 2460  800 S    0  0.1   0:03.31 notify-osd
18256 ian       20   0  146m 2444  776 S    0  0.1   0:00.03 kio_file
 2134 ian       20   0  301m 2396  852 S    0  0.1   0:26.26 gnome-settings-
 6204 ian       20   0  269m 2296  868 S    0  0.1   0:00.63 kwalletd




ian@goanna:~/Downloads/Windows$ ps auxfh                                                                                                                                      
root         2  0.0  0.0      0     0 ?        S<   Dec10   0:00 [kthreadd]                                                                                                   
root         3  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [migration/0]                                                                                            
root         4  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [ksoftirqd/0]                                                                                            
root         5  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [watchdog/0]                                                                                             
root         6  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [migration/1]                                                                                            
root         7  0.0  0.0      0     0 ?        S<   Dec10   0:04  \_ [ksoftirqd/1]                                                                                            
root         8  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [watchdog/1]                                                                                             
root         9  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [events/0]                                                                                               
root        10  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [events/1]                                                                                               
root        11  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [cpuset]                                                                                                 
root        12  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [khelper]                                                                                                
root        13  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [netns]                                                                                                  
root        14  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [async/mgr]                                                                                              
root        15  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [kintegrityd/0]                                                                                          
root        16  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [kintegrityd/1]                                                                                          
root        17  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [kblockd/0]                                                                                              
root        18  0.0  0.0      0     0 ?        S<   Dec10   0:01  \_ [kblockd/1]                                                                                              
root        19  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [kacpid]                                                                                                 
root        20  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [kacpi_notify]                                                                                           
root        21  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [kacpi_hotplug]                                                                                          
root        22  0.0  0.0      0     0 ?        S<   Dec10   0:02  \_ [ata/0]                                                                                                  
root        23  0.0  0.0      0     0 ?        S<   Dec10   0:21  \_ [ata/1]                                                                                                  
root        24  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [ata_aux]                                                                                                
root        25  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [ksuspend_usbd]                                                                                          
root        26  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [khubd]                                                                                                  
root        27  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [kseriod]                                                                                                
root        28  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [kmmcd]                                                                                                  
root        29  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [bluetooth]                                                                                              
root        30  0.0  0.0      0     0 ?        S    Dec10   0:00  \_ [khungtaskd]                                                                                             
root        33  0.0  0.0      0     0 ?        D<   Dec10   0:56  \_ [kswapd0]                                                                                                
root        34  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [aio/0]                                                                                                  
root        35  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [aio/1]                                                                                                  
root        36  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [ecryptfs-kthrea]                                                                                        
root        37  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [crypto/0]                                                                                               
root        38  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [crypto/1]                                                                                               
root        47  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [scsi_eh_0]                                                                                              
root        48  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [scsi_eh_1]                                                                                              
root        49  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [scsi_eh_2]                                                                                              
root        50  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [scsi_eh_3]                                                                                              
root        54  0.0  0.0      0     0 ?        S<   Dec10   0:38  \_ [scsi_eh_4]                                                                                              
root        56  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [scsi_eh_5]                                                                                              
root        61  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [kstriped]                                                                                               
root        62  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [kmpathd/0]                                                                                              
root        63  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [kmpathd/1]                                                                                              
root        64  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [kmpath_handlerd]                                                                                        
root        65  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [ksnapd]                                                                                                 
root        66  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [kondemand/0]                                                                                            
root        67  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [kondemand/1]                                                                                            
root        68  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [kconservative/0]                                                                                        
root        69  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [kconservative/1]                                                                                        
root        70  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [krfcommd]                                                                                               
root       332  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [usbhid_resumer]                                                                                         
root       358  0.0  0.0      0     0 ?        S<   Dec10   0:02  \_ [md0_raid1]                                                                                              
root       363  0.0  0.0      0     0 ?        S<   Dec10   0:02  \_ [md1_raid1]                                                                                              
root       370  0.0  0.0      0     0 ?        S<   Dec10   0:06  \_ [md2_raid1]                                                                                              
root       470  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [kjournald2]                                                                                             
root       550  0.0  0.0      0     0 ?        S<   Dec10   0:20  \_ [kjournald2]                                                                                             
root       853  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [edac-poller]                                                                                            
root       861  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [kpsmoused]                                                                                              
root       998  0.0  0.0      0     0 ?        S<   Dec10   0:00  \_ [hd-audio0]                                                                                              
root     15290  0.0  0.0      0     0 ?        S    Dec13   0:01  \_ [pdflush]                                                                                                
root     20590  0.0  0.0      0     0 ?        S    01:54   0:00  \_ [pdflush]                                                                                                
root         1  0.0  0.0  19444    56 ?        Ss   Dec10   0:00 /sbin/init                                                                                                   
root       529  0.0  0.0  12768     4 ?        S    Dec10   0:00 upstart-udev-bridge --daemon                                                                                 
root       562  0.0  0.0  17296     0 ?        S<s  Dec10   0:00 udevd --daemon                                                                                               
root     17671  0.0  0.0  17292     0 ?        S<   Dec13   0:00  \_ udevd --daemon                                                                                           
root     17672  0.0  0.0  17292     0 ?        S<   Dec13   0:00  \_ udevd --daemon                                                                                           
root       713  0.0  0.0   8192     4 ?        Ss   Dec10   0:00 dd bs=1 if=/proc/kmsg of=/var/run/rsyslog/kmsg                                                               
syslog     823  0.0  0.0 126388     4 ?        Sl   Dec10   0:00 rsyslogd -c4                                                                                                 
root      1023  0.0  0.0   5988     4 tty4     Ss+  Dec10   0:00 /sbin/getty -8 38400 tty4                                                                                    
root      1027  0.0  0.0   5988     4 tty5     Ss+  Dec10   0:00 /sbin/getty -8 38400 tty5                                                                                    
root      1035  0.0  0.0   5988     4 tty2     Ss+  Dec10   0:00 /sbin/getty -8 38400 tty2                                                                                    
root      1036  0.0  0.0   5988     4 tty3     Ss+  Dec10   0:00 /sbin/getty -8 38400 tty3                                                                                    
root      1038  0.0  0.0   5988     4 tty6     Ss+  Dec10   0:00 /sbin/getty -8 38400 tty6                                                                                    
root      1041  0.0  0.0   4352     0 ?        Ss   Dec10   0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket                                                           
daemon    1046  0.0  0.0  16512     0 ?        Ss   Dec10   0:00 atd                                                                                                          
root      1047  0.0  0.0  18708   212 ?        Ss   Dec10   0:00 cron                                                                                                         
102       1081  0.0  0.0  24524   264 ?        Ss   Dec10   0:05 dbus-daemon --system --fork                                                                                  
root      1086  0.0  0.0  49072     0 ?        Ss   Dec10   0:00 /usr/sbin/sshd                                                                                               
avahi     1097  0.0  0.0  31884    20 ?        Ss   Dec10   0:00 avahi-daemon: running [goanna.local]                                                                         
avahi     1098  0.0  0.0  31760     0 ?        Ss   Dec10   0:00  \_ avahi-daemon: chroot helper                                                                              
root      1171  0.0  0.0 120380   100 ?        Ssl  Dec10   0:00 /usr/sbin/console-kit-daemon                                                                                 
root      1258  0.0  0.0  74940    60 ?        Ss   Dec10   0:00 gdm-binary                                                                                                   
root      1449  0.0  0.0  76864    44 ?        S    Dec10   0:00  \_ /usr/lib/gdm/gdm-simple-slave --display-id /org/gnome/DisplayManager/Display1                            
root      1481  0.5  0.5 693636 23396 tty7     Ss+  Dec10  24:49      \_ /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-3BSkay/database -nolisten tcp vt7         
root      2018  0.0  0.0  89308     4 ?        S    Dec10   0:00      \_ /usr/lib/gdm/gdm-session-worker                                                                      
ian       2066  0.0  0.0 206368    36 ?        Ssl  Dec10   0:01          \_ gnome-session                                                                                    
ian       2112  0.0  0.0  36060    68 ?        Ss   Dec10   0:00              \_ /usr/bin/ssh-agent /usr/bin/gpg-agent --daemon --sh --write-env-file=/home/ian/.gnupg/gpg-agent-info-goanna /usr/bin/dbus-launch
ian       2113  0.0  0.0  16436   192 ?        Ss   Dec10   0:01              \_ /usr/bin/gpg-agent --daemon --sh --write-env-file=/home/ian/.gnupg/gpg-agent-info-goanna /usr/bin/dbus-launch --exit-with-session
ian       2154  0.0  0.0   4004     4 ?        S    Dec10   0:00              \_ /bin/sh /usr/bin/compiz                                                                                                          
ian       2227  0.1  0.2 343772 11984 ?        S    Dec10   7:31              |   \_ /usr/bin/compiz.real --ignore-desktop-hints --replace --sm-client-id 107066e3dbebd64909126046229394317400000020660022 --loose
ian       2274  0.0  0.0   4004     4 ?        Ss   Dec10   0:00              |       \_ /bin/sh -c /usr/bin/compiz-decorator                                                                                     
ian       2275  0.0  0.0 212940  3444 ?        S    Dec10   0:33              |           \_ /usr/bin/gtk-window-decorator                                                                                        
ian       2231  0.0  0.2 356232  8240 ?        S    Dec10   1:08              \_ gnome-panel                                                                                                                      
ian       2233  0.0  0.0 571332  2452 ?        S    Dec10   4:35              \_ nautilus                                                                                                                         
ian       2237  0.0  0.0 221780     8 ?        S    Dec10   0:01              \_ python /usr/share/system-config-printer/applet.py                                                                                
ian       2239  0.0  0.0 194440   492 ?        S    Dec10   0:06              \_ update-notifier --startup-delay=60                                                                                               
ian       2244  0.0  0.0 191016   564 ?        S    Dec10   0:00              \_ /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1                                                                   
ian       2246  0.0  0.0 242076   152 ?        S    Dec10   0:01              \_ nm-applet --sm-disable                                                                                                           
ian       2249  0.0  0.0 152116    64 ?        S    Dec10   0:00              \_ bluetooth-applet                                                                                                                 
ian       2252  0.0  0.0 188816   524 ?        S    Dec10   0:01              \_ gnome-power-manager                                                                                                              
ian       2255  0.0  0.0 160236    64 ?        S    Dec10   0:00              \_ /usr/lib/gnome-disk-utility/gdu-notification-daemon                                                                              
ian       2265  0.0  0.0 429172     4 ?        Sl   Dec10   0:00              \_ /usr/lib/evolution/2.28/evolution-alarm-notify                                                                                   
ian       2267  0.0  0.0 272640     4 ?        S    Dec10   0:00              \_ gnome-volume-control-applet                                                                                                      
root      1280  0.0  0.0  89400    56 ?        Ssl  Dec10   0:00 NetworkManager                                                                                                                                   
root      1320  0.0  0.0   6464     4 ?        S    Dec10   0:00  \_ /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth0.pid -lf /var/lib/dhcp3/dhclient-e4eb7d4a-6ab9-
root      1286  0.0  0.0  51476    24 ?        S    Dec10   0:00 /usr/sbin/modem-manager                                                                                                                          
root      1318  0.0  0.0  28216     4 ?        S    Dec10   0:00 /sbin/wpa_supplicant -u -s                                                                                                                       
root      1643  0.0  0.0  12636   236 ?        Ss   Dec10   0:00 /sbin/mdadm --monitor --pid-file /var/run/mdadm/monitor.pid --daemonise --scan --syslog                                                          
root      1668  0.0  0.0  75280     4 ?        Ss   Dec10   0:00 /usr/sbin/cupsd -C /etc/cups/cupsd.conf                                                                                                          
root      1944  0.0  0.0   5988     4 tty1     Ss+  Dec10   0:00 /sbin/getty -8 38400 tty1                                                                                                                        
gdm       1967  0.0  0.0  26156     0 ?        S    Dec10   0:00 /usr/bin/dbus-launch --exit-with-session                                                                                                         
root      1972  0.0  0.0  46988    20 ?        S    Dec10   0:00 /usr/lib/devicekit-power/devkit-power-daemon                                                                                                     
ian       2051  0.0  0.0 169196     4 ?        Sl   Dec10   0:00 /usr/bin/gnome-keyring-daemon --daemonize --login                                                                                                
ian       2116  0.0  0.0  26156     0 ?        S    Dec10   0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session gnome-session                                                                    
ian       2117  0.0  0.0  25884     4 ?        Ss   Dec10   0:49 /bin/dbus-daemon --fork --print-pid 7 --print-address 9 --session                                                                                
ian       2121  0.1  0.0 207868   184 ?        Ssl  Dec10   5:41 /usr/bin/pulseaudio --start                                                                                                                      
ian       2124  0.0  0.0  94308     4 ?        S    Dec10   0:00  \_ /usr/lib/pulseaudio/pulse/gconf-helper                                                                                                       
ian       2126  0.0  0.0  46476  1108 ?        S    Dec10   0:10 /usr/lib/libgconf2-4/gconfd-2                                                                                                                    
ian       2134  0.0  0.0 308292  1352 ?        Ssl  Dec10   0:26 /usr/lib/gnome-settings-daemon/gnome-settings-daemon                                                                                             
ian       2142  0.0  0.0  45068     4 ?        S    Dec10   0:00 /usr/lib/gvfs/gvfsd                                                                                                                              
ian       2146  0.0  0.0 192836    32 ?        Ss   Dec10   0:00 seahorse-daemon                                                                                                                                  
ian       2148  0.0  0.0  83824     4 ?        Ssl  Dec10   0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/ian/.gvfs                                                                                                  
ian       2151  0.0  0.0 205560  1276 ?        S    Dec10   0:03 /usr/lib/notify-osd/notify-osd                                                                                                                   
ian       2235  0.0  0.0 152476     4 ?        Ssl  Dec10   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=19                                                             
root      2254  0.0  0.0  59212    56 ?        S    Dec10   0:00 /usr/lib/policykit-1/polkitd                                                                                                                     
root      2257  0.0  0.0  51048    52 ?        S    Dec10   0:35 /usr/lib/devicekit-disks/devkit-disks-daemon                                                                                                     
root      2264  0.0  0.0  42180   140 ?        S    Dec10   0:09  \_ devkit-disks-daemon: polling /dev/sr0                                                                                                        
ian       2263  0.0  0.0 236096     4 ?        S    Dec10   0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=18                                     
ian       2272  0.0  0.0  49872     4 ?        S    Dec10   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.9 /org/gtk/gvfs/exec_spaw/0                                                                               
ian       2273  0.0  0.0 180736   916 ?        Ss   Dec10   0:12 gnome-screensaver                                                                                                                                
ian       2278  0.0  0.0 144456    48 ?        Sl   Dec10   0:01 /usr/lib/gvfs/gvfs-gdu-volume-monitor                                                                                                            
ian       2281  0.0  0.0  50456     4 ?        S    Dec10   0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
ian       2287  0.0  0.0 250844     4 ?        S    Dec10   0:00 /usr/lib/indicator-applet/indicator-applet-session --oaf-activate-iid=OAFIID:GNOME_FastUserSwitchApplet_Factory --oaf-ior-fd=19
ian       2289  0.0  0.0 249488     4 ?        S    Dec10   0:00 /usr/lib/indicator-applet/indicator-applet --oaf-activate-iid=OAFIID:GNOME_IndicatorApplet_Factory --oaf-ior-fd=26
ian       2311  0.0  0.0  51420     4 ?        S    Dec10   0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.9 /org/gtk/gvfs/exec_spaw/1
ian       2313  0.0  0.0  65420    36 ?        S    Dec10   0:01 /usr/lib/indicator-messages/indicator-messages-service
ian       2315  0.0  0.0  95376     4 ?        S    Dec10   0:00 /usr/lib/indicator-session/indicator-status-service
ian       2317  0.0  0.0  42164    36 ?        S    Dec10   0:00 /usr/lib/indicator-session/indicator-users-service
ian       2319  0.0  0.0  51088    20 ?        S    Dec10   0:00 /usr/lib/indicator-session/indicator-session-service
ian       2326  0.0  0.3 477132 13080 ?        Sl   Dec10   1:06 konsole
ian       2330  0.0  0.0  21604     4 pts/0    Ss   Dec10   0:00  \_ /bin/bash
root     15160  0.0  0.0  48568     4 pts/0    S    Dec13   0:00  |   \_ su -
root     15170  0.0  0.0  19176     4 pts/0    S    Dec13   0:00  |       \_ -su
root     20585  0.1  0.0  19132   732 pts/0    S+   01:52   0:01  |           \_ top
ian       2348  0.0  0.0  21584    48 pts/1    Ss+  Dec10   0:00  \_ /bin/bash
ian       2366  0.0  0.0  21604   824 pts/2    Ss   Dec10   0:00  \_ /bin/bash
ian      20612  0.0  0.0  15304  1188 pts/2    R+   02:05   0:00  |   \_ ps auxfh
ian       2384  0.0  0.0  21540     4 pts/3    Ss   Dec10   0:00  \_ /bin/bash
ian       2426  0.0  0.0 352380     4 ?        Sl   Dec10   0:00 /usr/lib/evolution/2.28/evolution-exchange-storage --oaf-activate-iid=OAFIID:GNOME_Evolution_Exchange_Connector_CalFactory:1.2 --oaf-ior-fd=24
ian       2430  0.0  0.0 447556     4 ?        Sl   Dec10   0:00 /usr/lib/evolution/evolution-data-server-2.28 --oaf-activate-iid=OAFIID:GNOME_Evolution_DataServer_CalFactory:1.2 --oaf-ior-fd=27
ian       2582  0.0  0.0 138292   644 ?        Ss   Dec10   0:00 kdeinit4: kdeinit4 Running...
ian       2585  0.0  0.0 146852  1484 ?        S    Dec10   0:00  \_ kdeinit4: klauncher [kdeinit] --fd=8
ian       6120  1.4  3.6 1270376 149392 ?      Sl   Dec13  20:01  \_ kdeinit4: konqueror [kdeinit] --silent
ian      14937  5.6 67.2 3662276 2730372 ?     D    Dec13  34:51  \_ kdeinit4: kio_file [kdeinit] file local:/tmp/ksocket-ian/klauncherMT2585.slave-socket local:/tmp/ksocket-ian/konquerora14904.slave-socket
ian      18256  0.0  0.0 149584   708 ?        S    Dec13   0:00  \_ kdeinit4: kio_file [kdeinit] file local:/tmp/ksocket-ian/klauncherMT2585.slave-socket local:/tmp/ksocket-ian/k3bf18220.slave-socket
ian       2587  0.0  0.0 583008  1660 ?        S    Dec10   0:28 kdeinit4: kded4 [kdeinit] e
ian       2592  0.0  0.0 698432   944 ?        Sl   Dec10   0:03 /usr/bin/knotify4
root      4190  0.0  0.0  23328     4 ?        Ss   Dec10   0:00 /bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
root      4191  0.0  0.0  26156     0 pts/0    S    Dec10   0:00 dbus-launch --autolaunch 9406996680bcbf6db99608b14af9820b --binary-syntax --close-stderr
103       6731  0.0  0.0  33992   720 ?        Ss   Dec10   0:01 hald --daemon=yes
root      6732  0.0  0.0  20056     4 ?        S    Dec10   0:00  \_ hald-runner
root      6787  0.0  0.0  22208   220 ?        S    Dec10   0:00      \_ hald-addon-input: Listening on /dev/input/event0 /dev/input/event1 /dev/input/event4
103       6789  0.0  0.0  26080     4 ?        S    Dec10   0:00      \_ hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
root      6796  0.0  0.0  22180   200 ?        S    Dec10   0:27      \_ hald-addon-storage: polling /dev/sr0 (every 2 sec)
root      6857  0.0  0.0  72112     4 ?        S    Dec10   0:00 /usr/bin/python /usr/lib/system-service/system-service-d
root     11390  0.0  0.0  40176     4 ?        S    Dec10   0:00 /usr/sbin/system-tools-backends
root     11392  0.0  0.0  58596     4 ?        S    Dec10   0:00 /usr/bin/perl /usr/share/system-tools-backends-2.0/scripts/SystemToolsBackends.pl -m Platform
ian      14347  1.1  1.5 628228 62720 ?        Sl   Dec12  19:53 /usr/lib/firefox-3.5.5/firefox
ian      12733  0.1  0.0 222380   480 ?        S    Dec13   1:25  \_ /usr/lib/nspluginwrapper/i386/linux/npviewer.bin --plugin /usr/lib/flashplugin-installer/libflashplayer.so --connection /org/wrapper/NSPlugin
ian       6204  0.0  0.0 275540  1368 ?        S    Dec13   0:00 kdeinit4: kwalletd [kdeinit]
ian       7500  0.0  0.0 276044  1364 ?        S    Dec13   0:00 kdeinit4: kglobalaccel [kdeinit]
proftpd   9952  0.0  0.0  73824   228 ?        SNs  Dec13   0:00 proftpd: (accepting connections)
ian      17724  0.0  0.0  34864     4 ?        S    Dec13   0:00 /usr/lib/gvfs/gvfsd-metadata
ian      20597  0.2  0.1 371836  6888 ?        S    01:56   0:01 kate


top - 02:10:27 up 3 days,  8:46,  1 user,  load average: 3.26, 3.26, 2.74
Tasks: 175 total,   2 running, 173 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.2%us,  1.0%sy,  0.0%ni,  0.3%id, 97.3%wa,  0.2%hi,  0.0%si,  0.0%st
Mem:   4060760k total,  4032604k used,    28156k free,      304k buffers
Swap:  4104504k total,  2050768k used,  2053736k free,    20012k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
14937 ian       20   0 3576m 3.2g    8 D    0 82.1  34:54.35 kio_file
 6120 ian       20   0 1240m 123m 3672 R    1  3.1  20:03.62 konqueror
 1481 root      20   0  677m  21m 1824 S    0  0.5  24:51.62 Xorg
 2227 ian       20   0  341m  10m 6928 S    0  0.3   7:32.37 compiz.real
 2326 ian       20   0  466m 9964 2412 S    1  0.2   1:09.19 konsole
14347 ian       20   0  613m 9292 2252 S    1  0.2  19:55.52 firefox
20597 ian       20   0  365m 8264  928 S    0  0.2   0:01.96 kate
 2231 ian       20   0  347m 7320 2284 S    0  0.2   1:08.74 gnome-panel
 2275 ian       20   0  207m 2364  940 S    0  0.1   0:33.48 gtk-window-deco
 2233 ian       20   0  557m 1976  468 S    0  0.0   4:35.40 nautilus
 2587 ian       20   0  569m 1952  756 S    0  0.0   0:28.11 kded4
 7500 ian       20   0  269m 1804  656 S    0  0.0   0:00.42 kglobalaccel
 6204 ian       20   0  269m 1760  652 S    0  0.0   0:00.65 kwalletd
 2592 ian       20   0  682m 1336  704 S    0  0.0   0:03.87 knotify4
 2134 ian       20   0  301m 1128  512 S    0  0.0   0:26.40 gnome-settings-
 2585 ian       20   0  143m 1068  196 S    0  0.0   0:00.84 klauncher
 2151 ian       20   0  200m 1020  460 S    0  0.0   0:03.43 notify-osd
 2244 ian       20   0  186m  876  484 S    0  0.0   0:00.52 polkit-gnome-au
 2273 ian       20   0  176m  860  432 S    0  0.0   0:12.95 gnome-screensav
12733 ian       20   0  217m  788  492 S    0  0.0   1:25.83 npviewer.bin
 2126 ian       20   0 46476  784  224 S    0  0.0   0:10.17 gconfd-2
20585 root      20   0 19132  740  432 R    0  0.0   0:01.49 top
 6731 haldaemo  20   0 33992  712  168 S    0  0.0   0:01.80 hald
18256 ian       20   0  146m  652    4 S    0  0.0   0:00.03 kio_file
 2582 ian       20   0  135m  632    4 S    0  0.0   0:00.51 kdeinit4
 2366 ian       20   0 21604  532    4 S    0  0.0   0:00.24 bash
 2252 ian       20   0  184m  512  248 S    0  0.0   0:01.57 gnome-power-man
 2239 ian       20   0  189m  472  232 S    0  0.0   0:06.28 update-notifier
14182 ian       20   0 47388  292  176 S    0  0.0   0:02.25 ssh
 1643 root      20   0 12636  240  156 S    0  0.0   0:00.15 mdadm
 9952 proftpd   30  10 73824  228  140 S    0  0.0   0:00.37 proftpd
 1047 root      20   0 18708  212  132 S    0  0.0   0:00.18 cron
 2113 ian       20   0 16436  196  116 S    0  0.0   0:01.28 gpg-agent

---

