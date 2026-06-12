---
title: "sources.list &amp; apt-get update error"
date: 2009-01-26
forum: General Help
---

### Post by detroit/zero on 2009-01-26
For the last few days, I've been getting an error whenever I run apt-get update from my terminal:```
zero@zero-laptop:~$ sudo apt-get update
Hit http://packages.medibuntu.org hardy Release.gpg                            
Ign http://packages.medibuntu.org hardy/free Translation-en_US                 
Get:1 http://download.tuxfamily.org ./ Release.gpg [197B]                      
Hit http://archive.canonical.com hardy Release.gpg                             
Ign http://archive.canonical.com hardy/partner Translation-en_US               
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US             
Hit http://packages.medibuntu.org hardy Release                                
Ign http://download.tuxfamily.org ./ Translation-en_US                         
Hit http://archive.canonical.com hardy Release                                 
Hit http://packages.medibuntu.org hardy/free Packages                          
Get:2 http://download.tuxfamily.org ./ Release [956B]                          
Hit http://archive.canonical.com hardy/partner Packages                        
Hit http://packages.medibuntu.org hardy/non-free Packages                      
Get:3 http://download.tuxfamily.org ./ Packages [9839B]                        
Hit http://archive.canonical.com hardy/partner Sources                         
Ign http://ppa.launchpad.net hardy Release.gpg                                 
Ign http://ppa.launchpad.net hardy/main Translation-en_US                  
Get:4 http://ppa.launchpad.net intrepid Release.gpg [307B]
Ign http://ppa.launchpad.net intrepid/main Translation-en_US
Ign http://ppa.launchpad.net hardy Release.gpg                 
Ign http://ppa.launchpad.net hardy/main Translation-en_US      
Ign http://ppa.launchpad.net hardy Release.gpg                 
Ign http://ppa.launchpad.net hardy/main Translation-en_US      
Ign http://ppa.launchpad.net hardy Release.gpg
Ign http://ppa.launchpad.net hardy/main Translation-en_US      
Get:5 http://ppa.launchpad.net hardy Release [27.6kB]          
Get:6 http://ppa.launchpad.net intrepid Release [27.6kB]               
Get:7 http://ppa.launchpad.net hardy Release [27.6kB]                          
Get:8 http://ppa.launchpad.net hardy Release [27.6kB]                          
Get:9 http://ppa.launchpad.net hardy Release [27.6kB]                          
Ign http://ppa.launchpad.net intrepid Release                                  
Ign http://ppa.launchpad.net hardy/main Packages                               
Ign http://ppa.launchpad.net hardy/main Packages               
Ign http://ppa.launchpad.net hardy/main Sources
Ign http://ppa.launchpad.net hardy/main Packages
Ign http://ppa.launchpad.net hardy/main Sources
Ign http://ppa.launchpad.net hardy/main Packages               
Ign http://ppa.launchpad.net hardy/main Sources                                
Ign http://ppa.launchpad.net intrepid/main Packages                            
Hit http://ppa.launchpad.net hardy/main Packages                               
Hit http://ppa.launchpad.net hardy/main Packages                               
Hit http://ppa.launchpad.net hardy/main Sources                                
Hit http://ppa.launchpad.net hardy/main Packages                               
Hit http://ppa.launchpad.net hardy/main Sources                                
Hit http://ppa.launchpad.net hardy/main Packages                               
Hit http://ppa.launchpad.net hardy/main Sources                                
Hit http://ppa.launchpad.net intrepid/main Packages                            
Hit http://de.archive.ubuntu.com hardy Release.gpg                             
Ign http://de.archive.ubuntu.com hardy/main Translation-en_US                  
Ign http://de.archive.ubuntu.com hardy/restricted Translation-en_US            
Ign http://de.archive.ubuntu.com hardy/universe Translation-en_US              
Ign http://de.archive.ubuntu.com hardy/multiverse Translation-en_US            
Hit http://de.archive.ubuntu.com hardy-updates Release.gpg                     
Ign http://de.archive.ubuntu.com hardy-updates/main Translation-en_US          
Ign http://de.archive.ubuntu.com hardy-updates/restricted Translation-en_US    
Ign http://de.archive.ubuntu.com hardy-updates/universe Translation-en_US      
Ign http://de.archive.ubuntu.com hardy-updates/multiverse Translation-en_US    
Hit http://de.archive.ubuntu.com hardy-backports Release.gpg                   
Ign http://de.archive.ubuntu.com hardy-backports/main Translation-en_US        
Ign http://de.archive.ubuntu.com hardy-backports/restricted Translation-en_US  
Ign http://de.archive.ubuntu.com hardy-backports/universe Translation-en_US    
Ign http://de.archive.ubuntu.com hardy-backports/multiverse Translation-en_US  
Hit http://de.archive.ubuntu.com hardy-security Release.gpg                    
Ign http://de.archive.ubuntu.com hardy-security/main Translation-en_US         
Ign http://de.archive.ubuntu.com hardy-security/restricted Translation-en_US   
Ign http://de.archive.ubuntu.com hardy-security/universe Translation-en_US     
Ign http://de.archive.ubuntu.com hardy-security/multiverse Translation-en_US   
Hit http://de.archive.ubuntu.com hardy-proposed Release.gpg                    
Ign http://de.archive.ubuntu.com hardy-proposed/restricted Translation-en_US   
Ign http://de.archive.ubuntu.com hardy-proposed/main Translation-en_US         
Ign http://de.archive.ubuntu.com hardy-proposed/multiverse Translation-en_US   
Ign http://de.archive.ubuntu.com hardy-proposed/universe Translation-en_US     
Hit http://de.archive.ubuntu.com hardy Release                                 
Hit http://de.archive.ubuntu.com hardy-updates Release                         
Hit http://de.archive.ubuntu.com hardy-backports Release                       
Hit http://de.archive.ubuntu.com hardy-security Release                        
Hit http://de.archive.ubuntu.com hardy-proposed Release                        
Hit http://de.archive.ubuntu.com hardy/main Packages                           
Hit http://de.archive.ubuntu.com hardy/restricted Packages                     
Hit http://de.archive.ubuntu.com hardy/main Sources                            
Hit http://de.archive.ubuntu.com hardy/restricted Sources                      
Hit http://de.archive.ubuntu.com hardy/universe Packages                       
Hit http://de.archive.ubuntu.com hardy/universe Sources                        
Hit http://de.archive.ubuntu.com hardy/multiverse Packages                     
Hit http://de.archive.ubuntu.com hardy/multiverse Sources                      
Hit http://de.archive.ubuntu.com hardy-updates/main Packages                   
Hit http://de.archive.ubuntu.com hardy-updates/restricted Packages             
Hit http://de.archive.ubuntu.com hardy-updates/main Sources                    
Hit http://de.archive.ubuntu.com hardy-updates/restricted Sources              
Hit http://de.archive.ubuntu.com hardy-updates/universe Packages               
Hit http://de.archive.ubuntu.com hardy-updates/universe Sources                
Hit http://de.archive.ubuntu.com hardy-updates/multiverse Packages             
Hit http://de.archive.ubuntu.com hardy-updates/multiverse Sources              
Hit http://de.archive.ubuntu.com hardy-backports/main Packages                 
Hit http://de.archive.ubuntu.com hardy-backports/restricted Packages           
Hit http://de.archive.ubuntu.com hardy-backports/universe Packages             
Hit http://de.archive.ubuntu.com hardy-backports/multiverse Packages           
Hit http://de.archive.ubuntu.com hardy-security/main Packages                  
Hit http://de.archive.ubuntu.com hardy-security/restricted Packages            
Hit http://de.archive.ubuntu.com hardy-security/main Sources                   
Hit http://de.archive.ubuntu.com hardy-security/restricted Sources             
Hit http://de.archive.ubuntu.com hardy-security/universe Packages              
Hit http://de.archive.ubuntu.com hardy-security/universe Sources               
Hit http://de.archive.ubuntu.com hardy-security/multiverse Packages            
Hit http://de.archive.ubuntu.com hardy-security/multiverse Sources             
Hit http://de.archive.ubuntu.com hardy-proposed/restricted Packages            
Hit http://de.archive.ubuntu.com hardy-proposed/main Packages                  
Hit http://de.archive.ubuntu.com hardy-proposed/multiverse Packages            
Hit http://de.archive.ubuntu.com hardy-proposed/universe Packages              
Fetched 11.3kB in 11s (1002B/s)                                                
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2BA7BC59D745C5EB
W: You may want to run apt-get update to correct these problems
```As you can see, one of the entries in my sources.list file must be no longer valid, but the thing is: I can't figure out which one.

I especially like how it tells me to run apt-get update to correct errors given by apt-get update.

At any rate, the error states that it's a problem with an Intrepid Release something at launchpad.net. The only Intrepid repo I have added is Kaivalagi's repo so I can stay current on his conky email scripts. Am I blind? Just stupid?

I've attached my sources.list if anybody cares to help me find the bad repo..

---

### Post by taurus on 2009-01-26
You are running hardy but how come you have a line for intrepid in your /etc/apt/sources.list?

```
Hit **[COLOR="Red"]http://ppa.launchpad.net intrepid/main[/COLOR]** Packages
```
Shouldn't mix repos in /etc/apt/sources.list since that is not a good practice.

---

### Post by detroit/zero on 2009-01-26
[I did that on advice from Kaivalagi]("http://ubuntuforums.org/showpost.php?p=6621566&postcount=174"). He told me that he keeps his Intrepid repo updated for his conky-email script, but not so much the Hardy repo.

Besides - I only changed that entry in sources.list just tonight, and I've been getting this error for three or four days now. (Actually the apt-get update && apt-get install conkyemail after that change is what I was doing when I saw the error again and it motivated me to finally make a post about it.)

Again, as far as I can see (and to the best of my knowledge) that's the only Intrepid repo in my entire sources.list file. Even if I comment that line out, I still get the error.

---

### Post by Twitch6000 on 2009-01-26
looking at the reply he gave you he said it should work,but he wasn't quite sure. 

He then also stated if you wanted to be sure it would work compile it from the source.

Your problem is indeed the repo.

---

### Post by sisco311 on 2009-01-26
```
gpg --keyserver keyserver.ubuntu.com --recv d745c5eb
```
```
gpg --export --armor d745c5eb | sudo apt-key add -
```
[http://ubuntuforums.org/showthread.php?p=6616484]("http://ubuntuforums.org/showthread.php?p=6616484")

---

### Post by detroit/zero on 2009-01-26
> **sisco311 said:**
> ```
gpg --keyserver keyserver.ubuntu.com --recv d745c5eb
``````
gpg --export --armor d745c5eb | sudo apt-key add -
```[http://ubuntuforums.org/showthread.php?p=6616484](http://ubuntuforums.org/showthread.php?p=6616484)
Worked like a charm. 

That's a neat little trick. I'll have to remember that one.

Thanks!

---

