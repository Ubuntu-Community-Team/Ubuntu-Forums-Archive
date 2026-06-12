---
title: "Cant get Mint to update"
date: 2009-05-24
forum: General Help
---

### Post by thebrandon on 2009-05-24
For some time now my update manager says there are updates available but then when I open it there is nothing to update.  I tried to update from the command line and got this :

brandon@brandon-desktop ~ $ sudo apt-get update
[sudo] password for brandon: 
Ign [http://apt.boxee.tv](http://apt.boxee.tv) hardy Release.gpg
Ign [http://apt.boxee.tv](http://apt.boxee.tv) hardy/main Translation-en_US                           
Ign [http://apt.boxee.tv](http://apt.boxee.tv) hardy/third Translation-en_US                          
Ign [http://apt.boxee.tv](http://apt.boxee.tv) hardy/party Translation-en_US                          
Ign [http://apt.boxee.tv](http://apt.boxee.tv) hardy Release                                          
Ign [http://apt.boxee.tv](http://apt.boxee.tv) hardy/main Packages                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US                     
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                             
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US               
Ign [http://apt.boxee.tv](http://apt.boxee.tv) hardy/third Packages                                   
Ign [http://apt.boxee.tv](http://apt.boxee.tv) hardy/party Packages                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US           
Hit [http://apt.boxee.tv](http://apt.boxee.tv) hardy/main Packages                                    
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg [307B]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                      
Err [http://apt.boxee.tv](http://apt.boxee.tv) hardy/third Packages                                   
  404 Not Found
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg [197B]                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US                 
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa Release.gpg                           
Err [http://apt.boxee.tv](http://apt.boxee.tv) hardy/party Packages                                   
  404 Not Found
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_US               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_US               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_US       
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release                                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/Hardy Translation-en_US                     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US             
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [65.9kB]                          
Get:4 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release [11.7kB]                     
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa/main Translation-en_US                
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa/upstream Translation-en_US            
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa/import Translation-en_US              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release                                     
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Get:5 [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa Release [7871B]                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages              
Get:6 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages [6334B]                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/Hardy Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/Hardy Sources                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages                
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/Hardy Packages                              
  404 Not Found
Get:7 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages [7345B]  
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa/main Packages                     
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/Hardy Sources                    
  404 Not Found
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa/upstream Packages
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa/import Packages
Hit [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa/main Packages
Hit [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa/upstream Packages
Hit [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa/import Packages 
Fetched 33.8kB in 1s (18.4kB/s)                          
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7D2C7A23BF810CD5
W: Failed to fetch [http://apt.boxee.tv/dists/hardy/third/binary-i386/Packages.gz](http://apt.boxee.tv/dists/hardy/third/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://apt.boxee.tv/dists/hardy/party/binary-i386/Packages.gz](http://apt.boxee.tv/dists/hardy/party/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ppa.launchpad.net/awn-testing/ubuntu/dists/hardy/Hardy/binary-i386/Packages.gz](http://ppa.launchpad.net/awn-testing/ubuntu/dists/hardy/Hardy/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ppa.launchpad.net/awn-testing/ubuntu/dists/hardy/Hardy/source/Sources.gz](http://ppa.launchpad.net/awn-testing/ubuntu/dists/hardy/Hardy/source/Sources.gz)  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
brandon@brandon-desktop ~ $ 

What am I doing wrong?

---

### Post by x33a on 2009-05-24
try changing your download server.

then
```
sudo aptitude update && sudo aptitude upgrade
```

---

### Post by thebrandon on 2009-05-24
So I tried the sudo aptitude update and got this :

brandon@brandon-desktop ~ $ sudo aptitude update
[sudo] password for brandon: 
Ign [http://apt.boxee.tv](http://apt.boxee.tv) hardy Release.gpg
Ign [http://apt.boxee.tv](http://apt.boxee.tv) hardy/main Translation-en_US                            
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                              
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US                
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg [307B]                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                       
Ign [http://apt.boxee.tv](http://apt.boxee.tv) hardy/third Translation-en_US                           
Ign [http://apt.boxee.tv](http://apt.boxee.tv) hardy/party Translation-en_US                           
Ign [http://apt.boxee.tv](http://apt.boxee.tv) hardy Release                                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US                      
Ign [http://apt.boxee.tv](http://apt.boxee.tv) hardy/main Packages                                     
Ign [http://apt.boxee.tv](http://apt.boxee.tv) hardy/third Packages                                    
Ign [http://apt.boxee.tv](http://apt.boxee.tv) hardy/party Packages                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/Hardy Translation-en_US                      
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [65.9kB]                           
Hit [http://apt.boxee.tv](http://apt.boxee.tv) hardy/main Packages                                     
Err [http://apt.boxee.tv](http://apt.boxee.tv) hardy/third Packages                                    
  404 Not Found
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_US                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_US                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_US        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release                                      
Err [http://apt.boxee.tv](http://apt.boxee.tv) hardy/party Packages                                    
  404 Not Found
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release                                     
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa Release.gpg                            
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg [197B]                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                           
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release                             
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa/main Translation-en_US                 
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa/upstream Translation-en_US             
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa/import Translation-en_US               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US              
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/Hardy Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/Hardy Sources                                
Get:4 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release [11.7kB]                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages               
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/Hardy Packages                               
  404 Not Found
Get:5 [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa Release [7871B]                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages                 
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/Hardy Sources                                
  404 Not Found
Get:6 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages [6334B]           
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa/main Packages              
Get:7 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages [7345B]
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa/upstream Packages
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa/import Packages
Hit [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa/main Packages
Hit [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa/upstream Packages
Hit [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa/import Packages 
Fetched 33.8kB in 1s (18.4kB/s)                          
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7D2C7A23BF810CD5
W: You may want to run apt-get update to correct these problems
brandon@brandon-desktop ~ $

---

### Post by x33a on 2009-05-24
try changing the download servers.

---

### Post by thebrandon on 2009-05-24
Well, Im a bit embarrassed to admit this as I thought I knew how, but I dont seem to know how to do that!  Can you point me in the right direction?

---

### Post by thebrandon on 2009-05-24
Nevermind, I took that lauchpad stuff, I think it was for awn, out of my repositories and suddenly the update started working!  I feel like a dummy, anyhow thanks for all of your help!

---

