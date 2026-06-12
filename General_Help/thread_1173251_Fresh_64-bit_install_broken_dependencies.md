---
title: "Fresh 64-bit install broken dependencies"
date: 2009-05-29
forum: General Help
---

### Post by flashmxboy on 2009-05-29
Hi

i recently did a fresh install of kubuntu 9.04 64-bit from live cd on my Acer Aspire 5920G laptop. Its the only OS on the computer since i deleted vista.(It felt good)
After the install everything worked except that i had to connect to a open wireless network to be able to connect to a WPA network. Therefore i decided to update the newly installed system. Then i got a error telling me that i had broken dependencies. Then i did a "sudo apt-get install -f" to fix it. This returned:
> Reading package lists... Done                                                   
Building dependency tree                                                        
Reading state information... Done                                               
Correcting dependencies... Done                                                 
The following extra packages will be installed:                                 
  libqt4-designer                                                               
The following packages will be upgraded:                                        
  libqt4-designer                                                               
1 upgraded, 0 newly installed, 0 to remove and 40 not upgraded.                 
2 not fully installed or removed.                                               
Need to get 0B/1795kB of archives.                                              
After this operation, 0B of additional disk space will be used.                 
Do you want to continue [Y/n]? y                                                
(Reading database ... 88757 files and directories currently installed.)         
Preparing to replace libqt4-designer 4.5.0-0ubuntu4 (using .../libqt4-designer_4.5.0-0ubuntu4.1_amd64.deb) ...                                                  
Unpacking replacement libqt4-designer ...                                       
lzma: Decoder error                                                             
dpkg-deb: subprocess <decompress> returned error exit status 1                  
dpkg: error processing /var/cache/apt/archives/libqt4-designer_4.5.0-0ubuntu4.1_amd64.deb (--unpack):                                                           
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/libQtDesigner.so.4.5.0')                                                                         
Errors were encountered while processing:                                       
 /var/cache/apt/archives/libqt4-designer_4.5.0-0ubuntu4.1_amd64.deb             
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any help here?

---

### Post by flashmxboy on 2009-05-30
anyone... i would realy like to get this working...

---

### Post by whoop on 2009-05-30
lzma: Decoder error. That could indicate that it didn't download correctly or was compressed incorrectly etc...
try reinstalling libqt4-designer

---

### Post by flashmxboy on 2009-05-30
Thank you! That did it:D

solved

---

