---
title: "Problems installing apps with Synaptic and 'Add/Remove'"
date: 2006-08-28
forum: Desktop Environments
---

### Post by mod187 on 2006-08-28
When I run Synaptic package manager, it asks me for my root password. I enter it, and then nothing happens. Nothing. I just sit here and wait. Still, nothing.

-and-

When I try to add an app with 'Add/Remove' from the Applications menu, I put a check in the box next to what I want to add and click 'Apply'. It then asks  if I want to apply the following changes (list of stuff I wanted), I click 'Apply', and a window pops up that says 'Checking installed and available applications'. It then takes me back to where I choose what I want to install, but what I have choosen is listed as *not installed. I check to see if the program has been installed, and it is not there.

any ideas?

---

### Post by aysiu on 2006-08-28
Well, first of all, Synaptic isn't asking for your *root* password. It's asking for your *user* password. To help me (or someone else) better diagnose this problem (and the other one), can you post the output of these commands (just highlight, copy, and paste everything from the terminal--do not summarize the output--post exactly what came out): ```
sudo aptitude update
cat /etc/apt/sources.list
gksudo synaptic
```

---

### Post by mod187 on 2006-08-28
> taylorm@ubuntu-AMD:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
Ign [http://dl.google.com](http://dl.google.com) stable Release.gpg
Hit [http://dl.google.com](http://dl.google.com) stable Release                                         
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release.gpg [189B]                     
Ign [http://dl.google.com](http://dl.google.com) stable/non-free Packages                               
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release                                  
Get:2 [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release.gpg [189B]                        
Hit [http://dl.google.com](http://dl.google.com) stable/non-free Packages                               
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release                                     
Ign [http://theli.free.fr](http://theli.free.fr) dapper Release.gpg                                     
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper/main Packages                            
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper Release.gpg                                  
Get:3 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]         
Ign [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages                               
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper Release                                      
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release                      
Hit [http://theli.free.fr](http://theli.free.fr) dapper Release                                         
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper/main Packages                                
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages                
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper/main Packages                                
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages                               
Ign [http://theli.free.fr](http://theli.free.fr) dapper/listen Packages                                 
Hit [http://theli.free.fr](http://theli.free.fr) dapper/listen Packages                                 
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]                    
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [189B]            
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release.gpg                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release.gpg [189B]              
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release                                         
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [189B]    
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [189B]  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release                                    
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/universe Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Fetched 9B in 5s (2B/s)  
Reading package lists... Done
taylorm@ubuntu-AMD:~$ 


> taylorm@ubuntu-AMD:~$ cat /etc/apt/sources.list
## Automatix sources.list
## This is automatically generated by Automatix


####################################
### Official Ubuntu Repositories ###
####################################

# Dapper Final Release Repository
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

# Dapper Security Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security multiverse

# Dapper Bugfix Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates multiverse

# Dapper Backports (new software versions, provided by the Ubuntu Backports Project)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main
#  deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports restricted
#  deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
#  deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports universe
#  deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main


##############################
### Automatix Repositories ###
##############################

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

## created by automatixrepo3
deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main
deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) dapper listen
deb [http://people.ubuntu.com/~seb128/deb](http://people.ubuntu.com/~seb128/deb) ./
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free
deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main


and

> taylorm@ubuntu-AMD:~$ gksudo synaptic
synaptic: error while loading shared libraries: libvte.so.4: cannot open shared object file: No such file or directory
taylorm@ubuntu-AMD:~$ 


---

### Post by aysiu on 2006-08-28
Well, your update and sources.list look good.

I Googled your error when launching Synaptic, and [this thread](http://www.ubuntuforums.org/showthread.php?p=1424019) looks like it might help.

---

### Post by mod187 on 2006-08-28
> sudo ln -s /usr/lib/libvte.so.9 /usr/lib/libvte.so.4

It workes now...

Many thanks, All-Mighty one...

---

### Post by aysiu on 2006-08-29
> **mod187 said:**
> It workes now...

Many thanks, All-Mighty one...
Thank Google, not me. All I did was search for your error.

---

### Post by mod187 on 2006-08-29
> gksudo synaptic

I need to learn what that means, and many other commands.

You pointed me into the right direction. If I knew to run that command, I may have been able to google it also.

Thanks again

---

### Post by randell6564 on 2006-08-29
> **aysiu said:**
> Thank Google, not me. All I did was search for your error.

Which YOU should have done! lol!

OK.,I admit it.,I'm guilty too!  But isn't this forum WONDERFUL?!  We can DO that!

---

