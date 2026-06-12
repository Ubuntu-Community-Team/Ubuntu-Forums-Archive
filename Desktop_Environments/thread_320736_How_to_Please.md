---
title: "How to Please"
date: 2006-12-17
forum: Desktop Environments
---

### Post by wireddad on 2006-12-17
I am not completely dumb but please point me to a gDesklet how to.  I have looked at the web site and search here and did not find anything.  Thanks.  ](*,)

---

### Post by aysiu on 2006-12-17
Assuming you have **[extra repositories enabled](http://www.psychocats.net/ubuntu/sources)**, just paste these commands into the terminal: ```
sudo aptitude update
sudo aptitude install gdesklets gdesklets-data
gdesklet &
```

---

### Post by wireddad on 2006-12-17
> **aysiu said:**
> Assuming you have **[extra repositories enabled]("http://www.psychocats.net/ubuntu/sources")**, just paste these commands into the terminal: ```
sudo aptitude update
sudo aptitude install gdesklets gdesklets-data
gdesklet &
```

Does this mean I do not have "extra repositories enabled?"

wireddad@pavilion:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Ign file: apt-build Release.gpg
Ign file: apt-build/main Translation-en_US                                      
Get:1 file: apt-build Release [89B]                                             
Ign file: apt-build/main Packages                                               
Ign [http://dl.google.com](http://dl.google.com) stable Release.gpg                                     
Get:2 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg [189B]                       
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_US                     
Ign [http://dl.google.com](http://dl.google.com) stable/non-free Translation-en_US                      
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release                                    
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages                              
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US                    
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US       
Hit [http://dl.google.com](http://dl.google.com) stable Release                                         
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy Release.gpg                                    
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy/main Translation-en_US                         
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US             
Hit [http://dl.google.com](http://dl.google.com) stable/non-free Packages                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US     
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [191B]   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US 
Get:7 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]         
Ign [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy Release                                        
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Translation-en_US      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release                                   
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg [191B]                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Translation-en_US          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release                           
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy/main Packages                                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Translation-en_US        
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]                        
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release                             
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy/main Packages                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
Fetched 98B in 1s (82B/s)
Reading package lists... Done
wireddad@pavilion:~$ sudo aptitude install gdesklets gdesklets-data
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
wireddad@pavilion:~$ gdesklet &
[1] 6446
wireddad@pavilion:~$ bash: gdesklet: command not found

---

### Post by aysiu on 2006-12-17
That's weird. You *appear* to have a lot of extra repositories enabled, but no gDesklets available?

I suppose you could always download the individual .deb files and then just double-click them (they're at the way bottom of these links):
[http://packages.ubuntu.com/edgy/gnome/gdesklets](http://packages.ubuntu.com/edgy/gnome/gdesklets)
[http://packages.ubuntu.com/edgy/x11/gdesklets-data](http://packages.ubuntu.com/edgy/x11/gdesklets-data)

---

### Post by reiatzu on 2006-12-17
Read before you write.
'wireddad@pavilion:~$ bash: gdesklet: command not found'
The command is not gdesklet but gdesklets.

---

### Post by wireddad on 2006-12-17
Ahh.  Will do.

---

### Post by aysiu on 2006-12-17
> **reiatzu said:**
> Read before you write.
'wireddad@pavilion:~$ bash: gdesklet: command not found'
The command is not gdesklet but gdesklets.
You're right. A typo on my part. 

Now that I look at the output, wireddad probably already has gDesklets installed and just needs to run the right command.

Thanks for pointing that out.

---

### Post by wireddad on 2006-12-17
> **aysiu said:**
> You're right. A typo on my part. 

Now that I look at the output, wireddad probably already has gDesklets installed and just needs to run the right command.

Thanks for pointing that out.

Thanks.  I did have the program install.  Sorry.  Thought at first you were telling me to download a how to/help file or something.
I just need to know how to use it.

---

### Post by reiatzu on 2006-12-17
[Ubuntu Gdesklets mini howto.]("http://rimron.co.uk/weblog/2005/05/07/ubuntu-gdesklet-mini-howto/")

---

### Post by wireddad on 2006-12-17
Awesome.  Thanks.

---

