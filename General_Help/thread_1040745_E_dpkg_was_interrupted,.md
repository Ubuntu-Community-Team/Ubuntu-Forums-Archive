---
title: "E: dpkg was interrupted,"
date: 2009-01-15
forum: General Help
---

### Post by jaijaiyro on 2009-01-15
when i was trying to install cmake 
 or any other package i get this error
and i have not any clue on how to fix it 

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
```

please any help would be greatly appreciated

---

### Post by SuperSonic4 on 2009-01-15
Do what it says on the tin, just add sudo infront so it acts as root

```
sudo dpkg --configure -a
```

---

### Post by jaijaiyro on 2009-01-15
> **SuperSonic4 said:**
> Do what it says on the tin, just add sudo infront so it acts as root

```
sudo dpkg --configure -a
```

i just gave that a shot an got no response

---

### Post by cdtech on 2009-01-15
So now what do you get with:
```
sudo apt-get update
```

---

### Post by jaijaiyro on 2009-01-15
> **cdtech said:**
> So now what do you get with:
```
sudo apt-get update
```

i got this 

```
jay@jay-laptop:~$ sudo apt-get update
Get:1 http://security.ubuntu.com intrepid-security Release.gpg [189B]
Hit http://archive.canonical.com intrepid Release.gpg                          
Ign http://archive.canonical.com intrepid/partner Translation-en_US            
Hit http://archive.ubuntu.com intrepid Release.gpg                             
Ign http://security.ubuntu.com intrepid-security/main Translation-en_US        
Hit http://us.archive.ubuntu.com intrepid Release.gpg                          
Ign http://us.archive.ubuntu.com intrepid/main Translation-en_US               
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_US  
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_US    
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_US  
Hit http://wine.budgetdedicated.com intrepid Release.gpg                       
Ign http://wine.budgetdedicated.com intrepid/main Translation-en_US            
Hit http://archive.canonical.com intrepid Release                              
Hit http://archive.ubuntu.com intrepid Release                                 
Ign http://us.archive.ubuntu.com intrepid/restricted Translation-en_US         
Ign http://us.archive.ubuntu.com intrepid/universe Translation-en_US           
Ign http://us.archive.ubuntu.com intrepid/multiverse Translation-en_US         
Get:2 http://us.archive.ubuntu.com intrepid-updates Release.gpg [189B]         
Ign http://us.archive.ubuntu.com intrepid-updates/main Translation-en_US       
Get:3 http://security.ubuntu.com intrepid-security Release [44.0kB]            
Ign http://us.archive.ubuntu.com intrepid-updates/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com intrepid-updates/universe Translation-en_US   
Ign http://us.archive.ubuntu.com intrepid-updates/multiverse Translation-en_US 
Hit http://us.archive.ubuntu.com intrepid-backports Release.gpg                
Ign http://us.archive.ubuntu.com intrepid-backports/main Translation-en_US     
Ign http://us.archive.ubuntu.com intrepid-backports/restricted Translation-en_US
Hit http://wine.budgetdedicated.com intrepid Release                           
Ign http://us.archive.ubuntu.com intrepid-backports/universe Translation-en_US 
Ign http://us.archive.ubuntu.com intrepid-backports/multiverse Translation-en_US
Get:4 http://us.archive.ubuntu.com intrepid-proposed Release.gpg [189B]    
Ign http://us.archive.ubuntu.com intrepid-proposed/restricted Translation-en_US
Hit http://archive.canonical.com intrepid/partner Packages                     
Ign http://us.archive.ubuntu.com intrepid-proposed/main Translation-en_US      
Ign http://us.archive.ubuntu.com intrepid-proposed/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-proposed/universe Translation-en_US  
Hit http://us.archive.ubuntu.com intrepid Release                              
Get:5 http://us.archive.ubuntu.com intrepid-updates Release [51.2kB]           
Hit http://archive.ubuntu.com intrepid/main Sources                            
Ign http://wine.budgetdedicated.com intrepid/main Packages                     
Hit http://archive.canonical.com intrepid/partner Sources                      
Hit http://archive.ubuntu.com intrepid/restricted Sources                      
Hit http://wine.budgetdedicated.com intrepid/main Packages                     
Hit http://us.archive.ubuntu.com intrepid-backports Release
Get:6 http://us.archive.ubuntu.com intrepid-proposed Release [51.2kB]
Get:7 http://security.ubuntu.com intrepid-security/main Packages [52.2kB]   
Hit http://us.archive.ubuntu.com intrepid/main Packages                        
Hit http://us.archive.ubuntu.com intrepid/restricted Packages
Hit http://us.archive.ubuntu.com intrepid/restricted Sources
Hit http://us.archive.ubuntu.com intrepid/main Sources  
Hit http://us.archive.ubuntu.com intrepid/multiverse Sources
Hit http://us.archive.ubuntu.com intrepid/universe Sources
Hit http://us.archive.ubuntu.com intrepid/universe Packages
Hit http://us.archive.ubuntu.com intrepid/multiverse Packages
Get:8 http://us.archive.ubuntu.com intrepid-updates/main Packages [271kB]     
Get:9 http://security.ubuntu.com intrepid-security/restricted Packages [1785B]
Get:10 http://security.ubuntu.com intrepid-security/restricted Sources [571B]
Get:11 http://security.ubuntu.com intrepid-security/main Sources [16.0kB]      
Get:12 http://security.ubuntu.com intrepid-security/multiverse Sources [584B]
Get:13 http://security.ubuntu.com intrepid-security/universe Sources [3235B]   
Get:14 http://security.ubuntu.com intrepid-security/universe Packages [20.5kB]
Get:15 http://security.ubuntu.com intrepid-security/multiverse Packages [1330B]
Get:16 http://us.archive.ubuntu.com intrepid-updates/restricted Packages [5770B]
Get:17 http://us.archive.ubuntu.com intrepid-updates/restricted Sources [1701B]
Get:18 http://us.archive.ubuntu.com intrepid-updates/main Sources [83.7kB]
Get:19 http://us.archive.ubuntu.com intrepid-updates/multiverse Sources [1145B]
Get:20 http://us.archive.ubuntu.com intrepid-updates/universe Sources [7453B]
Get:21 http://us.archive.ubuntu.com intrepid-updates/universe Packages [36.0kB]
Get:22 http://us.archive.ubuntu.com intrepid-updates/multiverse Packages [3180B]
Hit http://us.archive.ubuntu.com intrepid-backports/main Packages
Hit http://us.archive.ubuntu.com intrepid-backports/restricted Packages
Hit http://us.archive.ubuntu.com intrepid-backports/universe Packages
Hit http://us.archive.ubuntu.com intrepid-backports/multiverse Packages
Hit http://us.archive.ubuntu.com intrepid-backports/main Sources
Hit http://us.archive.ubuntu.com intrepid-backports/restricted Sources
Hit http://us.archive.ubuntu.com intrepid-backports/universe Sources
Hit http://us.archive.ubuntu.com intrepid-backports/multiverse Sources
Get:23 http://us.archive.ubuntu.com intrepid-proposed/restricted Packages [6720B]
Get:24 http://us.archive.ubuntu.com intrepid-proposed/main Packages [82.2kB]
Get:25 http://us.archive.ubuntu.com intrepid-proposed/multiverse Packages [4052B]
Get:26 http://us.archive.ubuntu.com intrepid-proposed/universe Packages [44.5kB]
Fetched 790kB in 3s (230kB/s)                           
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
jay@jay-laptop:~$ 
```

---

### Post by cdtech on 2009-01-15
I would try both:
```

sudo apt-get autoremove
sudo dpkg --configure -a && sudo apt-get -f install

```
Then try running the update.........

---

### Post by jaijaiyro on 2009-01-15
> **cdtech said:**
> I would try both:
```

sudo apt-get autoremove
sudo dpkg --configure -a && sudo apt-get -f install

```
Then try running the update.........

i tryed the first cmd line and i got the same error

```
jay@jay-laptop:~$ sudo apt-get autoremove
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
jay@jay-laptop:~$ 

```

---

### Post by jaijaiyro on 2009-01-15
now i just tryed doing an update cause i saw the icon at my menu bar and i got this error while i tryed updating my apps

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

---

### Post by cdtech on 2009-01-15
Try this:
```
cd /var/lib/dpkg/updates
```
Then remove the files within that directory:
```
sudo rm *
```
That's a temporary directory and you may have a damaged file in there.
Then try the "sudo apt-get update"

---

### Post by jaijaiyro on 2009-01-15
> **cdtech said:**
> Try this:
```
cd /var/lib/dpkg/updates
```
Then remove the files within that directory:
```
sudo rm *
```
That's a temporary directory and you may have a damaged file in there.
Then try the "sudo apt-get update"

im not sure where to put the first code cause it does nothing in terminal, 
im a noob at this stuff 

sorry

---

### Post by cdtech on 2009-01-15
If you type the first line it changes you to the directory /var/lib/dpkg/updates, you probably don't see your in that directory.

Before you do the "rm" do an "ls" that will list the contents of the directory. Be sure your in the correct directory.

---

### Post by snova on 2009-01-15
Most of the time, when a command succeeds, it doesn't say anything. You only get output when it's status information or an error.

And, in this case, cd is such a commonly used command, to print something every time you run it would be *extremely* annoying.

It worked.

---

### Post by cdtech on 2009-01-15
Well put snova, thank you. You get a star if I could find em.......

---

### Post by jaijaiyro on 2009-01-15
okay now like i did the first command now i get this near my name 
```
jay@jay-laptop:/var/lib/dpkg/updates$ 
```
Should i run th rm at this point ?

---

### Post by snova on 2009-01-15
Yes.

---

### Post by jaijaiyro on 2009-01-15
awesome i ran that script and now im finishing up some system updates

any reason as to why this problem came up?

brb

---

