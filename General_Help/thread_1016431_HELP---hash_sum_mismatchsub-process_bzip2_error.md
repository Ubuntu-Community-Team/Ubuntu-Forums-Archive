---
title: "HELP---hash sum mismatch/sub-process bzip2 error"
date: 2008-12-19
forum: General Help
---

### Post by meetmeinfairview on 2008-12-19
I'm finally giving in and asking for help.  I'm new to the Linux operating system, but I'm not a novice in general.  I downloaded the Ubuntu Intrepid ISO, burnt the image, and installed it on an older desktop I had lying around my apartment.  The desktop to is an emachines, with the Intel Pentium 4 2.53 ghz processor.  I already successfully completed the workaround pertaining to the removal of the compiz/compiz-core packages.  The problem I'm having is... I can't seem to update/download ANYTHING.  I'm coming up with various errors and tried about everything.  

When using ```
sudo apt-get update
```

 i get...
```

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Some index files failed to download, they have been ignored, or old ones used instead. 
```

When trying to install or upgrade ANYTHING, it returns a HASH SUM MISMATCH.  I've done a clean install a few times, assuming I messed up some setting along the way trying to get this to work, and every time I have not been successful in updating.  My network connection is fine.  I have a PC with Vista, Apple with Leopard, and Xbox 360 sitting next to me and have no troubles.  I've tried about 10 different servers.  Also worth mentioning, when I go to the page containing the Packages.bz2 and Sources.bz2, the files have question marks next to them whereas the .gz file does not. I realize this has been an issue for a lot of people and I've attempted several of the workaround's presented in various other threads with no luck.  If I could get any help, it would be greatly appreciated.

---

### Post by taurus on 2008-12-19
Go into System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and try the Main Server.  Close the window and press the Reload button.  Now, if you want to run it from a terminal, you need to close synaptic first.

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by meetmeinfairview on 2008-12-19
Thank you for your reply, however, I have tried this multiple times.  I just tried it again for the sake of documentation.  After changing to Main server and reloading, Synaptic gives me the error posted above saying it could not download all repository indexes.  After the 

Also, something I found odd was when updating in the Update Manager... it would get to the ...intrepid/main Packages, and once it leaves it says 'hit.'  Then as the queue comes by and reaches this line, it flashes 'done' for a brief moment before going to 'failed'.  In the terminal it just remains on 'get' and doesn't move past that.

```

Hit http://archive.ubuntu.com intrepid Release.gpg
Ign http://archive.ubuntu.com intrepid/main Translation-en_US
Ign http://archive.ubuntu.com intrepid/restricted Translation-en_US
Ign http://archive.ubuntu.com intrepid/universe Translation-en_US
Hit http://archive.ubuntu.com intrepid-updates Release.gpg
Ign http://archive.ubuntu.com intrepid-updates/main Translation-en_US
Ign http://archive.ubuntu.com intrepid-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com intrepid-updates/universe Translation-en_US
Hit http://archive.ubuntu.com intrepid-security Release.gpg
Ign http://archive.ubuntu.com intrepid-security/main Translation-en_US
Ign http://archive.ubuntu.com intrepid-security/restricted Translation-en_US
Ign http://archive.ubuntu.com intrepid-security/universe Translation-en_US
Hit http://archive.ubuntu.com intrepid Release
Hit http://archive.ubuntu.com intrepid-updates Release
Hit http://archive.ubuntu.com intrepid-security Release
Get:1 http://archive.ubuntu.com intrepid/main Packages [1256kB]
Hit http://archive.ubuntu.com intrepid/restricted Packages                     
Hit http://archive.ubuntu.com intrepid/main Sources                            
Hit http://archive.ubuntu.com intrepid/restricted Sources                      
Get:2 http://archive.ubuntu.com intrepid/universe Packages [4542kB]            
Get:3 http://archive.ubuntu.com intrepid/universe Sources [1981kB]             
76% [2 Packages bzip2 2277376] [3 Sources 128755/1981kB 6%]         126kB/s 14s
bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://archive.ubuntu.com intrepid/universe Packages                       
  Sub-process bzip2 returned an error code (2)
Hit http://archive.ubuntu.com intrepid-updates/main Packages                   
Hit http://archive.ubuntu.com intrepid-updates/restricted Packages             
Hit http://archive.ubuntu.com intrepid-updates/main Sources                    
Hit http://archive.ubuntu.com intrepid-updates/restricted Sources              
Hit http://archive.ubuntu.com intrepid-updates/universe Packages               
Hit http://archive.ubuntu.com intrepid-updates/universe Sources                
Hit http://archive.ubuntu.com intrepid-security/main Packages                  
Hit http://archive.ubuntu.com intrepid-security/restricted Packages            
Hit http://archive.ubuntu.com intrepid-security/main Sources                   
Hit http://archive.ubuntu.com intrepid-security/restricted Sources             
Hit http://archive.ubuntu.com intrepid-security/universe Packages              
Hit http://archive.ubuntu.com intrepid-security/universe Sources               
99% [3 Sources bzip2 3407872]                                        127kB/s 0s
bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://archive.ubuntu.com intrepid/universe Sources                        
  Sub-process bzip2 returned an error code (2)
Fetched 7779kB in 1min3s (122kB/s)                                             
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.bz2  Sub-process bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

I'm fairly familiar with the Linux terminal by now so feel free to throw things at me to post their results.  I'd like to get this figured out, so I can get to the fun part!  Also, not mentioned above, this is a clean install on a formatted hardrive, **not dual booting**.  Will post the results of the apt-get upgrade once it completes.

---

### Post by meetmeinfairview on 2008-12-19
Results of apt-get upgrade...

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-headers-generic linux-image-generic linux-restricted-modules-generic
The following packages will be upgraded:
  alsa-utils bind9-host console-setup cups cups-common dnsutils evolution evolution-common
  evolution-data-server evolution-data-server-common evolution-exchange evolution-plugins gedit
  gedit-common gnome-games gnome-games-data gnome-panel-data gnome-power-manager gnome-terminal-data
  language-pack-en-base language-pack-gnome-en-base libbind9-40 libdns43 libglib2.0-0 libglib2.0-data
  libisc44 libisccc40 libisccfg40 liblwres40 libsmbclient libsnmp15 linux-headers-2.6.27-7
  linux-image-2.6.27-7-generic openoffice.org-base-core openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-gnome openoffice.org-gtk openoffice.org-impress
  openoffice.org-math openoffice.org-style-human openoffice.org-writer python-uno rhythmbox samba-common
  smbclient totem totem-common totem-gstreamer totem-mozilla totem-plugins update-manager
  update-manager-core xulrunner-1.9 xulrunner-1.9-gnome-support
57 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 153MB/159MB of archives.
After this operation, 315kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com intrepid-updates/main language-pack-en-base 1:8.10+20081107 [491kB]
Get:2 http://archive.ubuntu.com intrepid-updates/main language-pack-gnome-en-base 1:8.10+20081107 [240kB]
Get:3 http://archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]    
Get:4 http://archive.ubuntu.com intrepid-updates/main openoffice.org-calc 1:2.4.1-11ubuntu2.1 [4113kB]     
Get:5 http://archive.ubuntu.com intrepid-updates/main openoffice.org-style-human 1:2.4.1-11ubuntu2.1 [3928kB]
Get:6 http://archive.ubuntu.com intrepid-updates/main openoffice.org-common 1:2.4.1-11ubuntu2.1 [9700kB]   
Get:7 http://archive.ubuntu.com intrepid-updates/main libglib2.0-0 2.18.2-0ubuntu2 [771kB]                 
Get:8 http://archive.ubuntu.com intrepid-updates/main openoffice.org-writer 1:2.4.1-11ubuntu2.1 [5094kB]   
Get:9 http://archive.ubuntu.com intrepid-updates/main openoffice.org-core 1:2.4.1-11ubuntu2.1 [26.1MB]     
Get:10 http://archive.ubuntu.com intrepid-updates/main console-setup 1.25ubuntu4 [472kB]                   
Get:11 http://archive.ubuntu.com intrepid-updates/main libdns43 1:9.5.0.dfsg.P2-1ubuntu3 [536kB]           
Get:12 http://archive.ubuntu.com intrepid-updates/main update-manager 1:0.93.34 [787kB]                    
Get:13 http://archive.ubuntu.com intrepid-updates/main alsa-utils 1.0.17-0ubuntu3 [1056kB]                 
Get:14 http://archive.ubuntu.com intrepid-updates/main cups-common 1.3.9-2ubuntu4 [1162kB]                 
Get:15 http://archive.ubuntu.com intrepid-updates/main cups 1.3.9-2ubuntu4 [2138kB]                        
Get:16 http://archive.ubuntu.com intrepid-updates/main evolution-data-server 2.24.2-0ubuntu1 [459kB]       
Get:17 http://archive.ubuntu.com intrepid-updates/main evolution 2.24.2-0ubuntu1 [2743kB]                  
Get:18 http://archive.ubuntu.com intrepid-updates/main evolution-common 2.24.2-0ubuntu1 [16.7MB]           
Get:19 http://archive.ubuntu.com intrepid-updates/main gedit-common 2.24.2-0ubuntu1 [1501kB]               
Get:20 http://archive.ubuntu.com intrepid-updates/main gedit 2.24.2-0ubuntu1 [767kB]                       
Get:21 http://archive.ubuntu.com intrepid-updates/main gnome-games-data 1:2.24.1.1-0ubuntu1 [13.9MB]       
Get:22 http://archive.ubuntu.com intrepid-updates/main gnome-games 1:2.24.1.1-0ubuntu1 [1099kB]            
Get:23 http://archive.ubuntu.com intrepid-updates/main gnome-panel-data 1:2.24.1-0ubuntu2.1 [1393kB]       
Get:24 http://archive.ubuntu.com intrepid-updates/main gnome-power-manager 2.24.0-0ubuntu8.1 [2181kB]      
Get:25 http://archive.ubuntu.com intrepid-updates/main gnome-terminal-data 2.24.1.1-0ubuntu1 [1067kB]      
Get:26 http://archive.ubuntu.com intrepid-updates/main libsmbclient 2:3.2.3-1ubuntu3.3 [1218kB]            
Get:27 http://archive.ubuntu.com intrepid-updates/main libsnmp15 5.4.1~dfsg-7.1ubuntu6.1 [1119kB]          
Get:28 http://archive.ubuntu.com intrepid-updates/main linux-headers-2.6.27-7 2.6.27-7.16 [5771kB]         
Get:29 http://archive.ubuntu.com intrepid-updates/main rhythmbox 0.11.6svn20081008-0ubuntu4.2 [3396kB]     
Get:30 http://archive.ubuntu.com intrepid-updates/main smbclient 2:3.2.3-1ubuntu3.3 [6403kB]               
Get:31 http://archive.ubuntu.com intrepid-updates/main samba-common 2:3.2.3-1ubuntu3.3 [3459kB]            
Get:32 http://archive.ubuntu.com intrepid-updates/main totem-common 2.24.3-0ubuntu1 [1675kB]               
Get:33 http://archive.ubuntu.com intrepid-updates/main totem-gstreamer 2.24.3-0ubuntu1 [880kB]             
Get:34 http://archive.ubuntu.com intrepid-updates/main xulrunner-1.9 1.9.0.5+nobinonly-0ubuntu0.8.10.1 [7536kB]
Fetched 152MB in 20min36s (123kB/s)                                                                        
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en-base/language-pack-en-base_8.10+20081107_all.deb  Hash Sum mismatch
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.27-7-generic_2.6.27-7.16_i386.deb  Hash Sum mismatch
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-calc_2.4.1-11ubuntu2.1_i386.deb  Hash Sum mismatch
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-style-human_2.4.1-11ubuntu2.1_all.deb  Hash Sum mismatch
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-common_2.4.1-11ubuntu2.1_all.deb  Hash Sum mismatch
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-writer_2.4.1-11ubuntu2.1_i386.deb  Hash Sum mismatch
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_2.4.1-11ubuntu2.1_i386.deb  Hash Sum mismatch
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/c/console-setup/console-setup_1.25ubuntu4_all.deb  Hash Sum mismatch
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/libdns43_9.5.0.dfsg.P2-1ubuntu3_i386.deb  Hash Sum mismatch
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager_0.93.34_all.deb  Hash Sum mismatch
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/a/alsa-utils/alsa-utils_1.0.17-0ubuntu3_i386.deb  Hash Sum mismatch
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-common_1.3.9-2ubuntu4_all.deb  Hash Sum mismatch
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/c/cups/cups_1.3.9-2ubuntu4_i386.deb  Hash Sum mismatch
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/evolution-data-server_2.24.2-0ubuntu1_i386.deb  Hash Sum mismatch
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution_2.24.2-0ubuntu1_i386.deb  Hash Sum mismatch
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-common_2.24.2-0ubuntu1_all.deb  Hash Sum mismatch
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/g/gedit/gedit_2.24.2-0ubuntu1_i386.deb  Hash Sum mismatch
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnome-games-data_2.24.1.1-0ubuntu1_all.deb  Hash Sum mismatch
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnome-games_2.24.1.1-0ubuntu1_i386.deb  Hash Sum mismatch
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-terminal/gnome-terminal-data_2.24.1.1-0ubuntu1_all.deb  Hash Sum mismatch
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.2.3-1ubuntu3.3_i386.deb  Hash Sum mismatch
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/n/net-snmp/libsnmp15_5.4.1~dfsg-7.1ubuntu6.1_i386.deb  Hash Sum mismatch
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.27-7_2.6.27-7.16_all.deb  Hash Sum mismatch
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/r/rhythmbox/rhythmbox_0.11.6svn20081008-0ubuntu4.2_i386.deb  Hash Sum mismatch
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.2.3-1ubuntu3.3_i386.deb  Hash Sum mismatch
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.2.3-1ubuntu3.3_i386.deb  Hash Sum mismatch
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/t/totem/totem-common_2.24.3-0ubuntu1_all.deb  Hash Sum mismatch
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/t/totem/totem-gstreamer_2.24.3-0ubuntu1_i386.deb  Hash Sum mismatch
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9_1.9.0.5+nobinonly-0ubuntu0.8.10.1_i386.deb  Hash Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

---

### Post by meetmeinfairview on 2008-12-20
Does anybody have any recommendations?  I just completed a reinstall and directly went to update and had the issues again.  I removed all sources except those of main and restricted and managed avoid the bzip2 errors from the first part.  Then the downloads failed with the hash sum mismatch.  Any advice would be appreciated.  I'm starting to become frustrated, as I have spent almost 48 hours straight trying to get this to work.  Thanks!

---

### Post by ben2talk on 2009-10-26
> **meetmeinfairview said:**
> I have spent almost 48 hours straight trying to get this to work.  Thanks!

I'll be honest with you - sometimes it just sucks. I get paranoid about my connection at times. I have a procedure which cleans things up to get rid of that 'you didn't update for a few days' rubbish...

sudo apt-get clean
gksu nautilus /var/lib/apt
gksu gnome-terminal

Now, move your 'lists' folder to 'lists.old' (rename it)(in nautilus or terminal, up to you 'mv lists lists.old - I put the nautilus here, because I don't know how to remove lists.old directory the next time I do it - so I use nautilus)

terminal - 'sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update

(actually, I recommend you edit - gedit .bashrc - and enter an alias line : alias update='sudo aptitude update && sudo aptitude safe-upgrade' - or 'sudo apt-get update' if you don't want it to ask you to go ahead with the upgrade... then add shortcut Super+U to launch the updater)

so you do sudo aptitude safe-upgrade
autoclean

Now try opening your software updates and see if it tells you you didn't update for a few days.

Actually, it doesn't usually cause problems - I noticed a few times that Chromium isn't updating too well, and gets behind Chrome. I do a clean up and it generally works. I hope this won't repeat in Karmic...  It really does, basically, suck.

Just be very careful - whenever it says it can't complete, and offers 'partial upgrade' I'd say ALWAYS refuse. Best stay behind than mess it up.

---

