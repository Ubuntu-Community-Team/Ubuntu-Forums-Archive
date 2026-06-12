---
title: "[SOLVED] Protobuf on hardy - possible?"
date: 2008-12-14
forum: Desktop Environments
---

### Post by Izek on 2008-12-14
I just want to know, is it possible to install protobuf onto hardy? If so, how?

---

### Post by Izek on 2008-12-14
BAM!

[https://launchpad.net/~drizzle-developers/+archive](https://launchpad.net/~drizzle-developers/+archive)

And choose "The Hardy Heron" from the drop-down.

---

### Post by detroit/zero on 2009-01-07
> **Izek said:**
> BAM!

[https://launchpad.net/~drizzle-developers/+archive]("https://launchpad.net/%7Edrizzle-developers/+archive")

And choose "The Hardy Heron" from the drop-down.
I went through Loomsens tut the other night and everything worked flawlessly, but ever since I added protobuf repos to Hardy, Ive been getting update errors:
```
zero@zero-laptop:~$ sudo apt-get clean && sudo apt-get update && sudo apt-get upgrade
Get:1 http://download.tuxfamily.org ./ Release.gpg [197B]
Ign http://ppa.launchpad.net hardy Release.gpg                                 
Ign http://ppa.launchpad.net hardy/main Translation-en_US                      
Hit http://packages.medibuntu.org hardy Release.gpg                            
Ign http://download.tuxfamily.org ./ Translation-en_US                         
Ign http://ppa.launchpad.net hardy Release.gpg                                 
Ign http://ppa.launchpad.net hardy/main Translation-en_US                      
Ign http://ppa.launchpad.net hardy Release.gpg                                 
Ign http://ppa.launchpad.net hardy/main Translation-en_US                      
Ign http://ppa.launchpad.net hardy Release.gpg                                 
Ign http://ppa.launchpad.net hardy/main Translation-en_US                      
Ign http://ppa.launchpad.net intrepid Release.gpg                              
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                   
Ign http://ppa.launchpad.net hardy Release.gpg                                 
Get:2 http://download.tuxfamily.org ./ Release [956B]                          
Ign http://ppa.launchpad.net hardy/main Translation-en_US                      
Ign http://ppa.launchpad.net hardy Release.gpg                                 
Ign http://packages.medibuntu.org hardy/free Translation-en_US                 
Get:3 http://download.tuxfamily.org ./ Packages [9839B]                        
Ign http://ppa.launchpad.net hardy/main Translation-en_US                      
Get:4 http://ppa.launchpad.net hardy Release [27.6kB]                          
Get:5 http://ppa.launchpad.net hardy Release [27.6kB]                          
Get:6 http://ppa.launchpad.net hardy Release [27.6kB]                          
Get:7 http://ppa.launchpad.net hardy Release [27.6kB]                          
Get:8 http://ppa.launchpad.net intrepid Release [27.6kB]                       
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US             
Get:9 http://ppa.launchpad.net hardy Release [27.6kB]                          
Get:10 http://ppa.launchpad.net hardy Release [27.6kB]                         
Ign http://ppa.launchpad.net hardy/main Packages                               
Ign http://ppa.launchpad.net hardy/main Sources                                
Ign http://ppa.launchpad.net hardy/main Packages                               
Ign http://ppa.launchpad.net hardy/main Sources                                
Ign http://ppa.launchpad.net hardy/main Packages                               
Hit http://ubuntu.task.gda.pl hardy Release.gpg                                
Ign http://ubuntu.task.gda.pl hardy/main Translation-en_US                     
Ign http://ubuntu.task.gda.pl hardy/restricted Translation-en_US               
Ign http://ubuntu.task.gda.pl hardy/universe Translation-en_US                 
Ign http://ubuntu.task.gda.pl hardy/multiverse Translation-en_US               
Hit http://ubuntu.task.gda.pl hardy-updates Release.gpg                        
Ign http://ubuntu.task.gda.pl hardy-updates/main Translation-en_US             
Ign http://ubuntu.task.gda.pl hardy-updates/restricted Translation-en_US       
Ign http://ubuntu.task.gda.pl hardy-updates/universe Translation-en_US         
Ign http://ppa.launchpad.net hardy/main Packages                               
Ign http://ppa.launchpad.net hardy/main Sources                                
Ign http://ubuntu.task.gda.pl hardy-updates/multiverse Translation-en_US       
Hit http://ubuntu.task.gda.pl hardy-backports Release.gpg                      
Ign http://ubuntu.task.gda.pl hardy-backports/main Translation-en_US           
Ign http://ppa.launchpad.net intrepid/main Packages                            
Ign http://ppa.launchpad.net hardy/main Packages                               
Ign http://ppa.launchpad.net hardy/main Sources                                
Ign http://ppa.launchpad.net hardy/main Packages                               
Ign http://ppa.launchpad.net hardy/main Sources                                
Hit http://ppa.launchpad.net hardy/main Packages                               
Hit http://packages.medibuntu.org hardy Release                                
Hit http://ppa.launchpad.net hardy/main Sources                                
Hit http://ppa.launchpad.net hardy/main Packages                               
Hit http://ppa.launchpad.net hardy/main Sources                                
Ign http://ubuntu.task.gda.pl hardy-backports/restricted Translation-en_US     
Ign http://ubuntu.task.gda.pl hardy-backports/universe Translation-en_US       
Ign http://ubuntu.task.gda.pl hardy-backports/multiverse Translation-en_US     
Hit http://ubuntu.task.gda.pl hardy-security Release.gpg                       
Ign http://ubuntu.task.gda.pl hardy-security/main Translation-en_US            
Ign http://ubuntu.task.gda.pl hardy-security/restricted Translation-en_US      
Ign http://ubuntu.task.gda.pl hardy-security/universe Translation-en_US        
Ign http://ubuntu.task.gda.pl hardy-security/multiverse Translation-en_US      
Hit http://ubuntu.task.gda.pl hardy-proposed Release.gpg                       
Ign http://ubuntu.task.gda.pl hardy-proposed/restricted Translation-en_US      
Hit http://ppa.launchpad.net hardy/main Packages                               
Hit http://ppa.launchpad.net hardy/main Packages                               
Hit http://ppa.launchpad.net hardy/main Sources                                
Hit http://ppa.launchpad.net intrepid/main Packages                            
Hit http://ppa.launchpad.net hardy/main Packages                               
Hit http://ppa.launchpad.net hardy/main Sources                                
Hit http://ppa.launchpad.net hardy/main Packages                               
Hit http://ppa.launchpad.net hardy/main Sources                                
Ign http://ubuntu.task.gda.pl hardy-proposed/main Translation-en_US            
Ign http://ubuntu.task.gda.pl hardy-proposed/multiverse Translation-en_US      
Ign http://ubuntu.task.gda.pl hardy-proposed/universe Translation-en_US        
Hit http://ubuntu.task.gda.pl hardy Release                                    
Hit http://ubuntu.task.gda.pl hardy-updates Release                            
Hit http://ubuntu.task.gda.pl hardy-backports Release                          
Hit http://ubuntu.task.gda.pl hardy-security Release                           
Hit http://packages.medibuntu.org hardy/free Packages                          
Hit http://ubuntu.task.gda.pl hardy-proposed Release                           
Hit http://ubuntu.task.gda.pl hardy/main Packages                              
Hit http://ubuntu.task.gda.pl hardy/restricted Packages                        
Hit http://ubuntu.task.gda.pl hardy/main Sources                               
Hit http://ubuntu.task.gda.pl hardy/restricted Sources                         
Hit http://ubuntu.task.gda.pl hardy/universe Packages          
Hit http://ubuntu.task.gda.pl hardy/universe Sources           
Hit http://ubuntu.task.gda.pl hardy/multiverse Packages        
Hit http://ubuntu.task.gda.pl hardy/multiverse Sources         
Hit http://ubuntu.task.gda.pl hardy-updates/main Packages                      
Hit http://ubuntu.task.gda.pl hardy-updates/restricted Packages                
Hit http://ubuntu.task.gda.pl hardy-updates/main Sources                       
Hit http://packages.medibuntu.org hardy/non-free Packages      
Hit http://ubuntu.task.gda.pl hardy-updates/restricted Sources 
Hit http://ubuntu.task.gda.pl hardy-updates/universe Packages  
Hit http://ubuntu.task.gda.pl hardy-updates/universe Sources   
Hit http://ubuntu.task.gda.pl hardy-updates/multiverse Packages
Hit http://ubuntu.task.gda.pl hardy-updates/multiverse Sources 
Hit http://ubuntu.task.gda.pl hardy-backports/main Packages    
Hit http://ubuntu.task.gda.pl hardy-backports/restricted Packages
Hit http://ubuntu.task.gda.pl hardy-backports/universe Packages
Hit http://ubuntu.task.gda.pl hardy-backports/multiverse Packages
Hit http://ubuntu.task.gda.pl hardy-security/main Packages     
Hit http://ubuntu.task.gda.pl hardy-security/restricted Packages
Hit http://ubuntu.task.gda.pl hardy-security/main Sources      
Hit http://ubuntu.task.gda.pl hardy-security/restricted Sources
Hit http://ubuntu.task.gda.pl hardy-security/universe Packages 
Hit http://ubuntu.task.gda.pl hardy-security/universe Sources  
Hit http://ubuntu.task.gda.pl hardy-security/multiverse Packages
Hit http://ubuntu.task.gda.pl hardy-security/multiverse Sources
Hit http://ubuntu.task.gda.pl hardy-proposed/restricted Packages
Hit http://ubuntu.task.gda.pl hardy-proposed/main Packages     
Hit http://ubuntu.task.gda.pl hardy-proposed/multiverse Packages
Hit http://ubuntu.task.gda.pl hardy-proposed/universe Packages 
Hit http://archive.canonical.com hardy Release.gpg             
Ign http://archive.canonical.com hardy/partner Translation-en_US
Hit http://archive.canonical.com hardy Release
Hit http://archive.canonical.com hardy/partner Packages
Hit http://archive.canonical.com hardy/partner Sources
Fetched 11.0kB in 5s (1913B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR=Red]The following packages have been kept back:
  gimp gimp-data gimp-gnomevfs gimp-python libgimp2.0 libprotobuf-dev
  libprotobuf0 ntfs-3g protobuf-compiler[/COLOR]
0 upgraded, 0 newly installed, 0 to remove and [COLOR=Red]**9 not upgraded**[/COLOR].
```I'm not sure how GIMP fits into the picture, but I haven't been able to pull these updates for four or five days now.

Anybody have a clue?

---

