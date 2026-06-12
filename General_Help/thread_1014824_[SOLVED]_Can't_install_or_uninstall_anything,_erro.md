---
title: "[SOLVED] Can't install or uninstall anything, error message"
date: 2008-12-18
forum: General Help
---

### Post by shelbyvision on 2008-12-18
Suddenly I can't use my update manager or synaptic. When I open synaptic, it tells me I have broken dependencies that need attention. When I try to do ANYTHING with synaptic I get this error message (see attachment). The same happens if I try to use the update manager. How can I fix this?
Thank you,
Steve

---

### Post by taurus on 2008-12-18
Close down synaptic or update-manager.  Then, open a terminal, Applications -> Accessories -> Terminal, and see what happens when you run this command.

```
sudo apt-get update
```

---

### Post by lovelyvik293 on 2008-12-18
You can use 
```

apt-get install -f

```
for fixing the broken packages.

---

### Post by shelbyvision on 2008-12-18
> **taurus said:**
> Close down synaptic or update-manager.  Then, open a terminal, Applications -> Accessories -> Terminal, and see what happens when you run this command.

```
sudo apt-get update
```
 
It gave me this:

steve@localhost:~$ sudo apt-get update
[sudo] password for steve:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/restricted Translation-en_US
Get:1 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [189B]                    
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US               
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [189B]   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US           
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US                  
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]             
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US  
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [189B]            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Translation-en_US        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release                      
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release [58.5kB]              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports Release              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages [12.4kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages [114kB]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources [2123B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Sources
Fetched 187kB in 5s (35.4kB/s)                     
Reading package lists... Done

---

### Post by shelbyvision on 2008-12-18
> **lovelyvik293 said:**
> You can use 
```

apt-get install -f

```
for fixing the broken packages.

I ran that and it gave me this error message:

dpkg: parse error, in file `/var/lib/dpkg/status' near line 28433 package `xrgb':
 field name `Dec' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by taurus on 2008-12-18
Now run the upgrade to see what happens.

```
sudo apt-get upgrade
```

---

### Post by shelbyvision on 2008-12-18
> **taurus said:**
> Now run the upgrade to see what happens.

```
sudo apt-get upgrade
```

OK, here's what is did:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  apport-gtk: Depends: apport (>= 0.41) but it is not installed
  bogofilter-bdb: Depends: libgsl0 (>= 1.4) but it is not installed
  ubuntu-desktop: Depends: nautilus-sendto but it is not installed
                  Recommends: gimp-print but it is not installed
E: Unmet dependencies. Try using -f.

When I tried -f I got this:

dpkg: parse error, in file `/var/lib/dpkg/status' near line 28433 package `xrgb':
field name `Dec' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by linux_tech on 2008-12-18
try repeating 
```
sudo apt-get upgrade 
```followed by
```
sudo apt-get install -f 
```
several times

---

### Post by shelbyvision on 2008-12-18
> **linux_tech said:**
> try repeating 
```
sudo apt-get upgrade 
```followed by
```
sudo apt-get install -f 
```
several times

OK, I tried it six times. No change.

---

### Post by shelbyvision on 2008-12-18
I checked the file mentioned in the error message: 
dpkg: parse error, in file `/var/lib/dpkg/status' near line 28433 package `xrgb':
field name `Dec' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)

Line 28433 is the first of 43 lines that start with "Dec 15". Here's line 28433: 

Dec 15 09:47:18 localhost kernel: [ 8720.016593] usb 5-1: reset high speed USB device using ehci_hcd and address 6

Times range to 12:10:21.
It seems that the error message is saying there should be a colon after each "Dec". Does that make any sense?

---

### Post by plucky on 2008-12-18
> Dec 15 09:47:18 localhost kernel: [ 8720.016593] usb 5-1: reset high speed USB device using ehci_hcd and address 6


That looks like a line that should be in a kernel error log,not a dpkg status file.

[b]What does the rest of the file look like? 
Does it have installed package information?[/b]


1) Make a copy of the status file ```
sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.before.edit
```

2) Edit the file and remove all the entries that look incorrect ```
gksudo gedit /var/lib/dpkg/status
```

3) See if that works ```
sudo apt-get update
``` should have no errors.


If the above doesn't work and you need to restore the original status file, Use ```
sudo cp /var/lib/dpkg/status.before.edit /var/lib/dpkg/status
```

Good Luck

---

### Post by shelbyvision on 2008-12-18
> **plucky said:**
> That looks like a line that should be in a kernel error log,not a dpkg status file.

[b]What does the rest of the file look like? 
Does it have installed package information?[/b]


1) Make a copy of the status file ```
sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.before.edit
```

2) Edit the file and remove all the entries that look incorrect ```
gksudo gedit /var/lib/dpkg/status
```

3) See if that works ```
sudo apt-get update
``` should have no errors.

If the above doesn't work and you need to restore the original status file, Use ```
sudo cp /var/lib/dpkg/status.before.edit /var/lib/dpkg/status
```

Good Luck


I'm sorry, that file has over 30000 lines. There's no way...

I need a real answer to this problem.

---

### Post by shelbyvision on 2008-12-19
I'll try again. Here's the message I get when I try to run the update manager: (first attachment)
Then here's the message I get when I open synaptic: (2nd attachment)
Then here are the broken packages: (3rd attachment)


Should I try re-installing, removal, or complete removal?

---

### Post by MeURi on 2008-12-19
Reinstall them, and let us know if something else happens, or if you get rid of your issues.

EDIT: sorry for what I wrote, I think it's better to do this way

- open Synaptic
- under Edit search for "Fx Broken Packages"

That should do it.

Let us know if it fixes your issues.

---

### Post by shelbyvision on 2008-12-19
> **MeURi said:**
> 

- open Synaptic
- under Edit search for "Fx Broken Packages"

That should do it.

Let us know if it fixes your issues.


OK, I tried that. It does nothing at all.

---

### Post by Elfy on 2008-12-19
Check to see if there is a backup - the system creates them. Run this in a terminal

```
ls /var/lib/dpkg/status*
```

If you have a /var/lib/dpkg/status-old - backup the new one to your home and copy the -old file

```
sudo cp /var/lib/dpkg/status ~/Desktop/status
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

Then update ```
sudo apt-get update
```

---

### Post by shelbyvision on 2008-12-19
> **forestpixie said:**
> Check to see if there is a backup - the system creates them. Run this in a terminal

```
ls /var/lib/dpkg/status*
```

If you have a /var/lib/dpkg/status-old - backup the new one to your home and copy the -old file

```
sudo cp /var/lib/dpkg/status ~/Desktop/status
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

Then update ```
sudo apt-get update
```

**BINGO!** That fixed it! Thank you. How do I do an official thank you, so it shows up in the records?
:p

---

### Post by Elfy on 2008-12-19
When you want to thank people use the marmite jar visible to you on other posts in the bottom right, next to the reply/quote buttons.

I've read your thanks so that's enough for me :)

---

