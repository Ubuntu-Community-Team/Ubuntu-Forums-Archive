---
title: "system freezes with Synaptic &amp; add/remove"
date: 2009-02-14
forum: General Help
---

### Post by ed1963 on 2009-02-14
Hi
I'm an absolute beginner to Ubuntu, and am having trouble with constant computer freezes.
It seems to happen when I use "Synaptic Package Manager" and "add/remove" in the system toolbar. The mouse pointer freezes and the hard drive stops whirring. It also happens when I try to run samba using the alt-f2 run command. 

I have managed to use the terminal screen to do some updates and get software like skype etc.

I'm using the latest version of Xbuntu (8.10?). I have 256mb ram on a slowish old computer (700mhz).
Internet is wireless.

Does anyone have any suggestions for me? As I said at the start, I'm an absolute beginner so it will probably take some patience! If any terminal commands are used it would be good if you could tell me what each line means too (so I learn).
Thanks in advance.

---

### Post by hyper_ch on 2009-02-14
hmmm, could be the specs... they are quite low... what do you want to install?

Open a terminal and run

```

sudo apt-get update

```

and post the output here.

---

### Post by ed1963 on 2009-02-14
Hi,
I want to run Samba so I can copy/share files from my Windows XP laptop, and other network type stuff. And also it would be good to have the package manager running properly anyway.
I typed the comand you suggested and got the following: (I hope this is what you meant by "post the output") 

Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid Release.gpg       
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/main Translation-en_NZ
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/restricted Translation-en_NZ
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/universe Translation-en_NZ
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/multiverse Translation-en_NZ
Get:1 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates Release.gpg [189B]
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/main Translation-en_NZ
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/restricted Translation-en_NZ
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/universe Translation-en_NZ
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_NZ
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid Release
Get:2 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates Release [51.2kB]           
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/main Packages             
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/main Sources       
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/restricted Sources 
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/universe Packages  
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/universe Sources   
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/multiverse Sources 
Get:3 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/main Packages [298kB]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg [189B]          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_NZ        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_NZ  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_NZ    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_NZ  
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release [44.0kB]            
Get:6 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/restricted Packages [6843B]
Get:7 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/main Sources [93.0kB]      
Get:8 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/restricted Sources [2016B] 
Get:9 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/universe Packages [69.7kB] 
Get:10 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/universe Sources [16.3kB] 
Get:11 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/multiverse Packages [5200B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages [66.1kB]     
Get:13 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/multiverse Sources [2366B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages [2079B]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources [19.2kB]      
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources [563B]  
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages [26.0kB] 
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources [5128B]   
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages [1330B]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources [584B]  
Fetched 710kB in 12s (54.8kB/s)                                                
Reading package lists... Done


Thanks

---

### Post by hyper_ch on 2009-02-14
run

```

sudo apt-get install samba

```

That was was I meant above, but enclose it in [noparse]```

```[/noparse] bracktes because it makes it easier to read...

---

### Post by ed1963 on 2009-02-14
OK, here's what comes up. I did "get install samba" earlier this morning. It hasn't put a "Samba" link anywhere on my applications menu that I can see. How would I normally start an application if its not on the shortcut menu?

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
samba is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

The Samba package is possibly a bit of a side issue, the freezing happens with any synaptic update, but a workaround for one may be a workaround for all.

---

### Post by hyper_ch on 2009-02-14
samba is a server.. a cli only program... you won't get a link for it...

if you want to setup sharing, have a look at this guide:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by ed1963 on 2009-02-27
SOLVED- OK, I've discovered that Xubuntu didn't like my 32mb PCI graphics card. When I changed the monitor to the onboard monitor plug, the freezing problem went away. Of course the computer goes even slower because some of the RAM has to be shared, but at least its not freezing :)

---

### Post by dsmithnc on 2009-02-27
I have been following several threads with the consistent "freezing" theme.

Today I took a chance and uninstalled the ATI driver on my PC.  Upside, no more freezes, downside, no control over screen resolution.  Onboard video died a while back.

Dick

---

