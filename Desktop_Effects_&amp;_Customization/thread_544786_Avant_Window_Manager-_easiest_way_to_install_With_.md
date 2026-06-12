---
title: "Avant Window Manager- easiest way to install With Beryl- Cause that is what I have-"
date: 2007-09-06
forum: Desktop Effects &amp; Customization
---

### Post by acelin on 2007-09-06
Yeh, I need some help- i tried using a familiar guide but It did not work.:guitar:

---

### Post by acelin on 2007-09-06
Bump

---

### Post by Inxsible on 2007-09-07
```
gksudo gedit /etc/apt/sources.list
```

Add the following two lines to the end of the file. Save and then close the file.
```
deb http://download.tuxfamily.org/syzygy42 feisty avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 feisty avant-window-navigator
```

then back in the terminal do```
sudo apt-get update && sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr
```

---

### Post by hyperair on 2007-09-07
Ok here you go:

1. Add "deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) feisty avant-window-navigator" to your sources.list file:
```

echo "deb http://download.tuxfamily.org/syzygy42 feisty avant-window-navigator" | sudo tee -a /etc/apt/sources.list

```

2. Add Reacocard's GPG key:
```

sudo wget http://download.tuxfamily.org/syzygy42/8434D43A.gpg -O - | sudo apt-key add -

```

3. Update your repositories:
```
sudo apt-get update
```

4. Install avant-window-navigator-bzr
```
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr
```

EDIT: Aw dammit someone beat me to it

---

### Post by Inxsible on 2007-09-07
> **hyperair said:**
> EDIT: Aw dammit someone beat me to itYes, but you gave him the GPG key which is good. I didn't remember reacocard's key, so i thought I'd better not give him the wrong one :)

---

### Post by acelin on 2007-09-07
E: Couldn't find package awn-core-applets-b
root@salane-laptop:/home/salane#

---

### Post by Inxsible on 2007-09-07
> **acelin said:**
> E: Couldn't find package awn-core-applets-b
root@salane-laptop:/home/salane#
you typed it in wrong. thats supposed to be awn-core-applets-bzr.

---

### Post by acelin on 2007-09-07
i typed in what was in above- copy and pasted.

---

### Post by acelin on 2007-09-07
root@salane-laptop:/home/salane# cho "deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) feisty avant-window-navigator" | sudo tee -a /etc/apt/sources.list
bash: cho: command not found
root@salane-laptop:/home/salane# sudo wget [http://download.tuxfamily.org/syzygy42/8434D43A.gpg](http://download.tuxfamily.org/syzygy42/8434D43A.gpg) -O - | sudo apt-key add -
--23:39:41--  [http://download.tuxfamily.org/syzygy42/8434D43A.gpg](http://download.tuxfamily.org/syzygy42/8434D43A.gpg)
           => `-'
Resolving download.tuxfamily.org... 88.191.250.18
Connecting to download.tuxfamily.org|88.191.250.18|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,682 (1.6K) [text/plain]

100%[====================================>] 1,682         --.--K/s             

23:39:41 (98.99 MB/s) - `-' saved [1682/1682]

OK
root@salane-laptop:/home/salane# sudo apt-get update
Get:1 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release.gpg [191B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US          
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US           
Get:4 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release.gpg [189B]                  
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Translation-en_US
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Translation-en_US
Get:5 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release.gpg [189B]                   
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Translation-en_US                 
Get:6 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release.gpg [189B]                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US           
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release                                
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release                               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Translation-en_US                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Translation-en_US            
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Translation-en_US             
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                   
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Packages       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release                               
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources              
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Sources        
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources              
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources             
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages                     
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Packages                
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Translation-en_US
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release
Err [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release                 
  
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages             
Get:8 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release [2965B]
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Packages                      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages                     
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Packages
Fetched 3350B in 1s (2959B/s)
Reading package lists... Done
root@salane-laptop:/home/salane# sudo apt-get install avant-window-navigator-bzr awn-core-applets-b
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package awn-core-applets-b
root@salane-laptop:/home/salane#

---

### Post by Inxsible on 2007-09-07
well you are missing out on letters in copy pasting surely.

the command is not "cho" its "echo"

Please make sure you copy the commands correctly. or you can simply type them in. just make sure you coapy/type them exactly !!

---

### Post by JBAlaska on 2007-09-07
Yup, I just updated my core applets with this command:
sudo apt-get install awn-core-applets-bzr

Worked a treat!

---

### Post by acelin on 2007-09-07
Thanks-

---

### Post by airtonix on 2007-12-26
cant install awn.

> :~$ sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzrReading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package avant-window-navigator-bzrsources.list
> ~$ cat /etc/apt/sources.list
deb [http://mirror.optus.net/ubuntu/](http://mirror.optus.net/ubuntu/) feisty main restricted universe multiverse
deb-src [http://mirror.optus.net/ubuntu/](http://mirror.optus.net/ubuntu/) feisty main restricted universe multiverse

deb [http://mirror.optus.net/ubuntu/](http://mirror.optus.net/ubuntu/) feisty-security main restricted universe multiverse
deb-src [http://mirror.optus.net/ubuntu/](http://mirror.optus.net/ubuntu/) feisty-security main restricted universe multiverse

deb [http://mirror.optus.net/ubuntu/](http://mirror.optus.net/ubuntu/) feisty-updates main restricted universe multiverse
deb-src [http://mirror.optus.net/ubuntu/](http://mirror.optus.net/ubuntu/) feisty-updates main restricted universe multiverse

deb [http://mirror.optus.net/ubuntu/](http://mirror.optus.net/ubuntu/) feisty-proposed main restricted universe multiverse
deb-src [http://mirror.optus.net/ubuntu/](http://mirror.optus.net/ubuntu/) feisty-proposed main restricted universe multiverse

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse


deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) feisty avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) feisty avant-window-navigator

## Screenlets
deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) feisty screenlets

navigating to [http://download.tuxfamily.org/syzygy42/pool/feisty/avant-window-navigator/](http://download.tuxfamily.org/syzygy42/pool/feisty/avant-window-navigator/)

reveals no deb for  'avant-window-navigator-bzr' or 'avant-window-navigator'

---

### Post by hyperair on 2007-12-26
Add to your sources.list:
```

deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator

```

---

### Post by Anshar007 on 2007-12-27
I also have the same error as airtonix is there a way around this I wanna have a cool looking dock ^^

---

### Post by hyperair on 2007-12-27
> **Anshar007 said:**
> I also have the same error as airtonix is there a way around this I wanna have a cool looking dock ^^

Did you bother reading my post?

---

### Post by Anshar007 on 2007-12-27
ah sorry hyper air...I also added that code to my source list but I'm still getting the same error I'm using feisty anyway

---

### Post by hyperair on 2007-12-27
Ah I'm sorry, I forgot to mention that you have to update your repositories first.
```
sudo apt-get update
```

Also, if you're using feisty, replace the word "gutsy" with "feisty" in that line.

---

### Post by Anshar007 on 2007-12-27
I made that change to my source.list like your told me....but I should have mentioned this before when ever I type in:

sudo wget [http://download.tuxfamily.org/syzygy42/8434D43A.gpg](http://download.tuxfamily.org/syzygy42/8434D43A.gpg) -O - | sudo apt-key add -

--12:36:03--  [http://download.tuxfamily.org/syzygy42/8434D43A.gpg](http://download.tuxfamily.org/syzygy42/8434D43A.gpg)
           => `-'
Resolving download.tuxfamily.org... 88.191.250.18
Connecting to download.tuxfamily.org|88.191.250.18|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
12:36:09 ERROR 404: Not Found.

gpg: no valid OpenPGP data found.

I get that :P....any idea why...thanks for you help thus far btw ^^

---

### Post by awiggin on 2007-12-27
When I try to add the repository, here is what I get:

Resolving download.tuxfamily.org...88.191.250.18
[some other stuff]
request sent, awaiting response... 404 Not found
22:00 ERROR 404: Not Found.

: no valid OpenPGP data found


I thought I added the repository to my sources list (it looks like it's there).  But when I type in apt-get install avant-window-navigator or avant-window-navigator-bzr , I always get something about the package not being found.

Is it hopeless?  Am I?  :(

---

### Post by Anshar007 on 2007-12-27
Maybe this method of installing is out of date or something??

---

