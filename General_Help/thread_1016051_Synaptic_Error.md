---
title: "Synaptic Error"
date: 2008-12-19
forum: General Help
---

### Post by laos.lindberg on 2008-12-19
I tried to run sunaptic and keep getting this error.
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

so i ran dpkg and here's what i got:

```
manning@manning-laptop:~$ sudo -s
[sudo] password for manning: 
root@manning-laptop:~# dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/updates/0030' near line 1:
 newline in field name `#padding'

```
what should i do?

thanks folks
laos

---

### Post by 73ckn797 on 2008-12-19
> **laos.lindberg said:**
> I tried to run sunaptic and keep getting this error.
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

so i ran dpkg and here's what i got:

```
manning@manning-laptop:~$ sudo -s
[sudo] password for manning: 
root@manning-laptop:~# dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/updates/0030' near line 1:
 newline in field name `#padding'

```what should i do?

thanks folks
laos

I do not know about all the terminal info, so I cannot help there. It could be something very simple. Try repairing broken packages via the edit menu selection within Synaptic. Try reloading package info in same edit menu. See what happens.

---

### Post by laos.lindberg on 2008-12-20
well synaptic doesnt even open up
running is gksu shows nothing

```

manning@manning-laptop:~$ sudo apt-get update
Hit http://archive.canonical.com intrepid Release.gpg
Ign http://archive.canonical.com intrepid/partner Translation-en_US            
Hit http://us.archive.ubuntu.com intrepid Release.gpg                          
Ign http://us.archive.ubuntu.com intrepid/main Translation-en_US               
Hit http://security.ubuntu.com intrepid-security Release.gpg                   
Ign http://security.ubuntu.com intrepid-security/main Translation-en_US        
Ign http://us.archive.ubuntu.com intrepid/restricted Translation-en_US         
Ign http://us.archive.ubuntu.com intrepid/universe Translation-en_US           
Ign http://us.archive.ubuntu.com intrepid/multiverse Translation-en_US         
Hit http://us.archive.ubuntu.com intrepid-updates Release.gpg                  
Ign http://us.archive.ubuntu.com intrepid-updates/main Translation-en_US       
Ign http://us.archive.ubuntu.com intrepid-updates/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com intrepid-updates/universe Translation-en_US   
Ign http://us.archive.ubuntu.com intrepid-updates/multiverse Translation-en_US 
Hit http://archive.canonical.com intrepid Release                              
Hit http://us.archive.ubuntu.com intrepid Release                              
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_US  
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_US    
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_US  
Hit http://security.ubuntu.com intrepid-security Release                       
Hit http://us.archive.ubuntu.com intrepid-updates Release                      
Hit http://archive.canonical.com intrepid/partner Packages                     
Hit http://us.archive.ubuntu.com intrepid/main Packages                        
Hit http://us.archive.ubuntu.com intrepid/restricted Packages                  
Hit http://us.archive.ubuntu.com intrepid/main Sources                         
Hit http://us.archive.ubuntu.com intrepid/restricted Sources                   
Hit http://us.archive.ubuntu.com intrepid/universe Packages                    
Hit http://security.ubuntu.com intrepid-security/main Packages                 
Hit http://archive.canonical.com intrepid/partner Sources                      
Hit http://us.archive.ubuntu.com intrepid/universe Sources                     
Hit http://us.archive.ubuntu.com intrepid/multiverse Packages                  
Hit http://us.archive.ubuntu.com intrepid/multiverse Sources    
Hit http://us.archive.ubuntu.com intrepid-updates/main Packages 
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Packages
Hit http://us.archive.ubuntu.com intrepid-updates/main Sources                 
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Sources           
Hit http://us.archive.ubuntu.com intrepid-updates/universe Packages
Hit http://security.ubuntu.com intrepid-security/restricted Packages
Hit http://security.ubuntu.com intrepid-security/main Sources                  
Hit http://security.ubuntu.com intrepid-security/restricted Sources            
Hit http://security.ubuntu.com intrepid-security/universe Packages             
Hit http://us.archive.ubuntu.com intrepid-updates/universe Sources             
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Packages          
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Sources           
Hit http://security.ubuntu.com intrepid-security/universe Sources              
Hit http://security.ubuntu.com intrepid-security/multiverse Packages
Hit http://security.ubuntu.com intrepid-security/multiverse Sources
Get:1 http://packages.medibuntu.org intrepid Release.gpg [189B]
Ign http://packages.medibuntu.org intrepid/free Translation-en_US
Ign http://packages.medibuntu.org intrepid/non-free Translation-en_US
Get:2 http://packages.medibuntu.org intrepid Release [11.7kB]
Ign http://packages.medibuntu.org intrepid Release
Hit http://packages.medibuntu.org intrepid/free Packages
Hit http://packages.medibuntu.org intrepid/non-free Packages
Fetched 190B in 3s (51B/s)
W: GPG error: http://packages.medibuntu.org intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
```

someone throw me a bone!

---

### Post by abn91c on 2008-12-20
try removing the medibuntu repositories then run sudo dpkg --configure -a

---

### Post by Maelgwyn on 2008-12-20
> **abn91c said:**
> try removing the medibuntu repositories
 

+1 - looks like medibuntu is being annoying for you too! I've just had an major issue with it, and just fixed it myself, looks similar but it didn't stop me updating...

---

### Post by laos.lindberg on 2008-12-20
I removed the medibuntu repositories and ran sudo dpkg --configure -a and it is still giving me the same parse error

i tried to reinstall the package manager, but the add/remove program won't allow me

---

### Post by Wisp558 on 2008-12-20
What are the contents of the file it refers to in the error?

Synaptic gave me issues once, and it was just a matter of deleting the offending line... I don't know about you, though.

---

### Post by laos.lindberg on 2008-12-24
hey
how do i go about deleting the offending line? how do i know which to delete?

thanks
laos

---

### Post by jerome1232 on 2008-12-24
> **73ckn797 said:**
> I do not know about all the terminal info, so I cannot help there. It could be something very simple. Try repairing broken packages via the edit menu selection within Synaptic. Try reloading package info in same edit menu. See what happens.

Well it looks like the offending file is /var/lib/dpkg/updates/0030 

so for safety sakes I would move the file out then try to run sudo dpkg --configure -a again

```
sudo mv /var/lib/dpkg/updates/0030 ~/0030
sudo dpkg --configure -a
```

---

### Post by laos.lindberg on 2008-12-28
thanks

i moved the 0030 file to my desktop and ran sudo dpkg --configure -a and got this:

```
manning@manning-laptop:~$ sudo dpkg --configure -a
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted
manning@manning-laptop:~$
```

thanks 
laos

---

### Post by HereInOz on 2008-12-29
What is the content of that file /var/lib/dpkg/updates/0030?  It would appear that the error is telling you that there is an error with that file near line #1.

Is it possible that you can take a copy of that file, for safety's sake, then have a look at the file and see if there is anything obvious in there that can be deleted.  

This is the line which has me suspicious
dpkg: parse error, in file `/var/lib/dpkg/updates/0030' near line 1:
 newline in field name `#padding'

That "newline in field name '#padding' " indicates something is amiss there.

---

### Post by wsscott on 2009-01-01
I had a similar problem with 10 broken packages in file /var/lib/dpkg/available due to a power failure when Synaptic was running. Tried several options using "apt-get" and the "fix broken packages" in Synaptic. No success with anything!  Solved when I saw that the problem file "available" had a sister file "available-old" in /var/lib/dpkg.  I moved the file "available" from /var/lib/dpkg, then renamed "available-old" as "available".  Was able to reinstall the package that failed during the power failure with no problems.

---

