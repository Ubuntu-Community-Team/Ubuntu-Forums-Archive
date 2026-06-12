---
title: "Intermittent System Slowdown..??"
date: 2006-12-28
forum: Desktop Environments
---

### Post by richardq on 2006-12-28
I've been having strange problems for the last couple of months. I'm running Edgy on a P4-3Ghz with 1GB ram. I'm running plain Ubuntu with Beryl installed and running.

Here's a quick description of the problem:

Every 3rd or 4th time I boot up the machine, it seems to run very slow. I can tell it's going to run slow right after I log in from the GDM login screen. The ubuntu splash screen takes several seconds to show up, the icons appear slowly on the ubuntu splash panel and then when the desktop appears, the gnome panel fills up with icons very slowly. From that point onward the typical symptoms are:
- all apps take several seconds to launch (including small ones like terminal, calculator, Gedit etc.)
- File->Open dialogs appear immediately, but take several seconds to populate with files and folders (typical on all apps)
- Once apps are open, they seems to run normally, although I notice Firefox loading my initial home page slowly (my gmail)
- Some operations in apps like Inkscape or Gimp run much more slowly
- Even selecting the shutdown icon takes several seconds to show my shutdown choices

The strange thing is that other times the system runs very fast: apps appearing in 1 second, file->open dialogs populating immediately etc..

It seems like a filesystem thing to me, but I can't spot anything suspicious in the top command output or in the system monitor. Is there some way to dynamically monitor disk usage to try and nail down the problem? I'm pretty much a noob when it comes to digging deep into the inards of Linux but I'm not scared of the command line. It seems like maybe something is running in the background but it doesn't show up my system monitor. The level is a little higher at 9% (when it's usually 4-5 when running quickly) but jumps to 100% for almost any operation, like opening a web page, copying and pasting, etc.

I've attached a "top -n 1" output in case that helps. I'm also wondering why I have all the 'k' apps appearing in the top output. I haven't installed the kubuntu package since upgrading to edgy. Are all those things supposed to be there? I know they're not taking up much cpu percentage, but it seems strange that they're all there.


```
Tasks:  83 total,   2 running,  80 sleeping,   0 stopped,   1 zombie
Cpu(s): 36.1%us,  0.7%sy,  0.7%ni, 61.3%id,  1.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1026952k total,   496604k used,   530348k free,    19708k buffers
Swap:  2931820k total,        0k used,  2931820k free,   211676k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                        
 6502 richard   16   0  2156  992  748 R 13.5  0.1   0:00.16 top                                            
 4393 root      15   0  410m  73m 7624 S  6.7  7.3   2:27.44 Xorg                                           
 5158 richard   15   0  205m  62m  22m R  1.7  6.3   2:22.78 firefox-bin                                    
    1 root      16   0  1556  552  464 S  0.0  0.1   0:01.41 init                                           
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0                                    
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                     
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.24 events/0                                       
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper                                        
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread                                        
    8 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kblockd/0                                      
    9 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                         
   10 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                   
  117 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod                                        
  153 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                        
  154 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                        
  155 root      16   0     0    0    0 S  0.0  0.0   0:00.00 kswapd0                                        
  156 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                          
 1796 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 ata/0                                          
 1799 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0                                      
 1800 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_1                                      
 1874 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                          
 1890 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt                                       
 1919 root      15   0     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_0                                    
 2117 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kjournald                                      
 2217 root      15   0  1524  540  464 S  0.0  0.1   0:00.01 logd                                           
 2400 root      12  -4  2528 1056  364 S  0.0  0.1   0:01.76 udevd                                          
 3083 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 shpchpd                                        
 3177 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 hda_codec                                      
 3234 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused                                      
 3715 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 kjournald                                      
 3815 root      15   0  2684  884  656 S  0.0  0.1   0:00.00 pppd                                           
 4122 root      16   0  1516  508  436 S  0.0  0.0   0:00.00 getty                                          
 4123 root      16   0  1516  504  436 S  0.0  0.0   0:00.00 getty                                          
 4124 root      16   0  1520  512  436 S  0.0  0.0   0:00.00 getty                                          
 4318 root      16   0  2112 1132  620 S  0.0  0.1   0:00.14 acpid                                          
 4383 root      15   0 11784 1780 1288 S  0.0  0.2   0:00.02 gdm                                            
 4390 root      15   0 12140 2676 2120 S  0.0  0.3   0:00.09 gdm                                            
 4430 cupsys    16   0  4584 2084 1444 S  0.0  0.2   0:14.89 cupsd                                          
 4485 messageb  15   0  2088  848  628 S  0.0  0.1   0:00.24 dbus-daemon                                    
 4506 haldaemo  15   0  7192 5764 1660 S  0.0  0.6   0:29.87 hald                                           
 4507 root      16   0  2828 1032  876 S  0.0  0.1   0:00.05 hald-runner                                    
 4513 haldaemo  17   0  1932  820  700 S  0.0  0.1   0:00.00 hald-addon-acpi                                
 4540 haldaemo  15   0  1936  820  696 S  0.0  0.1   0:00.10 hald-addon-keyb                                
 4559 haldaemo  16   0  1936  832  708 S  0.0  0.1   0:00.35 hald-addon-stor                                
 4579 root      17   0 13532  10m 1272 S  0.0  1.1   0:00.38 perl                                           
 4622 Debian-e  16   0  5292  980  696 S  0.0  0.1   0:00.00 exim4                                          
 4657 root      23   0  3452  800  656 S  0.0  0.1   0:00.00 vsftpd                                         
 4715 root      16   0  2100  856  676 S  0.0  0.1   0:00.01 cron                                           
 4816 richard   15   0 20944  10m 8072 S  0.0  1.0   0:05.30 gnome-session                                  
 4871 richard   15   0  4396  688  492 S  0.0  0.1   0:00.00 ssh-agent                                      
 4872 richard   15   0  4400  692  492 S  0.0  0.1   0:00.00 ssh-agent                                      
 4875 richard   15   0  2452  628  504 S  0.0  0.1   0:00.00 dbus-launch                                    
 4876 richard   17   0  2088  952  744 S  0.0  0.1   0:00.06 dbus-daemon                                    
 4878 richard   16   0  7116 4712 1912 S  0.0  0.5   0:10.73 gconfd-2                                       
richard@ubuntu:~$ 
```

---

### Post by Nordicnurse on 2007-01-01
I've noticed same problem myself. Gnome seems to slow down almost to freeze, mouse and keyboard respondingvery slowly. Noob as I am only thing that popped up to me was program getty (showing up multiple times), which I was searching the forums for as I bumbed to your post. Must keep searching. Luck to ya.

---

### Post by ffi on 2007-01-01
I get slowdowns with the flash 9 beta, do you have it installed? The latest opera fixes it but I still have problems with FF.

---

### Post by finferflu on 2007-01-01
I had similar problems, apps taking forever to start up, and that was unacceptable for my 2.6GHz machine. So I switched to Kubuntu (sudo aptitude install kubuntu-desktop), which seems to be quite faster. If you want to get *very* fast, I suggest you IceWM (sudo aptitude install icewm), don't get discouraged by the crappy first looking, you can easily make it nice ([see here]("http://ubuntuforums.org/showthread.php?t=263710&page=18")).
To speed up Firefox I suggest not to install too many add-ons, since they can get very resource expensive.

Good luck!

---

