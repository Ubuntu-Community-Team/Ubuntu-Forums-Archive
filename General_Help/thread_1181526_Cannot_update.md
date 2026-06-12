---
title: "Cannot update"
date: 2009-06-08
forum: General Help
---

### Post by FlyOutlaw on 2009-06-08
I get the little light bulb on the panel bar at the top of the screen.  I click on the light bulb to update my OS (Ubuntu 9.04 Jaunty Jackalope April 2009).  It opens a little box that ask for root password, I type in the password that I use to login with. The box just disappears and nothing else happens. This window does not try to do anything, the window just goes away like you closed a program. 

The password works Synaptic Package Manager & all commands in terminal. I have tried several things that I have found here on the forums for similar problems but none of them help. And now one of the tries has screwed up something else. But we shall let that go for now, it is still up and running and I am on the internet.  


Also I seem to be having a similar problem as some other users with the drop down menu for the (System Tools) Root Terminal when the box for the password drops down, put in the password and it tries to do something but nothing happens.


If there is anything else you need to know about this problem let me know. 

And thanks 

Nolan;)

---

### Post by _Purple_ on 2009-06-08
What is the output if you run in terminal
```
sudo apt-get update
```

---

### Post by FlyOutlaw on 2009-06-08
I ran the (sudo apt-get update) as you suggested. This is what I received nolan@Compaq:~$ sudo apt-get update
[sudo] password for nolan: 
Building old list of packages... [done]
Building old list of available updates... [done]
Building old list of watched packages... [done]
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Beta i386 (20090324) jaunty Release.gpg
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Beta i386 (20090324) jaunty/main Translation-en_US
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Beta i386 (20090324) jaunty/restricted Translation-en_US
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Beta i386 (20090324) jaunty Release
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Beta i386 (20090324) jaunty/main Packages
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Beta i386 (20090324) jaunty/restricted Packages
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Beta i386 (20090324) jaunty/main Packages
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Beta i386 (20090324) jaunty/restricted Packages
Err cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Beta i386 (20090324) jaunty/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Beta i386 (20090324) jaunty/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Get:1 [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg [189B]                   
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US              
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg [189B]                      
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg [189B]  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US          
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg [189B]                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US                 
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US           
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg [189B]           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US   
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Translation-en_US
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed/restricted Translation-en_US  
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Sources                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports Release                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed Release                       
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed Release                       
  
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Sources
Fetched 1323B in 1s (875B/s)
Building new list of packages... [done]
Building new list of available updates... [done]
Building new list of watched packages... [done]
Building list of outdated packages... [done]

No new updates.
No new or removed packages.
No news in watched packages.
No outdated packages.
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Beta i386 (20090324)/dists/jaunty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Beta i386 (20090324)/dists/jaunty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-proposed/Release](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-proposed/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

---

### Post by _Purple_ on 2009-06-08
Go to System > Administration > Software sources and remove CD from sources and then run sudo apt-get update again.

---

### Post by FlyOutlaw on 2009-06-08
nolan@Compaq:~$ sudo apt-get update
[sudo] password for nolan: 
Building old list of packages... [done]
Building old list of available updates... [done]
Building old list of watched packages... [done]
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports Release.gpg        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Translation-en_US 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed Release.gpg                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed/restricted Translation-en_US  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release                                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed/main Translation-en_US        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                                
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports Release                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed Release                       
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed/main Sources
Building new list of packages... [done]
Building new list of available updates... [done]
Building new list of watched packages... [done]
Building list of outdated packages... [done]

No new updates.
No new or removed packages.
No news in watched packages.
No outdated packages.
Reading package lists... Done
nolan@Compaq:~$

---

### Post by _Purple_ on 2009-06-08
Update is working fine now and the errors are gone.

---

