---
title: "Could not update ICEauthority file /home/user/.ICEauthority"
date: 2011-09-09
forum: Desktop Environments
---

### Post by haddog on 2011-09-09
Has anyone been able to resolve this issue? 

Could not update ICEauthority file /home/user/.ICEauthority

fyi. replace the word "user" above with your user name. mine is mister

I am encountering this today when attempting to login. Cannot access Ubuntu desktop. Running Ubuntu oneiric beta 1 32bit.

---

### Post by Krytarik on 2011-09-09
It doesn't seem to be a specific Oneiric issue, so just try this:

1. At the login screen, press Ctrl+Alt+F1 to get to the console.

2. Log in there.

3. Check if ".ICEauthority" is owned by you:
```
ls -al .ICEauthority
```4. If it isn't (but possibly by root), change it to you:
```
sudo chown USERNAME:USERNAME .ICEauthority
```5. Switch back to the login screen by pressing Ctrl+Alt+F7 or F8

6. Try again to log in.

If it worked, see here about a possible cause:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Good luck!

---

### Post by haddog on 2011-09-10
Thanks for the suggestion Krytarik. Unfortunately your suggestions did not work. .ICEauthority is owned by me, the user. I even ran the chown command anyway. I even went as far as performing chown on /home/USER/.ICEauthority . Still no luck. I'll checkout the link you provided.

---

### Post by Krytarik on 2011-09-10
Try removing ".ICEauthority". Therefore, log in at the console as before, and then run:
```
rm .ICEauthority
```

---

### Post by haddog on 2011-09-10
@ Krytarik. Well I am able to login to ubuntu now but not using Gnome. I searched ubuntuforums and saw a couple solutions that worked for others. One solution is to run sudo apt-get install gnome-session, which as I guessed, responded by saying I already have the latest version. The other solution was to run sudo apt-get install lxde. Installed, Ctrl-Alt-F7, to get back to the login screen, selected user defined session in the drop down menu, entered my password, able to now login to an LXDE session. Thought about removing gnome-session, and then re-installing. That seems a bit extreme though. Will try your suggestion of removing .ICEauthority first.

---

### Post by BushyIII on 2011-09-10
What is the consequence of removing ICEauthority?  In other words, what does ICEauthority do?

---

### Post by haddog on 2011-09-10
@ BushyIII . Got this from [http://www.x.org/releases/X11R7.6/doc/libICE/ICElib.html](http://www.x.org/releases/X11R7.6/doc/libICE/ICElib.html)

There are numerous possible inter-client protocols, with many similarities and common needs - authentication, version negotiation, byte order negotiation, and so on. The Inter-Client Exchange (ICE) protocol is intended to provide a framework for building such protocols, allowing them to make use of common negotiation mechanisms and to be multiplexed over a single transport connection.

Haven't found what I installed that affected ICE.

---

### Post by Krytarik on 2011-09-10
@haddog: Yeah, I know the "install gnome-session" workaround from this thread:
[http://ubuntuforums.org/showthread.php?t=1742343](http://ubuntuforums.org/showthread.php?t=1742343)

But as this is basically about the Gnome 3 provided by those PPA, and there are no threads about Oneiric flooding these forums, I didn't really consider this being a first choice option. However, if you want to try this, just "reinstall" gnome-session instead:
```
sudo apt-get install --reinstall gnome-session
```@BushyIII: Yeah, as *haddog* said, so not really easy to get a grip on this. ;-) And, one can safely remove ".ICEauthority" as it will be re-created at the next login. I've successfully tested this in earlier threads. But you can also back it up before, if you want to be safe.

However, as your [own issue]("http://ubuntuforums.org/showthread.php?t=1841419") is actually about not being able to access it in the first place, because your home directory apparently isn't decrypted at login, this isn't your solution anyway.

---

### Post by haddog on 2011-09-10
duplicate - removed - see next message

---

### Post by haddog on 2011-09-10
> **haddog said:**
> Wow.... So I am back in Gnome, able to login, but with a "very different Gnome desktop"! So after installing LXDE, I remember my login probs started a couple days ago after doing a sudo apt-get upgrade and then I did a sudo apt-get install and installed the held back packages....can't remember what they were. Hey it is a Beta right? :-) I also recall that I had installed the open source version of M$ Silverlight, Moonlight, and I had to also install Chromium because Mozilla FF 7 wouldn't support Moonlight. So while in LXDE, I un-installed the Chromium Moonlight extension and rebooted. Could login to Gnome but there was only a menu at the top left of the desktop showing file, view, help, etc. There were no volume, battery, bluetooth user or logout/shutdown/restart indicators to the right. Unity desktop was partial, no launcher. So I went to file then open in the menu. Now I could see my home directory contents but Ubuntu Gnome desktop locked up. Did a powerdown by hold down the power button. Rebooted. This time I selected recovery console. At the recovery console menu I selected 'repair broken packages'. Package found/needing repair was Gnome-shell, I hit enter. Ubuntu dloaded the necessary file(s), installed Gnome-shell files and then sent me back to the recovery console menu where I selected normal boot. I selected my user, entered my password and selected Gnome as my session and got logged in. Very different desktop, not Ubuntu Unity.

Fyi. I just googled Gnome 3. It appears now have the Gnome 3 desktop instead on Unity...kinda neat.

---

### Post by Krytarik on 2011-09-10
Yeah, now you are - currently - using Gnome Shell. Tell us how you find it, compared to Unity. ;-)

But you should, nevertheless, still be able to choose "Ubuntu" as the session option to get to the Unity interface. Are you?

---

### Post by haddog on 2011-09-10
I have 5 session login options:

GNOME
GNOME/Openbox
LXDE
Openbox
Recovery Console
User Defined Session

No Ubuntu sessions listed. Gnome/Openbox and Openbox seem to be the Ubuntu Unity sessions though, as they show the desktop wallpaper I used when Unity was functional. Neither Gnome/Openbox or Openbox will produce a complete Unity desktop, only a menu at the top left of the dekstop. Haven't figured out how to repair Unity...

I like Gnome Shell. Not better than Unity, just different. I like them both, in particular the search function they employ at the "desktop".

---

### Post by Krytarik on 2011-09-10
Hmm, following the "gnome-session" package I can examine [here]("http://packages.ubuntu.com/oneiric/gnome-session"), there should be an "Ubuntu" session option. Please try reinstalling it with the earlier stated command.

---

### Post by haddog on 2011-09-10
> **Krytarik said:**
> Hmm, following the "gnome-session" package I can examine [here]("http://packages.ubuntu.com/oneiric/gnome-session"), there should be an "Ubuntu" session option. Please try reinstalling it with the earlier stated command.

O.k. Will try:

sudo apt-get install --reinstall gnome-session

---

### Post by haddog on 2011-09-10
Reinstalled gnome-session. Produced the following results:

misterT@3bootmini:~$ sudo apt-get install --reinstall gnome-session
[sudo] password for misterT: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/13.8 kB of archives.
After this operation, 0 B of additional disk space will be used.
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 31604 package 'gverse':
 error in Version string '.06': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 34063 package 'gverse':
 error in Version string '.06': version number does not start with digit
(Reading database ... 276902 files and directories currently installed.)
Preparing to replace gnome-session 3.1.91-0ubuntu2 (using .../gnome-session_3.1.91-0ubuntu2_all.deb) ...
Unpacking replacement gnome-session ...
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 31605 package 'gverse':
 error in Version string '.06': version number does not start with digit
Setting up gnome-session (3.1.91-0ubuntu2) ...
Error org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 127
misterT@3bootmini:~$ 

Lot's of errors. Rebooted. Still no Ubuntu session...

---

### Post by Krytarik on 2011-09-10
Urghh, ugly error messages there. ;-) Try cleaning them up by following the steps in this guide:

[https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure](https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure)

---

### Post by haddog on 2011-09-10
```
mista@3bootmini:~$ sudo fuser -vvv /var/lib/dpkg/lock
[sudo] password for mista: 
mista@3bootmini:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu oneiric (development branch)"
mista@3bootmini:~$ uname -a
Linux 3bootmini 3.0.0-10-generic #16-Ubuntu SMP Fri Sep 2 18:38:35 UTC 2011 i686 i686 i386 GNU/Linux
mista@3bootmini:~$ sudo rm /var/lib/apt/lists/lock
mista@3bootmini:~$ sudo cp -arf /var/lib/dpkg /var/lib/dpkg.backup

^Cmista@3bootmini:~$ sudo cp -arf /var/lib/dpkg /var/lib/dpkg.backup
mista@3bootmini:~$ sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
mista@3bootmini:~$ sudo cp /var/lib/dpkg/available-old /var/lib/dpkg/available
mista@3bootmini:~$ sudo rm -rf /var/lib/dpkg/updates/*
mista@3bootmini:~$ sudo rm -rf /var/lib/apt/lists
mista@3bootmini:~$ sudo rm /var/cache/apt/*.bin
mista@3bootmini:~$ sudo mkdir /var/lib/apt/lists
mista@3bootmini:~$ sudo mkdir /var/lib/apt/lists/partial
mista@3bootmini:~$ LANG=C;sudo apt-get clean
mista@3bootmini:~$ LANG=C;sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mista@3bootmini:~$ LANG=C;sudo apt-get --purge autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 31605 package 'gverse':
 error in Version string '.06': version number does not start with digit
Setting up gnome-session (3.1.91-0ubuntu2) ...
Error org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 127
mista@3bootmini:~$ LANG=C;sudo apt-get update -o APT::Cache-Limit=25165824
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric InRelease                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates InRelease              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports InRelease                      
Get:1 [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg [198 B]                 
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg [198 B]          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-proposed InRelease             
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release.gpg [198 B]                    
Get:4 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg [72 B]                      
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release [23.2 kB]            
Get:6 [http://archive.canonical.com](http://archive.canonical.com) oneiric Release [5922 B]          
Get:7 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release [9759 B]                        
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release.gpg [198 B]            
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports Release.gpg [198 B]          
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-proposed Release.gpg [198 B]          
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release [39.8 kB]                     
Get:12 [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Sources [1346 B]           
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages [14 B]   
Get:14 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages [14 B]              
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release [23.2 kB]             
Get:16 [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages [2821 B]     
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages [14 B]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages [14 B]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages [14 B]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports Release [23.3 kB]           
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-proposed Release [23.2 kB]            
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main i386 Packages [1579 kB]          
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe i386 Packages [6411 kB]
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted i386 Packages [9007 B]     
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse i386 Packages [176 kB]     
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main i386 Packages [14 B]     
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe i386 Packages [14 B] 
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted i386 Packages [14 B]
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse i386 Packages [14 B]
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/main i386 Packages [14 B]   
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/universe i386 Packages [14 B]
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/restricted i386 Packages [14 B]
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/multiverse i386 Packages [14 B]
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-proposed/main i386 Packages [14 B]    
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-proposed/universe i386 Packages [14 B]
Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-proposed/restricted i386 Packages [14 B]
Get:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-proposed/multiverse i386 Packages [14 B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main TranslationIndex                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse TranslationIndex              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted TranslationIndex              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe TranslationIndex                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main TranslationIndex            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted TranslationIndex      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe TranslationIndex        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/main TranslationIndex          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/restricted TranslationIndex    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/universe TranslationIndex      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-proposed/main TranslationIndex           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-proposed/multiverse TranslationIndex     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-proposed/restricted TranslationIndex     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-proposed/universe TranslationIndex       
Fetched 8329 kB in 27s (304 kB/s)                                              
Error org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 127
Reading package lists... Done
mista@3bootmini:~$ sudo dpkg --clear-avail
mista@3bootmini:~$ sudo dpkg --configure -a
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 31604 package 'gverse':
 error in Version string '.06': version number does not start with digit
mista@3bootmini:~$ LANG=C;sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mista@3bootmini:~$ LANG=C;sudo apt-get --fix-missing install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mista@3bootmini:~$ LANG=C;sudo apt-get update -o APT::Cache-Limit=25165824 && sudo apt-get dist-upgrade
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg          
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                         
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages              
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric InRelease                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates InRelease              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports InRelease            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-proposed InRelease             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release.gpg                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release.gpg                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports Release.gpg          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-proposed Release.gpg           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                     
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports Release               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-proposed Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main i386 Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe i386 Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted i386 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse i386 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main i386 Packages      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-proposed/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-proposed/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-proposed/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-proposed/multiverse i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/main TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/restricted TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/universe TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-proposed/main TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-proposed/multiverse TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-proposed/restricted TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-proposed/universe TranslationIndex
Error org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 127
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mista@3bootmini:~$ sudo apt-get install --reinstall gnome-session
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 13.8 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main gnome-session all 3.1.91-0ubuntu2 [13.8 kB]
Fetched 13.8 kB in 0s (19.1 kB/s)       
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 31604 package 'gverse':
 error in Version string '.06': version number does not start with digit
(Reading database ... 276902 files and directories currently installed.)
Preparing to replace gnome-session 3.1.91-0ubuntu2 (using .../gnome-session_3.1.91-0ubuntu2_all.deb) ...
Unpacking replacement gnome-session ...
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 31605 package 'gverse':
 error in Version string '.06': version number does not start with digit
Setting up gnome-session (3.1.91-0ubuntu2) ...
Error org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 127
mista@3bootmini:~$ 
```

************************************************************

Didn't resolve the gnome-session reinstall errors. I posted the terminal output to launchpad also.

[https://answers.launchpad.net/ubuntu/+question/170777](https://answers.launchpad.net/ubuntu/+question/170777)

---

### Post by Krytarik on 2011-09-10
This is actually an issue with the somehow half-installed package "gverse", and has nothing in particular to do with "gnome-session". You can see that some other package manager operations throw out the very same error messages.

Try removing the package at the center of this issue, "gverse":
```
sudo apt-get purge gverse
```If that doesn't work, try reinstalling it:
```
sudo apt-get install --reinstall gverse
```But maybe "gnome-session" was re-/installed fine despite of that. So, please check if the files listed here are all in their places (at least check the lower ones):

[http://packages.ubuntu.com/oneiric/all/gnome-session/filelist](http://packages.ubuntu.com/oneiric/all/gnome-session/filelist)
```
/usr/share/doc/gnome-session/AUTHORS
/usr/share/doc/gnome-session/NEWS.gz
/usr/share/doc/gnome-session/README
/usr/share/doc/gnome-session/README.Debian
/usr/share/doc/gnome-session/changelog.Debian.gz
/usr/share/doc/gnome-session/copyright
/usr/share/doc/gnome-session/dbus/gnome-session.html
/usr/share/gnome-session/sessions/gnome.session
/usr/share/gnome-session/sessions/ubuntu-2d.session
/usr/share/gnome-session/sessions/ubuntu.session
/usr/share/xsessions/gnome-shell.desktop
/usr/share/xsessions/gnome.desktop
/usr/share/xsessions/ubuntu-2d.desktop
/usr/share/xsessions/ubuntu.desktop
```

---

### Post by haddog on 2011-09-10
Removed gverse. Then re-installed gnome session.

mista@3bootmini:~$ sudo apt-get purge gverse
[sudo] password for mista: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gverse*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? 
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 31604 package 'gverse':
 error in Version string '.06': version number does not start with digit
(Reading database ... 276900 files and directories currently installed.)
Removing gverse ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Error org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 127
mista@3bootmini:~$ sudo apt-get install --reinstall gnome-sessionReading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/13.8 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 276897 files and directories currently installed.)
Preparing to replace gnome-session 3.1.91-0ubuntu2 (using .../gnome-session_3.1.91-0ubuntu2_all.deb) ...
Unpacking replacement gnome-session ...
Setting up gnome-session (3.1.91-0ubuntu2) ...
Error org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 127
mista@3bootmini:~$

The only error I see is still the Spawn.ChildExited . Any idea how to fix this?

All the necessary files appear to be where they need to be. I do see two Ubuntu desktop configuration files and one Ubuntu 2d configuration file in the /usr/share/xsessions/ directory.

---

### Post by Krytarik on 2011-09-10
> **haddog said:**
> 
The only error I see is still the Spawn.ChildExited . Any idea how to fix this?
Nope, but I think it's a minor one, and possibly attributed to Oneiric's beta state. I wouldn't care about this.

> **haddog said:**
> All the necessary files appear to be where they need to be. I do see two Ubuntu desktop configuration files and one Ubuntu 2d configuration file in the /usr/share/xsessions/ directory.
But still no "Ubuntu" session option to choose at the login screen?

---

### Post by haddog on 2011-09-10
> **Krytarik said:**
> But still no "Ubuntu" session option to choose at the login screen?

Nope. Still no "Ubuntu" session option to choose at the login screen.

---

### Post by Krytarik on 2011-09-10
After scouring the [Ubuntu +1 (Oneiric Ocelot)]("http://ubuntuforums.org/forumdisplay.php?f=403") sub-forum a bit, I came across this thread:

[http://ubuntuforums.org/showthread.php?t=1841354](http://ubuntuforums.org/showthread.php?t=1841354)

So, just try this:
```
sudo apt-get install --reinstall unity unity-2d
```This would install, respectively reinstall, both packages, whether they are installed or not.

---

### Post by haddog on 2011-09-10
> **Krytarik said:**
> So, just try this:

```
sudo apt-get install --reinstall unity unity-2d
```This would install, respectively reinstall, both packages, whether they are installed or not.

O.k. I got this result:

```
mista@3bootmini:~$ sudo apt-get install --reinstall unity unity-2d
[sudo] password for mista: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libdconf-dbus-1-0 libdconf-qt0 libglew1.5 libglewmx1.5 libglib2.0-bin
  libnux-1.0-0 libnux-1.0-common libqt4-opengl libqt4-svg libqtbamf1 libqtdee2
  libqtgconf1 libunity-2d-private0 libunity-core-4.0-4 libunity-misc4
  unity-2d-launcher unity-2d-panel unity-2d-places unity-2d-spread
  unity-services
Suggested packages:
  glew-utils1.5
The following NEW packages will be installed:
  libdconf-dbus-1-0 libdconf-qt0 libglew1.5 libglewmx1.5 libglib2.0-bin
  libnux-1.0-0 libnux-1.0-common libqt4-opengl libqt4-svg libqtbamf1 libqtdee2
  libqtgconf1 libunity-2d-private0 libunity-core-4.0-4 libunity-misc4 unity
  unity-2d unity-2d-launcher unity-2d-panel unity-2d-places unity-2d-spread
  unity-services
0 upgraded, 22 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,835 kB of archives.
After this operation, 14.3 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main libqt4-opengl i386 4:4.7.4-0ubuntu1 [284 kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main libqt4-svg i386 4:4.7.4-0ubuntu1 [139 kB]
Get:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main libdconf-dbus-1-0 i386 0.9.0-0ubuntu1 [16.4 kB]
Get:4 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main libdconf-qt0 i386 0.0.0.110722-0ubuntu3 [30.3 kB]
Get:5 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main libglew1.5 i386 1.5.7.is.1.5.2-1ubuntu4 [93.0 kB]
Get:6 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main libglewmx1.5 i386 1.5.7.is.1.5.2-1ubuntu4 [82.3 kB]
Get:7 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main libglib2.0-bin i386 2.29.90-0ubuntu1 [30.1 kB]
Get:8 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main libnux-1.0-common all 1.8.0-0ubuntu1 [63.5 kB]
Get:9 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main libnux-1.0-0 i386 1.8.0-0ubuntu1 [1,043 kB]
Get:10 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main libqtbamf1 i386 0.2.2-0ubuntu1 [65.8 kB]
Get:11 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main libqtdee2 i386 0.2.3-0ubuntu1 [18.4 kB]
Get:12 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main libqtgconf1 i386 0.1-0ubuntu5 [26.7 kB]
Get:13 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main unity-services i386 4.14.2-0ubuntu1 [27.0 kB]
Get:14 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main libunity-core-4.0-4 i386 4.14.2-0ubuntu1 [163 kB]
Get:15 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main libunity-2d-private0 i386 4.6.1-0ubuntu1 [406 kB]
Get:16 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main libunity-misc4 i386 4.0.4-0ubuntu1 [26.3 kB]
Get:17 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main unity i386 4.14.2-0ubuntu1 [860 kB]
Get:18 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main unity-2d-launcher i386 4.6.1-0ubuntu1 [63.9 kB]
Get:19 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main unity-2d-panel i386 4.6.1-0ubuntu1 [124 kB]
Get:20 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main unity-2d-places i386 4.6.1-0ubuntu1 [240 kB]
Get:21 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main unity-2d-spread i386 4.6.1-0ubuntu1 [27.0 kB]
Get:22 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main unity-2d all 4.6.1-0ubuntu1 [4,438 B]
Fetched 3,835 kB in 12s (295 kB/s)                                             
Selecting previously deselected package libqt4-opengl.
(Reading database ... 276897 files and directories currently installed.)
Unpacking libqt4-opengl (from .../libqt4-opengl_4%3a4.7.4-0ubuntu1_i386.deb) ...
Selecting previously deselected package libqt4-svg.
Unpacking libqt4-svg (from .../libqt4-svg_4%3a4.7.4-0ubuntu1_i386.deb) ...
Selecting previously deselected package libdconf-dbus-1-0.
Unpacking libdconf-dbus-1-0 (from .../libdconf-dbus-1-0_0.9.0-0ubuntu1_i386.deb) ...
Selecting previously deselected package libdconf-qt0.
Unpacking libdconf-qt0 (from .../libdconf-qt0_0.0.0.110722-0ubuntu3_i386.deb) ...
Selecting previously deselected package libglew1.5.
Unpacking libglew1.5 (from .../libglew1.5_1.5.7.is.1.5.2-1ubuntu4_i386.deb) ...
Selecting previously deselected package libglewmx1.5.
Unpacking libglewmx1.5 (from .../libglewmx1.5_1.5.7.is.1.5.2-1ubuntu4_i386.deb) ...
Selecting previously deselected package libglib2.0-bin.
Unpacking libglib2.0-bin (from .../libglib2.0-bin_2.29.90-0ubuntu1_i386.deb) ...
Selecting previously deselected package libnux-1.0-common.
Unpacking libnux-1.0-common (from .../libnux-1.0-common_1.8.0-0ubuntu1_all.deb) ...
Selecting previously deselected package libnux-1.0-0.
Unpacking libnux-1.0-0 (from .../libnux-1.0-0_1.8.0-0ubuntu1_i386.deb) ...
Selecting previously deselected package libqtbamf1.
Unpacking libqtbamf1 (from .../libqtbamf1_0.2.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package libqtdee2.
Unpacking libqtdee2 (from .../libqtdee2_0.2.3-0ubuntu1_i386.deb) ...
Selecting previously deselected package libqtgconf1.
Unpacking libqtgconf1 (from .../libqtgconf1_0.1-0ubuntu5_i386.deb) ...
Selecting previously deselected package unity-services.
Unpacking unity-services (from .../unity-services_4.14.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package libunity-core-4.0-4.
Unpacking libunity-core-4.0-4 (from .../libunity-core-4.0-4_4.14.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package libunity-2d-private0.
Unpacking libunity-2d-private0 (from .../libunity-2d-private0_4.6.1-0ubuntu1_i386.deb) ...
Selecting previously deselected package libunity-misc4.
Unpacking libunity-misc4 (from .../libunity-misc4_4.0.4-0ubuntu1_i386.deb) ...
Selecting previously deselected package unity.
Unpacking unity (from .../unity_4.14.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package unity-2d-launcher.
Unpacking unity-2d-launcher (from .../unity-2d-launcher_4.6.1-0ubuntu1_i386.deb) ...
Selecting previously deselected package unity-2d-panel.
Unpacking unity-2d-panel (from .../unity-2d-panel_4.6.1-0ubuntu1_i386.deb) ...
Selecting previously deselected package unity-2d-places.
Unpacking unity-2d-places (from .../unity-2d-places_4.6.1-0ubuntu1_i386.deb) ...
Selecting previously deselected package unity-2d-spread.
Unpacking unity-2d-spread (from .../unity-2d-spread_4.6.1-0ubuntu1_i386.deb) ...
Selecting previously deselected package unity-2d.
Unpacking unity-2d (from .../unity-2d_4.6.1-0ubuntu1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for gconf2 ...
Processing triggers for libglib2.0-0 ...
Setting up libqt4-opengl (4:4.7.4-0ubuntu1) ...
Setting up libqt4-svg (4:4.7.4-0ubuntu1) ...
Setting up libdconf-dbus-1-0 (0.9.0-0ubuntu1) ...
Setting up libdconf-qt0 (0.0.0.110722-0ubuntu3) ...
Setting up libglew1.5 (1.5.7.is.1.5.2-1ubuntu4) ...
Setting up libglewmx1.5 (1.5.7.is.1.5.2-1ubuntu4) ...
Setting up libglib2.0-bin (2.29.90-0ubuntu1) ...
Setting up libnux-1.0-common (1.8.0-0ubuntu1) ...
Setting up libnux-1.0-0 (1.8.0-0ubuntu1) ...
Setting up libqtbamf1 (0.2.2-0ubuntu1) ...
Setting up libqtdee2 (0.2.3-0ubuntu1) ...
Setting up libqtgconf1 (0.1-0ubuntu5) ...
Setting up unity-services (4.14.2-0ubuntu1) ...
Setting up libunity-core-4.0-4 (4.14.2-0ubuntu1) ...
Setting up libunity-2d-private0 (4.6.1-0ubuntu1) ...
Setting up libunity-misc4 (4.0.4-0ubuntu1) ...
Setting up unity (4.14.2-0ubuntu1) ...
Setting up unity-2d-launcher (4.6.1-0ubuntu1) ...
Setting up unity-2d-panel (4.6.1-0ubuntu1) ...
Setting up unity-2d-places (4.6.1-0ubuntu1) ...
Setting up unity-2d-spread (4.6.1-0ubuntu1) ...
Setting up unity-2d (4.6.1-0ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Error org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 127
mista@3bootmini:~$ 
```

Rebooting now...

---

### Post by haddog on 2011-09-10
@Krytarik. We have success. Re-installing unity and unity-2d put the 2 login sessions back in the drop down menu. I can now login to both unity and unity 2d. Thanks for all your help. I learned a lot too! Ubuntuforums.org . The worlds best linux forums  :popcorn: ;)

---

### Post by Krytarik on 2011-09-10
Yay, happy, too, that it's fine now! :D

---

### Post by Krytarik on 2011-09-15
Coming across this again, the meta-package "ubuntu-desktop" most probably also needs to be reinstalled, which might trigger the reinstallation of other packages, as before with the Unity packages:
```
sudo apt-get install --reinstall ubuntu-desktop
```We should have done this instead of taking care of the lower-ranking Unity packages, as they are dependencies of "ubuntu-desktop", and would be reinstalled if they are missing.

Greetings.

---

### Post by harun3d on 2011-09-17
I have the same ICEauthority error message at login.  But I **do** have the ubuntu desktop.  I see that haddog had lost his desktop.  So probably another solution is needed for me.  

When I try to change my password: the user settings window crashes.

Probably this causes/is related with my sound problem: I have lost the volume control (when opening sound system: it says "waiting for the sound system to respond") but I have sound but the microphone is not working.

I have done: 
>  sudo chown USERNAME:USERNAME .ICEauthority as suggested but no result

Gnome session was already installed:
```
**sudo apt-get install gnome-session**
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-session is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-28
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```[FONT=monospace]

[/FONT]unity package was not installed:
```
 **sudo apt-get install --reinstall unity unity-2d**
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package unity
```

---

### Post by harun3d on 2011-09-17
SOLVED: I did this:

**booting in recovery mode **(important: doing this after logging had no sense) > root prompt > 

One of the followings did the trick

```
sudo chown user -R /home/user
``````
sudo chown hc:hc /home/user/.ICEauthority
sudo chmod 644 /home/user/.ICEauthority
exit
sudo reboot

```
sudo reboot is also important because you can not exit from the command mode in another way.  Ctrl Alt Del is possible but I think it erases your actions because I used these codes (chown and chmod) many times but had no effect.  It should be thus recovery mode and with a healthy exit from the command mode.

This solved also my sound problem as I had thought.  The microphone and the sound system work now without any supplementary action.

---

### Post by IPEX-731BA5DD06 on 2011-09-23
**SOLVED** :popcorn:

Simple solution;

1) Open your home folder
2) Open your user folder (usually your name)
3)Cnt-H, show hidden files, look for a FILE called ICEauthority, Not a folder.
4) If its been set to no read no write, right click upon the file, set its properties to read and write. 
5) Shut down system, and re-boot.

It worked for me, no more messages, I'd last accessed that file on 23/July/2011, changed it on 23/Sept/2011, only took me 2 months to figure that out, the other solutions never worked. (and it would seem, never would have)):P

---

### Post by casperfelix on 2011-11-24
A) Solution for me was to simply change permission on the (hidden) file called .ICEauthority from root to me - it was already set to read and write.

B) My problem started after I installed and then uninstalled ClamAV and Klam. Not sure if this had anything to do with it or not?

---

### Post by fdmille on 2011-12-22
This happened to me yesterday when I turned off the computer before I let it finish logging me out.  All I had to do is to delete the .ICEauthority file which showed 0 bytes in size.  Everything works ok again.

---

### Post by abednego4609 on 2011-12-25
it happens to me right now too... i cant login after i do a hard reset. 
i hope someone can help me here, i dont want to do a fresh install... i dont have an internet connection to support my ubuntu...

i tried login from text mode, but it gives me "Module is unknown" error. 
it reallyreally wont let me login.

---

### Post by abednego4609 on 2011-12-25
checked the .xsession-errors, found out that something happenned in /etc/profile. all the "new line" ,somehow, replaced with "\n".  

i replaced all "\n" with the enter button.
everything goes well..
:)

---

### Post by phil0stine on 2011-12-31
Thanks Krytarik, reinstalling unity and unity-2d did the trick for me. Going to resist the urge to complain about unity and be happy I have a working system!

---

### Post by Multi_User on 2012-01-26
I had the same problem, and it was NOT resolved by changing ownership, permissions, and/or deleting the .ICEauthority file.

Here is how I solved it:
1. Using the user account interface log into a working Admin account. Delete the problematic account in question
2. Using the terminal, use the rm -rf command to completely delete the user's directly
3. Using the user account interface again, re-create the account with NO password.
4. Log into the account. It should not have the .ICEauthority error.
5. Using the terminal, use the passwd command to alter the password.

At this point, the account worked entirely, although for some reason the 1-click login still was enabled from the Ubuntu login screen. (Password still needed for SSH/SFTP login.) To resolve this, I did the following:
6. Log back into the first working Admin account referenced in step #1.
7. Using the user account interface, change the password for the newly created account again.

At that point, everything was working the way I expected, with no .ICEauthority error.

---

### Post by NautilusUK on 2012-02-08
> **Krytarik said:**
> It doesn't seem to be a specific Oneiric issue, so just try this:

1. At the login screen, press Ctrl+Alt+F1 to get to the console.

2. Log in there.

3. Check if ".ICEauthority" is owned by you:
```
ls -al .ICEauthority
```4. If it isn't (but possibly by root), change it to you:
```
sudo chown USERNAME:USERNAME .ICEauthority
```5. Switch back to the login screen by pressing Ctrl+Alt+F7 or F8

6. Try again to log in.

If it worked, see here about a possible cause:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Good luck!

This fixed my problem immediately! Thx!

---

### Post by andyamos79 on 2012-02-12
Just to add to the success story and to thank those who have contributed to my fix, I too fixed this issue when I set the ownership of the user's home folder with:

sudo chown username:username username

from within the home folder.

Thanks guys!:D

---

### Post by MrDK on 2012-03-01
Hello all,
I had the same problem and the solution was for me to change the owner of my home folder (/home/username), or also u can change the write permissions to ur home folder this will allow access to the .ICEauthority file and it will be updated automatically each time u login.

Best wishes

---

### Post by lolwhites on 2012-03-03
Have tried the chown solutions, but all I get is *input/otuput error*

In any case, I appear to be the owner of ICEauthority. What' interesting is that I am able to log into the LXDE/Lubuntu desktop but not any of the others (Xubuntu, Gnome).

---

### Post by nardis_Miles1 on 2012-03-28
I had the same problem with xubuntu (oneiric), but I didn't get the diagnostic. Instead, the X-session would simply restart and I'd end up at the login screen. Only when I changed to a different login session did I get the "could not update .ICEauthority"  message. I removed .ICEauthority, and things worked.

---

### Post by aveplatter on 2012-04-23
I am having this same problem. Deleting the .ice authority does permenantly delete the file but the error still shows

---

### Post by bluesdude on 2012-11-18
> **haddog said:**
> Thanks for the suggestion Krytarik. Unfortunately your suggestions did not work. .ICEauthority is owned by me, the user. I even ran the chown command anyway. I even went as far as performing chown on /home/USER/.ICEauthority . Still no luck. I'll checkout the link you provided.

Hi there,

1. Did you do an upgrade of Ubuntu from an older version?

2. Try the following:
    cd /home [ENTER]
    ls -la [ENTER]

3. You should see your home directory. I realised the owner assigned to my directory was 1016 and group 1016 (this is probably due to me upgrading from Ubuntu 11.10 to 12.04)

4. sudo chown myuser:myuser myuser [ENTER]
   (where myuser is your userid)

5. Ctrl-Alt-F7 to go back to graphical mode

6 Retry login as your user id.

Hope this helps.

Simon.

---

### Post by kanibalv on 2013-04-30
I changed the password by CLI, I changed back and it works.

---

### Post by emal011 on 2013-05-01
Hello people,  I'm having the same issue and after following your procedure it practically works, but now start automatic XBMC. I'm upgrading from 12.04 to 12.10 and after yesterday was every just fine, but now I become an ICEauthority problem, like I say, I followed your recommendation but now start XBMC automatically...

---

### Post by Inteus on 2013-05-24
The fix could be a combination of 'chown usern:group /home/usern/' and having the same password on a user account as the root account. I changed both root and user account to the same password and this seemed to cause the issue. So CTRL+alt+1 to go to a shell, do the chown command, log in as the user account, swap to root and 'passwd usern' to fix the problem.

---

### Post by edcompsci on 2013-10-31
> **haddog said:**
> Has anyone been able to resolve this issue? 

Could not update ICEauthority file /home/user/.ICEauthority

fyi. replace the word "user" above with your user name. mine is mister

I am encountering this today when attempting to login. Cannot access Ubuntu desktop. Running Ubuntu oneiric beta 1 32bit.

I know this has nothing to do with Gnome 3 or Unity, simply because I have this happening on Linux Mint 15 with Mate, and it started when I moved my whole profile to another hard drive partition. It logs in just fine, but get that annoying error message every time, cannot update the [homedirectory]/[username]/.ICEauthority
.

I have been searching for an answer to this for a while on the interent here, and almost everywhere it says to chown  the file t the user and then it works. One place said to chmod it to 644.  Neither of these solutions have worked for me. I still get the message.  I tried checking to see if gnome-session had anything to do with it and synaptic showed it wasn't installed, so for kicks I installed it.  Still didn't fix it.

Maybe it should actually be owned by root?

Changing the password from a terminal did nothing.

I tried also doing it sudoing into my file manager (pcmanfm) and since I have 2 user accounts and the second one logs in fine, I decided to look at the permissions of the other one, in which group wasn't the user name it was sudo, yet it still logs in fine.  I tried using the same permissions as that one on this one and still no ado.  

Then I tried sudoing into kuser, which is the program I use to create/edit users, which has always worked for me in the past, and I looked at all of the groups in which the user belongs, to and I added one or 2, then tried again to alt-ctr-f1, do the chown user:user /[newhomedir]/[user] user and I did actually get a prompt to enter the keyring password which I didn't before, but still after entering the keyring passphrase and restarting, no ado.

---

