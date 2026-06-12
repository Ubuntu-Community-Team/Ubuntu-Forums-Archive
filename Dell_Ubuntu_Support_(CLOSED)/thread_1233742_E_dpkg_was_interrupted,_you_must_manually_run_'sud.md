---
title: "E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct"
date: 2009-08-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dralex on 2009-08-07
Hello,

I am new kid using Linux and need help to resolve the following problem after issue the command: sudo apt-gt update

Thanks.


alex@judah-linux:~$ sudo apt-get update
[sudo] password for alex: 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg             
Ign [http://www.openprinting.org](http://www.openprinting.org) lsb3.2 Release.gpg           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Translation-en_SG
Ign [http://www.openprinting.org](http://www.openprinting.org) lsb3.2/postscript-hp Translation-en_SG
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Translation-en_SG
Get:1 [http://www.openprinting.org](http://www.openprinting.org) lsb3.2 Release [31.8kB]
Ign [http://www.openprinting.org](http://www.openprinting.org) lsb3.2/postscript-hp Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Translation-en_SG
Hit [http://www.openprinting.org](http://www.openprinting.org) lsb3.2/postscript-hp Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Translation-en_SG
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Translation-en_SG
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Translation-en_SG
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Translation-en_SG
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Translation-en_SG
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Translation-en_SG
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Translation-en_SG
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Translation-en_SG
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Translation-en_SG
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release [49.6kB]                
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security Release [49.6kB]               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Sources                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Sources                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Packages                       
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Packages [131kB]           
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Packages [2366B]     
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Sources [522B]       
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Sources [40.1kB]           
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Sources [1349B]     
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Sources [11.7kB]      
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Packages [41.3kB]     
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Packages [4118B]    
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Packages [64.5kB]        
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Packages [2366B]   
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Sources [522B]     
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Sources [18.8kB]         
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Sources [14B]      
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Sources [4712B]      
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Packages [21.7kB]    
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Packages [14B]     
[B][COLOR=Red]F[/COLOR][COLOR=Red]etched 445kB in 18s (23.8kB/s)                                                
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
alex@judah-linux:~$ [/COLOR][/B]

---

### Post by aysiu on 2009-08-07
So at *alex@judah-linux:~$* paste in the command ```
sudo dpkg --configure -a
```

---

