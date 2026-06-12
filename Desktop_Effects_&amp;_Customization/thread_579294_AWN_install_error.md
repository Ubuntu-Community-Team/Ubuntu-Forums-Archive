---
title: "AWN install error"
date: 2007-10-18
forum: Desktop Effects &amp; Customization
---

### Post by lucksin on 2007-10-18
Hi I am having this problem while installing AWN..

> rohit@lucky:~$ sudo apt-get updateGet:1 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release.gpg [191B]
Get:2 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release.gpg [189B]                  
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Translation-en_IN              
Get:3 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty Release.gpg [191B]         
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]            
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Translation-en_IN
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release                             
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release                               
Err [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release                               
  
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main Translation-en_IN                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_IN          
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages                       
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Sources                        
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/restricted Translation-en_IN 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_IN    
Get:5 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release [26.9kB]                    
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages                       
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe Translation-en_IN             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_IN      
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/multiverse Translation-en_IN           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_IN    
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release                               
Get:6 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates Release.gpg [191B]  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release               
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Packages
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/main Translation-en_IN
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/restricted Translation-en_IN
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources         
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/main Packages                  
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/restricted Packages            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/main Sources                   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/restricted Sources             
Fetched 27.1kB in 8s (3308B/s)                                                 
Reading package lists... Done
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3E231AC7F4ECF181
W: You may want to run apt-get update to correct these problems

what am i suppose to do now ??

---

### Post by woyzeckswoe on 2007-10-18
i've got the same error

---

### Post by lucksin on 2007-10-18
good to know that i am not alone.. hehehe

---

### Post by Mikey_S on 2007-10-18
ditto, any solution yet? can't upgrade to gutsy without this :|

---

### Post by soccermonstar13 on 2007-10-18
MESSAGE REMOVED --- posted in wrong thread

---

### Post by ryanjrose on 2007-10-18
I started getting this message today as well!  I have tried several things to fix it.  Is there a GPG key somewhere on download.tuxfamily.org that we can import?

---

### Post by lucksin on 2007-10-19
any one found any solution to this problem ?? please keep us updated..

---

### Post by lucksin on 2007-10-19
wohooo got the solution... for all those who are still stuck.. here is the guide.. 

First of all you need to have a right key for the installation.. so download the key from here.. 
> wget [http://download.tuxfamily.org/syzygy42/reacocard.asc](http://download.tuxfamily.org/syzygy42/reacocard.asc)

then add the key to you system database.
> sudo apt-key add reacocard.asc

once its done just update your system
> sudo apt-get update

and then finally install the AWN
> sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr

thats it.. you are done.

i found the guide while Googling and after i was done i accidently closed the firefox window. so all thanks to the orignal poster for helping me. and i hope it helps other as well.

lucksin

---

### Post by PaulRay on 2007-10-21
Thank You lucksin! My applets are finally working! You Rock!!

---

