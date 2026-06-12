---
title: "Enabling partner repo"
date: 2009-06-23
forum: General Help
---

### Post by chmacka on 2009-06-23
I can't enable partner repositories:

```
sudo apt-get update
Hit http://ba.archive.ubuntu.com jaunty Release.gpg
Ign http://ba.archive.ubuntu.com jaunty/main Translation-en_US                 
Ign http://ba.archive.ubuntu.com jaunty/restricted Translation-en_US           
Ign http://ba.archive.ubuntu.com jaunty/universe Translation-en_US             
Ign http://ba.archive.ubuntu.com jaunty/multiverse Translation-en_US           
Hit http://ba.archive.ubuntu.com jaunty-updates Release.gpg                    
Ign http://ba.archive.ubuntu.com jaunty-updates/main Translation-en_US         
Ign http://ba.archive.ubuntu.com jaunty-updates/restricted Translation-en_US   
Ign http://ba.archive.ubuntu.com jaunty-updates/universe Translation-en_US     
Ign http://ba.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US   
Hit http://packages.medibuntu.org hardy Release.gpg                            
Ign http://packages.medibuntu.org hardy/free Translation-en_US                 
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US             
Hit http://security.ubuntu.com jaunty-security Release.gpg                     
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US          
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US    
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US      
Hit http://ba.archive.ubuntu.com jaunty Release                                
Hit http://ba.archive.ubuntu.com jaunty-updates Release                        
Hit http://archive.canonical.com jaunty Release.gpg                            
Ign http://archive.canonical.com jaunty/partner Translation-en_US              
Hit http://packages.medibuntu.org hardy Release                                
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US    
Hit http://ba.archive.ubuntu.com jaunty/main Packages                          
Hit http://archive.canonical.com jaunty Release                                
Hit http://packages.medibuntu.org hardy/free Packages                          
Hit http://security.ubuntu.com jaunty-security Release                         
Hit http://ba.archive.ubuntu.com jaunty/restricted Packages          
Hit http://ba.archive.ubuntu.com jaunty/main Sources                 
Hit http://ba.archive.ubuntu.com jaunty/restricted Sources           
Hit http://ba.archive.ubuntu.com jaunty/universe Packages                      
Hit http://ba.archive.ubuntu.com jaunty/universe Sources                       
Hit http://packages.medibuntu.org hardy/non-free Packages                      
Hit http://ba.archive.ubuntu.com jaunty/multiverse Packages                    
Hit http://ba.archive.ubuntu.com jaunty/multiverse Sources                     
Hit http://ba.archive.ubuntu.com jaunty-updates/main Packages                  
Hit http://ba.archive.ubuntu.com jaunty-updates/restricted Packages  
Hit http://ba.archive.ubuntu.com jaunty-updates/main Sources         
Hit http://ba.archive.ubuntu.com jaunty-updates/restricted Sources             
Hit http://ba.archive.ubuntu.com jaunty-updates/universe Packages              
Hit http://ba.archive.ubuntu.com jaunty-updates/universe Sources               
Hit http://ba.archive.ubuntu.com jaunty-updates/multiverse Packages            
Ign http://archive.canonical.com jaunty/partner Packages                       
Hit http://ba.archive.ubuntu.com jaunty-updates/multiverse Sources             
Hit http://security.ubuntu.com jaunty-security/main Packages         
Ign http://archive.canonical.com jaunty/partner Sources              
Hit http://security.ubuntu.com jaunty-security/restricted Packages
Hit http://security.ubuntu.com jaunty-security/main Sources
Hit http://security.ubuntu.com jaunty-security/restricted Sources
Hit http://security.ubuntu.com jaunty-security/universe Packages     
Hit http://security.ubuntu.com jaunty-security/universe Sources      
Hit http://archive.canonical.com jaunty/partner Packages             
Hit http://security.ubuntu.com jaunty-security/multiverse Packages   
Hit http://security.ubuntu.com jaunty-security/multiverse Sources
Hit http://archive.canonical.com jaunty/partner Sources
Ign http://hendrik.kaju.pri.ee gutsy Release.gpg
Ign http://hendrik.kaju.pri.ee gutsy/screenlets Translation-en_US
Ign http://hendrik.kaju.pri.ee gutsy Release
Ign http://hendrik.kaju.pri.ee gutsy/screenlets Packages
Ign http://hendrik.kaju.pri.ee gutsy/screenlets Packages
Err http://hendrik.kaju.pri.ee gutsy/screenlets Packages
  404 Not Found
W: Failed to fetch http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/screenlets/binary-i386/Packages  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

---

### Post by chmacka on 2009-06-23
I forgot to close Synaptic. But even closing it didn't help:

```
sudo apt-get update
Hit http://ba.archive.ubuntu.com jaunty Release.gpg
Ign http://ba.archive.ubuntu.com jaunty/main Translation-en_US                 
Ign http://ba.archive.ubuntu.com jaunty/restricted Translation-en_US           
Ign http://ba.archive.ubuntu.com jaunty/universe Translation-en_US             
Ign http://ba.archive.ubuntu.com jaunty/multiverse Translation-en_US           
Hit http://ba.archive.ubuntu.com jaunty-updates Release.gpg                    
Ign http://ba.archive.ubuntu.com jaunty-updates/main Translation-en_US         
Ign http://ba.archive.ubuntu.com jaunty-updates/restricted Translation-en_US   
Ign http://ba.archive.ubuntu.com jaunty-updates/universe Translation-en_US     
Ign http://ba.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US   
Hit http://packages.medibuntu.org hardy Release.gpg                            
Ign http://packages.medibuntu.org hardy/free Translation-en_US                 
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US             
Hit http://security.ubuntu.com jaunty-security Release.gpg                     
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US          
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US    
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US      
Hit http://ba.archive.ubuntu.com jaunty Release                                
Hit http://ba.archive.ubuntu.com jaunty-updates Release                        
Hit http://archive.canonical.com jaunty Release.gpg                            
Ign http://archive.canonical.com jaunty/partner Translation-en_US              
Hit http://packages.medibuntu.org hardy Release                                
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US    
Hit http://ba.archive.ubuntu.com jaunty/main Packages                          
Hit http://archive.canonical.com jaunty Release                                
Hit http://packages.medibuntu.org hardy/free Packages                          
Hit http://security.ubuntu.com jaunty-security Release                         
Hit http://ba.archive.ubuntu.com jaunty/restricted Packages          
Hit http://ba.archive.ubuntu.com jaunty/main Sources                 
Hit http://ba.archive.ubuntu.com jaunty/restricted Sources           
Hit http://ba.archive.ubuntu.com jaunty/universe Packages                      
Hit http://ba.archive.ubuntu.com jaunty/universe Sources                       
Hit http://packages.medibuntu.org hardy/non-free Packages                      
Hit http://ba.archive.ubuntu.com jaunty/multiverse Packages                    
Hit http://ba.archive.ubuntu.com jaunty/multiverse Sources                     
Hit http://ba.archive.ubuntu.com jaunty-updates/main Packages                  
Hit http://ba.archive.ubuntu.com jaunty-updates/restricted Packages  
Hit http://ba.archive.ubuntu.com jaunty-updates/main Sources         
Hit http://ba.archive.ubuntu.com jaunty-updates/restricted Sources             
Hit http://ba.archive.ubuntu.com jaunty-updates/universe Packages              
Hit http://ba.archive.ubuntu.com jaunty-updates/universe Sources               
Hit http://ba.archive.ubuntu.com jaunty-updates/multiverse Packages            
Ign http://archive.canonical.com jaunty/partner Packages                       
Hit http://ba.archive.ubuntu.com jaunty-updates/multiverse Sources             
Hit http://security.ubuntu.com jaunty-security/main Packages         
Ign http://archive.canonical.com jaunty/partner Sources              
Hit http://security.ubuntu.com jaunty-security/restricted Packages
Hit http://security.ubuntu.com jaunty-security/main Sources
Hit http://security.ubuntu.com jaunty-security/restricted Sources
Hit http://security.ubuntu.com jaunty-security/universe Packages     
Hit http://security.ubuntu.com jaunty-security/universe Sources      
Hit http://archive.canonical.com jaunty/partner Packages             
Hit http://security.ubuntu.com jaunty-security/multiverse Packages   
Hit http://security.ubuntu.com jaunty-security/multiverse Sources
Hit http://archive.canonical.com jaunty/partner Sources
Ign http://hendrik.kaju.pri.ee gutsy Release.gpg
Ign http://hendrik.kaju.pri.ee gutsy/screenlets Translation-en_US
Ign http://hendrik.kaju.pri.ee gutsy Release
Ign http://hendrik.kaju.pri.ee gutsy/screenlets Packages
Ign http://hendrik.kaju.pri.ee gutsy/screenlets Packages
Err http://hendrik.kaju.pri.ee gutsy/screenlets Packages
  404 Not Found
W: Failed to fetch http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/screenlets/binary-i386/Packages  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
chmacka@chmacka-desktop:~$ sudo apt-get update
Hit http://packages.medibuntu.org hardy Release.gpg
Ign http://packages.medibuntu.org hardy/free Translation-en_US                 
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US             
Hit http://packages.medibuntu.org hardy Release                                
Hit http://archive.canonical.com jaunty Release.gpg                            
Ign http://archive.canonical.com jaunty/partner Translation-en_US              
Hit http://security.ubuntu.com jaunty-security Release.gpg                     
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US          
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US    
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US      
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US    
Hit http://packages.medibuntu.org hardy/free Packages                          
Hit http://security.ubuntu.com jaunty-security Release                         
Hit http://archive.canonical.com jaunty Release                                
Hit http://packages.medibuntu.org hardy/non-free Packages                      
Hit http://ba.archive.ubuntu.com jaunty Release.gpg                            
Hit http://security.ubuntu.com jaunty-security/main Packages                   
Ign http://archive.canonical.com jaunty/partner Packages                       
Hit http://security.ubuntu.com jaunty-security/restricted Packages   
Hit http://security.ubuntu.com jaunty-security/main Sources          
Hit http://security.ubuntu.com jaunty-security/restricted Sources    
Hit http://security.ubuntu.com jaunty-security/universe Packages               
Ign http://ba.archive.ubuntu.com jaunty/main Translation-en_US                 
Ign http://ba.archive.ubuntu.com jaunty/restricted Translation-en_US           
Ign http://ba.archive.ubuntu.com jaunty/universe Translation-en_US             
Ign http://ba.archive.ubuntu.com jaunty/multiverse Translation-en_US           
Hit http://ba.archive.ubuntu.com jaunty-updates Release.gpg          
Ign http://ba.archive.ubuntu.com jaunty-updates/main Translation-en_US
Ign http://archive.canonical.com jaunty/partner Sources              
Ign http://ba.archive.ubuntu.com jaunty-updates/restricted Translation-en_US
Ign http://ba.archive.ubuntu.com jaunty-updates/universe Translation-en_US
Ign http://ba.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US   
Hit http://security.ubuntu.com jaunty-security/universe Sources                
Hit http://security.ubuntu.com jaunty-security/multiverse Packages             
Hit http://security.ubuntu.com jaunty-security/multiverse Sources              
Hit http://archive.canonical.com jaunty/partner Packages                       
Hit http://ba.archive.ubuntu.com jaunty Release                      
Hit http://ba.archive.ubuntu.com jaunty-updates Release
Hit http://archive.canonical.com jaunty/partner Sources
Hit http://ba.archive.ubuntu.com jaunty/main Packages               
Hit http://ba.archive.ubuntu.com jaunty/restricted Packages
Hit http://ba.archive.ubuntu.com jaunty/main Sources
Hit http://ba.archive.ubuntu.com jaunty/restricted Sources
Hit http://ba.archive.ubuntu.com jaunty/universe Packages
Hit http://ba.archive.ubuntu.com jaunty/universe Sources
Hit http://ba.archive.ubuntu.com jaunty/multiverse Packages
Hit http://ba.archive.ubuntu.com jaunty/multiverse Sources
Hit http://ba.archive.ubuntu.com jaunty-updates/main Packages
Hit http://ba.archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://ba.archive.ubuntu.com jaunty-updates/main Sources
Hit http://ba.archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://ba.archive.ubuntu.com jaunty-updates/universe Packages
Hit http://ba.archive.ubuntu.com jaunty-updates/universe Sources
Hit http://ba.archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://ba.archive.ubuntu.com jaunty-updates/multiverse Sources
Ign http://hendrik.kaju.pri.ee gutsy Release.gpg
Ign http://hendrik.kaju.pri.ee gutsy/screenlets Translation-en_US
Ign http://hendrik.kaju.pri.ee gutsy Release
Ign http://hendrik.kaju.pri.ee gutsy/screenlets Packages
Ign http://hendrik.kaju.pri.ee gutsy/screenlets Packages
Err http://hendrik.kaju.pri.ee gutsy/screenlets Packages
  404 Not Found
W: Failed to fetch http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/screenlets/binary-i386/Packages  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by cariboo on 2009-06-23
Go to this [site]("http://dists/gutsy/screenlets/") and check the new url.

---

### Post by chmacka on 2009-06-23
> **cariboo907 said:**
> Go to this [site]("http://dists/gutsy/screenlets/") and check the new url.

*The domain dists.com is for sale. To purchase, call BuyDomains.com at 781-839-7903 or 866-866-2700. Click here for more details.*

---

