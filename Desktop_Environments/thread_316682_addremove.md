---
title: "add/remove"
date: 2006-12-11
forum: Desktop Environments
---

### Post by xptweakerntn on 2006-12-11
when i open add/remove applications, it always tells me that the list is outdated, i install the "update", but i have to do this everytime i open. is it normal, or, how can i fix it?

---

### Post by Ben Sprinkle on 2006-12-11
```

sudo apt-get update

```

---

### Post by bedake on 2007-02-22
I'm having this same issue, I just ran
```

sudo apt-get update

```
like the post above said but I am still receiving the same message saying that it is out of date each time it is ran.

---

### Post by Ben Sprinkle on 2007-02-23
Post the output of that command please.

---

### Post by bedake on 2007-02-23
```
Get:1 http://archive.ubuntu.com edgy Release.gpg [191B]                        
Ign http://archive.ubuntu.com edgy/main Translation-en_US                      
Get:2 http://medibuntu.sos-sts.com edgy Release.gpg [191B]                     
Ign http://archive.ubuntu.com edgy/restricted Translation-en_US                
Ign http://archive.ubuntu.com edgy/universe Translation-en_US                  
Ign http://archive.ubuntu.com edgy/multiverse Translation-en_US                
Get:3 http://archive.ubuntu.com edgy-proposed Release.gpg [191B]               
Ign http://archive.ubuntu.com edgy-proposed/main Translation-en_US             
Ign http://archive.ubuntu.com edgy-proposed/restricted Translation-en_US       
Ign http://archive.ubuntu.com edgy-proposed/universe Translation-en_US         
Ign http://archive.ubuntu.com edgy-proposed/multiverse Translation-en_US       
Get:4 http://archive.ubuntu.com edgy-updates Release.gpg [191B]                
Ign http://archive.ubuntu.com edgy-updates/main Translation-en_US              
Ign http://archive.ubuntu.com edgy-updates/restricted Translation-en_US        
Ign http://archive.ubuntu.com edgy-updates/universe Translation-en_US          
Ign http://archive.ubuntu.com edgy-updates/multiverse Translation-en_US        
Get:5 http://archive.ubuntu.com edgy-backports Release.gpg [191B]              
Ign http://archive.ubuntu.com edgy-backports/main Translation-en_US            
Ign http://archive.ubuntu.com edgy-backports/restricted Translation-en_US      
Ign http://archive.ubuntu.com edgy-backports/universe Translation-en_US        
Ign http://archive.ubuntu.com edgy-backports/multiverse Translation-en_US      
Get:6 http://archive.ubuntu.com edgy-security Release.gpg [191B]               
Ign http://archive.ubuntu.com edgy-security/main Translation-en_US             
Ign http://archive.ubuntu.com edgy-security/restricted Translation-en_US       
Ign http://archive.ubuntu.com edgy-security/universe Translation-en_US         
Ign http://archive.ubuntu.com edgy-security/multiverse Translation-en_US       
Hit http://archive.ubuntu.com edgy Release                                     
Hit http://archive.ubuntu.com edgy-proposed Release                            
Hit http://archive.ubuntu.com edgy-updates Release                             
Hit http://archive.ubuntu.com edgy-backports Release                           
Hit http://archive.ubuntu.com edgy-security Release                            
Ign http://medibuntu.sos-sts.com edgy/free Translation-en_US                   
Hit http://archive.ubuntu.com edgy/main Packages                               
Hit http://archive.ubuntu.com edgy/restricted Packages                         
Hit http://archive.ubuntu.com edgy/universe Packages                           
Hit http://archive.ubuntu.com edgy/multiverse Packages                         
Hit http://archive.ubuntu.com edgy/main Sources                                
Hit http://archive.ubuntu.com edgy/restricted Sources                          
Hit http://archive.ubuntu.com edgy/universe Sources                            
Hit http://archive.ubuntu.com edgy/multiverse Sources                          
Hit http://archive.ubuntu.com edgy-proposed/main Packages                      
Hit http://archive.ubuntu.com edgy-proposed/restricted Packages                
Hit http://archive.ubuntu.com edgy-proposed/universe Packages                  
Hit http://archive.ubuntu.com edgy-proposed/multiverse Packages                
Hit http://archive.ubuntu.com edgy-updates/main Packages                       
Hit http://archive.ubuntu.com edgy-updates/restricted Packages                 
Hit http://archive.ubuntu.com edgy-updates/universe Packages                   
Hit http://archive.ubuntu.com edgy-updates/multiverse Packages                 
Hit http://archive.ubuntu.com edgy-updates/main Sources                        
Hit http://archive.ubuntu.com edgy-updates/restricted Sources                  
Hit http://archive.ubuntu.com edgy-updates/universe Sources                    
Hit http://archive.ubuntu.com edgy-updates/multiverse Sources                  
Hit http://archive.ubuntu.com edgy-backports/main Packages                     
Hit http://archive.ubuntu.com edgy-backports/restricted Packages               
Hit http://archive.ubuntu.com edgy-backports/universe Packages                 
Hit http://archive.ubuntu.com edgy-backports/multiverse Packages               
Hit http://archive.ubuntu.com edgy-backports/main Sources                      
Hit http://archive.ubuntu.com edgy-backports/restricted Sources                
Hit http://archive.ubuntu.com edgy-backports/universe Sources                  
Hit http://archive.ubuntu.com edgy-backports/multiverse Sources                
Hit http://archive.ubuntu.com edgy-security/main Packages                      
Hit http://archive.ubuntu.com edgy-security/restricted Packages                
Ign http://medibuntu.sos-sts.com edgy/non-free Translation-en_US               
Hit http://archive.ubuntu.com edgy-security/universe Packages                  
Hit http://archive.ubuntu.com edgy-security/multiverse Packages                
Hit http://medibuntu.sos-sts.com edgy Release                                  
Hit http://medibuntu.sos-sts.com edgy/free Packages                            
Get:7 http://security.ubuntu.com edgy-security Release.gpg [191B]              
Ign http://security.ubuntu.com edgy-security/main Translation-en_US            
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US      
Get:8 http://archive.canonical.com edgy-commercial Release.gpg [191B]          
Ign http://archive.canonical.com edgy-commercial/main Translation-en_US        
Hit http://medibuntu.sos-sts.com edgy/non-free Packages                        
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US        
Ign http://security.ubuntu.com edgy-security/multiverse Translation-en_US      
Ign http://security.ubuntu.com edgy-security/multiverse Translation-en_US      
Hit http://security.ubuntu.com edgy-security Release                           
Hit http://archive.canonical.com edgy-commercial Release                       
Hit http://security.ubuntu.com edgy-security/main Packages                     
Hit http://archive.canonical.com edgy-commercial/main Packages                 
Hit http://security.ubuntu.com edgy-security/restricted Packages               
Hit http://security.ubuntu.com edgy-security/universe Packages                 
Hit http://security.ubuntu.com edgy-security/multiverse Packages               
Hit http://security.ubuntu.com edgy-security/main Sources                      
Hit http://security.ubuntu.com edgy-security/restricted Sources                
Hit http://security.ubuntu.com edgy-security/universe Sources                  
Hit http://security.ubuntu.com edgy-security/multiverse Sources                
Hit http://security.ubuntu.com edgy-security/multiverse Packages               
Hit http://medibuntu.sos-sts.com edgy/free Sources                             
Hit http://medibuntu.sos-sts.com edgy/non-free Sources                         
Err http://www.getautomatix.com edgy Release.gpg                               
  Could not connect to www.getautomatix.com:80 (82.165.193.29). - connect (111 Connection refused)
Err http://www.getautomatix.com edgy/main Translation-en_US                    
  Could not connect to www.getautomatix.com:80 (82.165.193.29). - connect (111 Connection refused)
Get:9 http://us.archive.ubuntu.com edgy Release.gpg [191B]                     
Ign http://us.archive.ubuntu.com edgy/multiverse Translation-en_US
Get:10 http://us.archive.ubuntu.com edgy-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com edgy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com edgy Release
Hit http://us.archive.ubuntu.com edgy-updates Release
Hit http://us.archive.ubuntu.com edgy/multiverse Packages
Hit http://us.archive.ubuntu.com edgy-updates/multiverse Packages
Fetched 10B in 20s (0B/s)
Failed to fetch http://www.getautomatix.com/apt/dists/edgy/Release.gpg  Could not connect to www.getautomatix.com:80 (82.165.193.29). - connect (111 Connection refused)
Failed to fetch http://www.getautomatix.com/apt/dists/edgy/main/i18n/Translation-en_US.bz2  Could not connect to www.getautomatix.com:80 (82.165.193.29). - connect (111 Connection refused)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by hikaricore on 2007-02-23
You have non-standard repos in your sources.list, aka comment them out and it should work.  Automatix is currently down btw. :P

---

### Post by bedake on 2007-02-23
> **hikaricore said:**
> You have non-standard repos in your sources.list, aka comment them out and it should work.  Automatix is currently down btw. :P

Ahh how do I identify the non standard repositories?  Searching the wiki I cant find anything about em

---

### Post by Nythain on 2007-02-23
kind of a stupid question... did you sudo apt-get upgrade after sudo apt-get update... that will automaticall get and install the newer versions of any software you have installed...

gotta love linux, i sudo aptitude update and upgrade about every day or two... so much better than waiting 6 month to 6 years for windows updates

---

### Post by Ben Sprinkle on 2007-02-23
> **bedake said:**
> Ahh how do I identify the non standard repositories?  Searching the wiki I cant find anything about em

```

Err http://www.getautomatix.com edgy Release.gpg                               
  Could not connect to www.getautomatix.com:80 (82.165.193.29). - connect (111 Connection refused)
Err http://www.getautomatix.com edgy/main Translation-en_US                    
  Could not connect to www.getautomatix.com:80 (82.165.193.29). - connect (111 Connection refused

```
:)

---

### Post by bedake on 2007-02-23
Alright, its working fine now thanks alot!

So it was just the fact that it couldent connect to the automatix repository that was causing it to say that it wasnt up to date?

---

### Post by Ben Sprinkle on 2007-02-23
> **bedake said:**
> Alright, its working fine now thanks alot!

So it was just the fact that it couldent connect to the automatix repository that was causing it to say that it wasnt up to date?
Yes sir. =)

---

### Post by Psquared on 2007-02-24
> **Ben Sprinkle said:**
> Yes sir. =)

getautomatix is still down????


Anybody know what the problem is?

---

