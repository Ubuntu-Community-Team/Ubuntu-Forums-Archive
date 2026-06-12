---
title: "/home is full cant login through kde4"
date: 2009-04-11
forum: General Help
---

### Post by souravmohanty on 2009-04-11
Hi,

I have a following problem in my office on kubuntu 8.10 m/c, 
/home  directory is 100% full , in that dev user having .local directory is using about 27GB.

ss@dev-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              14G  3.9G  9.2G  30% /
tmpfs                 499M     0  499M   0% /lib/init/rw
varrun                499M  132K  499M   1% /var/run
varlock               499M     0  499M   0% /var/lock
udev                  499M  2.7M  497M   1% /dev
tmpfs                 499M     0  499M   0% /dev/shm
lrm                   499M  2.0M  497M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sda6              28G   27G     0 100% /home

ss@dev-desktop:/home$ sudo du -h --max-depth 1                                      
8.0K    ./ftp                                                                      
25G     ./dev
2.2G    ./shekhar-sir
16K     ./lost+found
27G     .

ss@dev-desktop:/home/dev$ sudo du -h --max-depth 1 
16K     ./.mcop                                   
196K    ./.gconf                                  
8.0K    ./.fonts                                  
4.0K    ./c.shekhar                               
8.0K    ./.update-manager-core                    
4.0K    ./Parser                                  
12K     ./.gnome                                  
36K     ./.filezilla                              
8.0K    ./.gnome2_private                         
8.0K    ./.ssh                                    
8.0K    ./.smplayer                               
43M     ./.kde                                    
21G     ./.local                                  
588K    ./.gstreamer-0.10                         
8.0K    ./.cache                                  
599M    ./desk_bak_12Dec08                        
25M     ./.opera                                  
18M     ./.marble                                 
4.0K    ./share                                   
119M    ./.mozilla                                
957M    ./.cxgames                                
150M    ./OOO300_m9_native_packed-1_en-US.9358    
36K     ./Modules                                 
3.8M    ./.cxoffice                               
32K     ./.gnupg                                  
8.0K    ./.synaptic                               
4.0K    ./Objects                                 
4.0K    ./.aptitude                               
44K     ./.xine                                   
40K     ./.subversion                             
26M     ./.thumbnails                             
16K     ./prog                                    
20K     ./.mplayer                                
56K     ./.gnome2                                 
168K    ./phono_test                              
64K     ./.freqtweak                              
554M    ./Desktop                                 
8.0K    ./.qchat                                  
4.0K    ./.gnome-desktop                          
12K     ./.qt                                     
72K     ./output                                  
420K    ./usplash                                 
720K    ./.adobe                                  
112K    ./.designer                               
20M     ./Harshad                                 
19M     ./.wine                                   
112K    ./.config                                 
12K     ./enosh                                   
8.0K    ./.hplip                                  
12K     ./.dbus                                   
1.8M    ./Documents                               
2.8M    ./.openoffice.org                         
140K    ./.xchat2                                 
4.0K    ./.gconfd                                 
303M    ./.strigi                                 
2.5M    ./.evolution                              
20K     ./.cream                                  
4.0K    ./.pulse                                  
1020K   ./.macromedia                             
640K    ./.gimp-2.4                               
9.1M    ./26Dec                                   
956K    ./.loki                                   
3.1M    ./.openoffice.org2                        
84K     ./.fontconfig                             
4.0K    ./dwhelper             
                   
25G     .        


Problem is that how this .local directory is getting full about 21GB or so.

I checked with inode problem but it was using only 10% of the total quota.

So temporary to solve the problem i deleted share directory under the .local folder.


Regards,
Sourav Mohanty

:lolflag:

---

### Post by souravmohanty on 2009-04-11
Hi,

I have a following problem in my office on kubuntu 8.10 m/c, 
/home  directory is 100% full , in that dev user having .local directory is using about 27GB.

ss@dev-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              14G  3.9G  9.2G  30% /
tmpfs                 499M     0  499M   0% /lib/init/rw
varrun                499M  132K  499M   1% /var/run
varlock               499M     0  499M   0% /var/lock
udev                  499M  2.7M  497M   1% /dev
tmpfs                 499M     0  499M   0% /dev/shm
lrm                   499M  2.0M  497M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sda6              28G   27G     0 100% /home

ss@dev-desktop:/home$ sudo du -h --max-depth 1                                      
8.0K    ./ftp                                                                      
25G     ./dev
2.2G    ./shekhar-sir
16K     ./lost+found
27G     .

ss@dev-desktop:/home/dev$ sudo du -h --max-depth 1 
16K     ./.mcop                                   
196K    ./.gconf                                  
8.0K    ./.fonts                                  
4.0K    ./c.shekhar                               
8.0K    ./.update-manager-core                    
4.0K    ./Parser                                  
12K     ./.gnome                                  
36K     ./.filezilla                              
8.0K    ./.gnome2_private                         
8.0K    ./.ssh                                    
8.0K    ./.smplayer                               
43M     ./.kde                                    
21G     ./.local                                  
588K    ./.gstreamer-0.10                         
8.0K    ./.cache                                  
599M    ./desk_bak_12Dec08                        
25M     ./.opera                                  
18M     ./.marble                                 
4.0K    ./share                                   
119M    ./.mozilla                                
957M    ./.cxgames                                
150M    ./OOO300_m9_native_packed-1_en-US.9358    
36K     ./Modules                                 
3.8M    ./.cxoffice                               
32K     ./.gnupg                                  
8.0K    ./.synaptic                               
4.0K    ./Objects                                 
4.0K    ./.aptitude                               
44K     ./.xine                                   
40K     ./.subversion                             
26M     ./.thumbnails                             
16K     ./prog                                    
20K     ./.mplayer                                
56K     ./.gnome2                                 
168K    ./phono_test                              
64K     ./.freqtweak                              
554M    ./Desktop                                 
8.0K    ./.qchat                                  
4.0K    ./.gnome-desktop                          
12K     ./.qt                                     
72K     ./output                                  
420K    ./usplash                                 
720K    ./.adobe                                  
112K    ./.designer                               
20M     ./Harshad                                 
19M     ./.wine                                   
112K    ./.config                                 
12K     ./enosh                                   
8.0K    ./.hplip                                  
12K     ./.dbus                                   
1.8M    ./Documents                               
2.8M    ./.openoffice.org                         
140K    ./.xchat2                                 
4.0K    ./.gconfd                                 
303M    ./.strigi                                 
2.5M    ./.evolution                              
20K     ./.cream                                  
4.0K    ./.pulse                                  
1020K   ./.macromedia                             
640K    ./.gimp-2.4                               
9.1M    ./26Dec                                   
956K    ./.loki                                   
3.1M    ./.openoffice.org2                        
84K     ./.fontconfig                             
4.0K    ./dwhelper             
                   
25G     .        


Problem is that how this .local directory is getting full about 21GB or so.

I checked with inode problem but it was using only 10% of the total quota.

So temporary to solve the problem i deleted share directory under the .local folder.

Pl help

Regards,
Sourav Mohanty

:lolflag:

---

### Post by blazemore on 2009-04-11
More info here:
[http://ubuntuforums.org/showthread.php?t=1122417](http://ubuntuforums.org/showthread.php?t=1122417)

---

### Post by blazemore on 2009-04-11
Someone else had the same problem here:
[http://ubuntuforums.org/showthread.php?t=1122419](http://ubuntuforums.org/showthread.php?t=1122419)

---

### Post by _Purple_ on 2009-04-11
> **blazemore said:**
> More info here:
[http://ubuntuforums.org/showthread.php?t=1122417](http://ubuntuforums.org/showthread.php?t=1122417)

Duplicate post.

---

