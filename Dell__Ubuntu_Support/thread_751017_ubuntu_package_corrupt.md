---
title: "ubuntu package corrupt"
date: 2008-04-10
forum: Dell  Ubuntu Support
---

### Post by lowsignal on 2008-04-10
hello everyone,

i bought a dell inspirion 1525 with ubuntu 7.10 (gutsy gibbon) about a week ago, installed at the factory. i also have the cd. i'm not good with computers and i'm a former windows user with my last system being xp pro.

my system worked fine out of the box, but i wanted more software. i installed some software like firefox and epiphany. all was fine then too. then i used automatix to get more software. i tried to install a lot of the software that automatix offered. unfortunately it hung up in the process. it gave a message to please 'wait' while it was installing. i waited over an hour and a half with no more progress showing so i tried to stop it. unable to stop it i turned off the computer. now it won't update or upgrade anything. neither synaptec nor upgrade manager work now, not to mention automatix.

the error message told me to run "dpkg --configure -a". when i ran it, it went to the same place that it hung up originally. i left it run overnight hoping the process might complete, but it was in the same place in the morning.

unfortunately i don't remember the software it was trying to install when it hung.

i'm a little afraid to reinstall even though i have the cd.

the system seems to work ok with the exception of being unable to download and install anything further.

if anyone has any ideas about what to do, i'd be grateful.

thank you..

---

### Post by NeverM$4Me on 2008-04-10
Please try bringing up Synaptic Package Manager, select "Edit/Fix Broken Packages" then select "Edit/Apply Marked Changes".

See if that helps!

---

### Post by erginemr on 2008-04-10
If **NeverM$4Me**'s suggestion above does not work, then please try to update your system from the terminal:
```
sudo apt-get update
sudo apt-get upgrade
```
and** post the exact error messages produced here**.

You may try two generic commands to fix your package management system:
```
sudo apt-get install -f
sudo dpkg --configure -a
```

---

### Post by lowsignal on 2008-04-10
> **NeverM$4Me said:**
> Please try bringing up Synaptic Package Manager, select "Edit/Fix Broken Packages" then select "Edit/Apply Marked Changes".

See if that helps!

it says "dpkg was interrupted, you must manually run 'dpkg --configure -a' which doesn't work either. thanks for the suggestion.

EDIT: the 'thanks for the suggestion' was sincere. i didn't notice that it could have been taken in a bad way until i had already posted it. i really do thank you for trying to help me.

---

### Post by lowsignal on 2008-04-10
> **erginemr said:**
> If **NeverM$4Me**'s suggestion above does not work, then please try to update your system from the terminal:
```
sudo apt-get update
sudo apt-get upgrade
```
and** post the exact error messages produced here**.

You may try two generic commands to fix your package management system:
```
sudo apt-get install -f


this is what i get for "get update"..

----------------

tom@dell-desktop:~$ sudo apt-get update
[sudo] password for tom:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 http://www.getautomatix.com gutsy Release.gpg [189B]                     
Ign http://www.getautomatix.com gutsy/main Translation-en_US                   
Get:2 http://archive.ubuntu.com gutsy Release.gpg [191B]                       
Ign http://archive.ubuntu.com gutsy/main Translation-en_US                     
Get:3 http://security.ubuntu.com gutsy-security Release.gpg [191B]             
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US           
Get:4 http://www.getautomatix.com gutsy Release [6738B]                        
Get:5 http://archive.canonical.com gutsy Release.gpg [191B]                    
Ign http://archive.canonical.com gutsy/partner Translation-en_US               
Ign http://archive.ubuntu.com gutsy/restricted Translation-en_US               
Ign http://archive.ubuntu.com gutsy/multiverse Translation-en_US               
Ign http://archive.ubuntu.com gutsy/universe Translation-en_US                 
Get:6 http://archive.ubuntu.com gutsy-backports Release.gpg [191B]             
Ign http://archive.ubuntu.com gutsy-backports/main Translation-en_US           
Ign http://archive.ubuntu.com gutsy-backports/restricted Translation-en_US     
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US     
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US     
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US       
Hit http://www.getautomatix.com gutsy/main Packages                            
Hit http://security.ubuntu.com gutsy-security Release                          
Hit http://archive.canonical.com gutsy Release                                 
Ign http://archive.ubuntu.com gutsy-backports/universe Translation-en_US       
Ign http://archive.ubuntu.com gutsy-backports/multiverse Translation-en_US     
Get:7 http://archive.ubuntu.com gutsy-updates Release.gpg [191B]               
Ign http://archive.ubuntu.com gutsy-updates/main Translation-en_US             
Hit http://security.ubuntu.com gutsy-security/main Packages                    
Hit http://archive.canonical.com gutsy/partner Packages                        
Ign http://archive.ubuntu.com gutsy-updates/restricted Translation-en_US       
Ign http://archive.ubuntu.com gutsy-updates/universe Translation-en_US         
Ign http://archive.ubuntu.com gutsy-updates/multiverse Translation-en_US
Hit http://archive.ubuntu.com gutsy Release                
Hit http://archive.ubuntu.com gutsy-backports Release      
Hit http://security.ubuntu.com gutsy-security/restricted Packages              
Hit http://security.ubuntu.com gutsy-security/multiverse Packages              
Hit http://security.ubuntu.com gutsy-security/universe Packages                
Hit http://archive.ubuntu.com gutsy-updates Release                            
Hit http://security.ubuntu.com gutsy-security/main Sources                     
Hit http://security.ubuntu.com gutsy-security/restricted Sources               
Hit http://archive.ubuntu.com gutsy/main Packages                              
Hit http://archive.ubuntu.com gutsy/restricted Packages    
Hit http://archive.ubuntu.com gutsy/multiverse Packages    
Hit http://archive.ubuntu.com gutsy/universe Packages
Hit http://archive.ubuntu.com gutsy/main Sources           
Hit http://archive.ubuntu.com gutsy/restricted Sources     
Hit http://archive.ubuntu.com gutsy-backports/main Packages
Hit http://archive.ubuntu.com gutsy-backports/restricted Packages
Hit http://archive.ubuntu.com gutsy-backports/universe Packages
Hit http://archive.ubuntu.com gutsy-backports/multiverse Packages
Hit http://archive.ubuntu.com gutsy-updates/main Packages  
Hit http://archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://archive.ubuntu.com gutsy-updates/universe Packages
Hit http://archive.ubuntu.com gutsy-updates/multiverse Packages
Ign http://ppa.launchpad.net gutsy Release.gpg             
Ign http://ppa.launchpad.net gutsy/main Translation-en_US
Hit http://ppa.launchpad.net gutsy Release
Ign http://ppa.launchpad.net gutsy/main Packages
Ign http://ppa.launchpad.net gutsy/main Sources
Hit http://ppa.launchpad.net gutsy/main Packages                               
Hit http://ppa.launchpad.net gutsy/main Sources                                
Fetched 6744B in 6s (1027B/s)                                                  
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

sudo dpkg --configure -a
```

z

---

### Post by lowsignal on 2008-04-10
> **erginemr said:**
> If **NeverM$4Me**'s suggestion above does not work, then please try to update your system from the terminal:
```
sudo apt-get update
sudo apt-get upgrade
```
and** post the exact error messages produced here**.

You may try two generic commands to fix your package management system:
```
sudo apt-get install -f

for "upgrade" i get:

--------------------------------

tom@dell-desktop:~$ sudo apt-get upgrade
[sudo] password for tom:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
sudo dpkg --configure -a
```

-------------------------------

---

### Post by lowsignal on 2008-04-10
> **erginemr said:**
> If **NeverM$4Me**'s suggestion above does not work, then please try to update your system from the terminal:
```
sudo apt-get update
sudo apt-get upgrade
```
and** post the exact error messages produced here**.

You may try two generic commands to fix your package management system:
```
sudo apt-get install -f

for "install -f" i get:

----------------------------

tom@dell-desktop:~$ sudo apt-get install -f
[sudo] password for tom:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


sudo dpkg --configure -a
```

--------------------------------------

---

### Post by lowsignal on 2008-04-10
> **erginemr said:**
> If **NeverM$4Me**'s suggestion above does not work, then please try to update your system from the terminal:
```
sudo apt-get update
sudo apt-get upgrade
```
and** post the exact error messages produced here**.

You may try two generic commands to fix your package management system:
```
sudo apt-get install -f

for "sudo dpkg --configure -a" it hangs up in the same place and tells me to manually run 'dpkg --configure -a' again.

thanks for your help.

for "install -f" i get:

----------------------------

tom@dell-desktop:~$ sudo apt-get install -f
[sudo] password for tom:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


sudo dpkg --configure -a
```

--------------------------------------

---

### Post by lowsignal on 2008-04-12
hi erginemr,

i reinstalled ubuntu last night with no problem. then i installed the software that i wanted (including wine). then i gave administration priveldges to another user that i created just for safe surfing, intending later to revoke the same. i tried to install wine for this user and then the same problem as before happened. this time i didn't turn off the computer.  it's been running since last night.

the problem seems to be with 'msttcorefonts'. i don't understand why i could install wine for the other user and not the new one. anyway, it is frozen on 'please wait..' i can't cancel it with the cancel button.

do you or anyone have any idea on what would be the best course of action now?

thanks

---

### Post by erginemr on 2008-04-13
Well, I don't see any benefit of endless wait, so I suggest you to restart (or reset) your computer and run:
```
sudo dpkg --configure -a
```
and then,
```
sudo apt-get install -f
```
I don't understand why you are trying to install wine two times for two different users? Normally, a single install with root privileges should have served both users...

---

### Post by lowsignal on 2008-04-13
the last time i tried to resart the computer i had to turn it off instead. it froze while trying to shut down. then i couldn't download anything or run the dpkg --configure -a command. i had to reinstall. 

i don't know why wine wouldn't work with the other users. it didn't show up on any of the menus, except for the power user. i'm new to ubuntu, so i'm probably making mistakes. but i really like ubuntu and i'm not going back to windows. i'm starting to learn and will continue to learn for a long time. for me it will be a slow process. i'm grateful to you guys that help us noobs.

since i'm pretty sure that i'm going to have to reinstall again, i might just wait until 8.04 is ready and then just reinstall 7.10 in order to upgrade to 8.04 on the net. 

thanks again for the time you've taken to help me.

---

### Post by erginemr on 2008-04-14
You are welcome. I am sure you will reap the fruits of the time you have invested in Ubuntu in no time.

Just as a quick tip for your later reference, the menus for Gnome are kept in **~/.config/menus** and, esp. for wine, in **~/.local/share**, where ~ is the Linux shortcut for your home folder.

So, if you want, you can experiment with it by copying the power user's application menu to the other users' menu with:
```
(sudo) cp -r /home/<user_1>/.config/menus /home/<user_2>/.config/menus
(sudo) cp -r /home/<user_1>/.local/share /home/<user_2>/.local/share
```
or via Nautilus file manager, where Ctrl+H shows the hidden files and directories.

---

### Post by lowsignal on 2008-04-14
hi erginemr,

i found the process and killed it to end the problem. it was:

sudo killall automatix.py

and that was it. i really like this operating system. 

thanks again for the help.

---

### Post by erginemr on 2008-04-14
> **lowsignal said:**
> hi erginemr,

i found the process and killed it to end the problem. it was:

sudo killall automatix.py

and that was it. i really like this operating system. 

thanks again for the help.

:guitar: Take Care.

---

