---
title: "Wireless not working on Dell Inspiron 1720!"
date: 2012-04-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by TheSingingCoyote on 2012-04-28
My dad has been having difficulty with the wireless after installing Ubuntu on his Dell Inspiron 1720. He's running 11.10. He asked me to see if I could help, but couldn't find much via google search. None of the commands I typed from the pages worked. 

I tried the below commands, and got the below information:
```
keith@keith-Inspiron-1720:~$ sudo apt-get update  
 [sudo] password for keith:  
 Sorry, try again.  
 [sudo] password for keith:  
 Err [http://extras.ubuntu.com]("http://extras.ubuntu.com/") oneiric InRelease  
    
 Err [http://security.ubuntu.com]("http://security.ubuntu.com/") oneiric-security InRelease  
    
 Err [http://extras.ubuntu.com]("http://extras.ubuntu.com/") oneiric Release.gpg  
   Could not resolve '[extras.ubuntu.com]("http://extras.ubuntu.com/")' 
 Err [http://security.ubuntu.com]("http://security.ubuntu.com/") oneiric-security Release.gpg  
   Could not resolve '[security.ubuntu.com]("http://security.ubuntu.com/")'  
 Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") oneiric InRelease  
    
 Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") oneiric-updates InRelease  
    
 Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") oneiric-backports InRelease  
    
 Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") oneiric Release.gpg  
   Could not resolve '[us.archive.ubuntu.com]("http://us.archive.ubuntu.com/")'  
 Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") oneiric-updates Release.gpg  
   Could not resolve '[us.archive.ubuntu.com]("http://us.archive.ubuntu.com/")'  
 Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") oneiric-backports Release.gpg  
   Could not resolve '[us.archive.ubuntu.com]("http://us.archive.ubuntu.com/")'  
 Reading package lists... Done  
 W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/oneiric/InRelease)   
 

 W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/InRelease)   
 

 W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/InRelease)   
 

 W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/InRelease](http://security.ubuntu.com/ubuntu/dists/oneiric-security/InRelease)   
 

 W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/InRelease](http://extras.ubuntu.com/ubuntu/dists/oneiric/InRelease)   
 

 W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release.gpg)  Could not resolve '[extras.ubuntu.com]("http://extras.ubuntu.com/")'  
 

 W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/oneiric-security/Release.gpg)  Could not resolve '[security.ubuntu.com]("http://security.ubuntu.com/")'  
 

 W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg)  Could not resolve '[us.archive.ubuntu.com]("http://us.archive.ubuntu.com/")'  
 

 W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release.gpg)  Could not resolve '[us.archive.ubuntu.com]("http://us.archive.ubuntu.com/")'  
 

 W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/Release.gpg)  Could not resolve '[us.archive.ubuntu.com]("http://us.archive.ubuntu.com/")'  
   
 W: Some index files failed to download. They have been ignored, or old ones used instead.  

```
The wireless image is blank, and when I click, it does not give the option for wireless at all. The options I do see are:

Wired Network
disconnected
VPN Connections
Enable Networking
Connection Information
Edit Connections


Wired Network, disconnected, and connection information are grey. I cannot click them, obviously. 


Any thoughts?

---

### Post by xbostonirishx on 2012-04-29
I have the same Box, and always have the same problem after a clean install. 

connect to the net through a land line. 

Go to system Settings, 

go to additional drivers. 

Update your drivers.

---

### Post by TheSingingCoyote on 2012-04-29
Unfortunately, this is meant (by my dad) to be used as a portable laptop. A land line just won't suffice, I'm afraid.

---

### Post by dontquoteme on 2012-04-30
> **xbostonirishx said:**
> I have the same Box, and always have the same problem after a clean install. 

connect to the net through a land line. 

Go to system Settings, 

go to additional drivers. 

Update your drivers.


This advice happens just once - to reload your STA drivers used by the Dell.

Many Dell systems use a Broadcom wireless card - which runs from STA drivers.

After we upgrade an OS, we have to reinstall the STA driver again.
You download the drivers and get the wireless working.  It's done once... but remember how to do this... as everytime a new release comes out, this extra step for those laptops with Broadcom wireless cards.

The Dell's do work - but not from the B43 drivers, you'll have a better wireless response with the STA driver. 

Dell's can work well with ubuntu - this is the only hiccup. :)

---

### Post by TheSingingCoyote on 2012-05-01
> **dontquoteme said:**
> This advice happens just once - to reload your STA drivers used by the Dell.

Many Dell systems use a Broadcom wireless card - which runs from STA drivers.

After we upgrade an OS, we have to reinstall the STA driver again.
You download the drivers and get the wireless working.  It's done once... but remember how to do this... as everytime a new release comes out, this extra step for those laptops with Broadcom wireless cards.

The Dell's do work - but not from the B43 drivers, you'll have a better wireless response with the STA driver. 

Dell's can work well with ubuntu - this is the only hiccup. :)



Where might I be able to download the STA driver? EDIT: It says it already has Broadcom STA wireless driver, if that's what you meant...

I really don't know what the problem is...

---

### Post by TheSingingCoyote on 2012-05-06
I'm not entirely certain if this topic is showing up anymore, so I'm going to bump it, as I really do need some help with this?

---

