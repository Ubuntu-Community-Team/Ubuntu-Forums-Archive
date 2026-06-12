---
title: "Critical Temperature"
date: 2011-04-22
forum: Desktop Environments
---

### Post by aditya08 on 2011-04-22
Hi All,

I am using ubuntu 10.X as OS for my laptop. The laptop is over 18 months old. The laptop get heated up pretty soon and I get message..
"Critical Teamparature reaching, shutting down..

I don't play games on it, just usual document reading, watching movies, browing etc..Laptop configuration.
Memory - 4 GB
Processor - Core 2 duo P7450
OS - ubuntu 10.10 64 bit
Dell Studio 

temp1:       +68.0°C  (crit = +100.0°C)                  
temp2:       +71.0°C  (crit = +100.0°C)                  
temp3:       +95.0°C  (crit = +100.0°C)     

Regards,
Aditya

---

### Post by KegHead on 2011-04-22
Hi!

You're under critical temps.

Have you updated your kernel? (kernel manages many parameters)

sudo apt-get update

sudo aptitude install linux-image -f

You may need to restart..do so.

Please advise.

KegHead

---

### Post by aditya08 on 2011-04-22
Hi,

Will try now and leet you know.

---

### Post by aditya08 on 2011-04-22
First command was successful. However 2nd command wasn't..

tanu@tanu-Studio-1555:~$ sudo aptitude install linux-image -f
sudo: aptitude: command not found
tanu@tanu-Studio-1555:~$

---

### Post by KegHead on 2011-04-22
Hi!

Try;

sudo apt-get install linux-image -f

KegHead

---

### Post by lisati on 2011-04-22
> **aditya08 said:**
> First command was successful. However 2nd command wasn't..

tanu@tanu-Studio-1555:~$ sudo aptitude install linux-image -f
sudo: aptitude: command not found
tanu@tanu-Studio-1555:~$

aptitude isn't installed by default on some newer versions of Ubuntu. To install it:
```
sudo apt-get install aptitude
```

---

### Post by KegHead on 2011-04-22
Hi!

Thanks!

I've been running 11.04 from inception and used apt-get.

KegHead

---

### Post by aditya08 on 2011-04-22
Done. sudo apt-get install linux-image -f

Didn't ask for reboot though..now the temperature is ..
acpitz-virtual-0
Adapter: Virtual device
temp1:       +59.0°C  (crit = +100.0°C)                  
temp2:       +61.0°C  (crit = +100.0°C)                  
temp3:       +79.0°C  (crit = +100.0°C)

---

### Post by KegHead on 2011-04-22
Hmm,

FYI


jim@jim:~$ sudo apt-get update
[sudo] password for jim: 
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197 B]                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                        
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg [198 B]                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Get:3 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                          
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release [39.8 kB]                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                
Get:5 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,077 B]                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release                         
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources [864 kB]                 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en                         
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources [4,110 B]          
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources [4,381 kB]      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en          
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en        
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources [155 kB]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main i386 Packages [1,554 kB]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted i386 Packages [9,012 B]   
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe i386 Packages [6,019 kB]    
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse i386 Packages [183 kB]    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe i386 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse i386 Packages        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en_US                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en         
Fetched 13.2 MB in 16s (787 kB/s)                                              
Reading package lists... Done
jim@jim:~$ sudo aptitude install linux-image -f
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
                                         
jim@jim:~$

---

### Post by KegHead on 2011-04-22
Hi!

Thinking out loud!

Did your fan kick on? (it might at a certain temp)

KegHead

---

### Post by aditya08 on 2011-04-22
Here is the output of previous command..


tanu@tanu-Studio-1555:~$ sudo apt-get install linux-image -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-generic linux-image-2.6.35-28-generic linux-image-generic
Suggested packages:
  fdutils linux-doc-2.6.35 linux-source-2.6.35 linux-tools
The following NEW packages will be installed
  linux-image linux-image-2.6.35-28-generic
The following packages will be upgraded:
  linux-generic linux-image-generic
2 upgraded, 2 newly installed, 0 to remove and 316 not upgraded.
Need to get 34.2MB of archives.
After this operation, 139MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/main linux-image-2.6.35-28-generic amd64 2.6.35-28.50 [34.2MB]
Get:2 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/main linux-generic amd64 2.6.35.28.36 [5,446B]                                                             
Get:3 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/main linux-image-generic amd64 2.6.35.28.36 [5,456B]                                                       
Get:4 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/main linux-image amd64 2.6.35.28.36 [5,440B]                                                               
Fetched 34.2MB in 50s (679kB/s)                                                                                                                                        
Selecting previously deselected package linux-image-2.6.35-28-generic.
(Reading database ... 122913 files and directories currently installed.)
Unpacking linux-image-2.6.35-28-generic (from .../linux-image-2.6.35-28-generic_2.6.35-28.50_amd64.deb) ...
Done.

Preparing to replace linux-generic 2.6.35.22.23 (using .../linux-generic_2.6.35.28.36_amd64.deb) ...
Unpacking replacement linux-generic ...
Preparing to replace linux-image-generic 2.6.35.22.23 (using .../linux-image-generic_2.6.35.28.36_amd64.deb) ...
Unpacking replacement linux-image-generic ...
Selecting previously deselected package linux-image.
Unpacking linux-image (from .../linux-image_2.6.35.28.36_amd64.deb) ...
Setting up linux-image-2.6.35-28-generic (2.6.35-28.50) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-28-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-28-generic
Found initrd image: /boot/initrd.img-2.6.35-28-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up linux-image-generic (2.6.35.28.36) ...
Setting up linux-generic (2.6.35.28.36) ...
Setting up linux-image (2.6.35.28.36) ...

---

### Post by aditya08 on 2011-04-22
yep..Fan is running

---

### Post by KegHead on 2011-04-22
Hi!

Yup, your kernel was updated!

That might have solved your temp problem.

Give it a few hours-days!

If you're satisfied your question was answered, please mark your thread as "solved".

KegHead

---

### Post by aditya08 on 2011-04-22
Temperature is still high..
acpitz-virtual-0
Adapter: Virtual device
temp1:       +83.0°C  (crit = +100.0°C)                  
temp2:       +78.0°C  (crit = +100.0°C)                  
temp3:       +98.0°C  (crit = +100.0°C) 

It didn't solve the issue

---

### Post by KegHead on 2011-04-22
Hi!

Is there a red icon on the upper right hand part of your screen?

If it's red, you'll need to restart for the upgrade to take effect.

KegHead

---

### Post by aditya08 on 2011-04-22
Nope. Coz I have already restarted.

---

### Post by aditya08 on 2011-04-23
Hi All,

The issue is still  not resolved. Pls advise,

Thanks,
Aditya

---

### Post by KegHead on 2011-04-23
Hi!

Can you get into your bios?

You might have a few options there.

KegHead

---

### Post by aditya08 on 2011-04-24
I can.
Since the issue is unresolved, I will open a new thread.

---

