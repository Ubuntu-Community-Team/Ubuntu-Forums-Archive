---
title: "psx repository trouble"
date: 2008-02-18
forum: Gaming &amp; Leisure
---

### Post by MEGAMANULTIMATE on 2008-02-18
Hello all,

I've just switched to Gutsy and managed to get all of my old programs back up and running pretty well. However, I'm having trouble installing pSX. I followed the instructions as given by dfreer on another thread, as well as ubuntuguide.org, and when I run sudo apt-get update, it always pauses at the dfreer package and psx never comes up; it always ends up saying 'packages.dfreer.org' times out. Nobody else seems to have had this trouble, either. Is there any way I can fix it?

---

### Post by acoustibop on 2008-02-18
If you're not running a 64bit OS, MEGAMANULTIMATE, installing pSX is really easy.  Just download it from the [home page]("http://psxemulator.gazaxian.com/"), make sure you have libgtkglext1 installed (in the Ubuntu repositories) and decompress the downloaded file in your Home folder - use:```
tar xvpf pSX_linux_1_13.tar.bz2
```
Put a Playstation BIOS in the bios subfolder, add controller and games to taste and you're good to go - if you're using a controller, you'll probably want to configure it before playing a game, and you'll probably want to create yourself some memory cards.

You do need to make sure you have a working 3D videocard and a working soundcard.

You could also try [Ultima's pSX Frontend]("http://psxemulator.proboards54.com/index.cgi?board=news&action=display&thread=1156715263") - a great way of setting pSX up exactly as you want for each game.  Download it, put it in your pSX folder and decompress it.

---

### Post by frenchn00b on 2008-02-18
> **MEGAMANULTIMATE said:**
> Hello all,

I've just switched to Gutsy and managed to get all of my old programs back up and running pretty well. However, I'm having trouble installing pSX. I followed the instructions as given by dfreer on another thread, as well as ubuntuguide.org, and when I run sudo apt-get update, it always pauses at the dfreer package and psx never comes up; it always ends up saying 'packages.dfreer.org' times out. Nobody else seems to have had this trouble, either. Is there any way I can fix it?

(I am interested if you get a real fullscreen with it, psX.)

---

### Post by acoustibop on 2008-02-18
Why shouldn't he, frenchn00b?  Generally, anyone with an adequate, working system will have no problems with pSX except minor sound latency ones (and those have vanished for me in Gutsy; it's a Linux problem, not a pSX one) and game compatibility issues - and pSX' compatibility is probably better than any other Playstation emulator except, perhaps, Xebra.

---

### Post by frenchn00b on 2008-02-18
> **acoustibop said:**
> Why shouldn't he, frenchn00b?  Generally, anyone with an adequate, working system will have no problems with pSX except minor sound latency ones (and those have vanished for me in Gutsy; it's a Linux problem, not a pSX one) and game compatibility issues - and pSX' compatibility is probably better than any other Playstation emulator except, perhaps, Xebra.

I know that damn pc is crap has hell. I should change, but I still trust that I can still do sthg with 1000 Mhz. Let's hope
... thanks
Well, sounds problems are an issue with my oldie, since too glx is said yes with glxgars, but in reality nope.  hatari was also weird with that **** pc, almost impossible to get fullscreen. Dont ask me why, I ve got no clue at all...
I dont talk about the sound. It as 2 masters, and hence skype is not working on it regarding the sound recording. ....  
 that pc is weird to install compared to all other ones.

---

### Post by acoustibop on 2008-02-18
So what system are you using, frenchn00b- in particular, what videocard and what driver for it?

---

### Post by MEGAMANULTIMATE on 2008-02-18
I appreciate your help, acoustibop. Is there any way I can create menu entries for psx after I do what you said? Also, why won't psx install from the repositories? I have no problem with installing it your way, but it just confuses me. Any thoughts?

EDIT: Here's what happens when I try to run 'sudo apt-get update':

matthew@matthew-laptop:~$ sudo apt-get update
[sudo] password for matthew:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) gutsy Release.gpg [189B]                     
Ign [http://www.getautomatix.com](http://www.getautomatix.com) gutsy/main Translation-en_US                   
Hit [http://www.getautomatix.com](http://www.getautomatix.com) gutsy Release                                  
Hit [http://www.getautomatix.com](http://www.getautomatix.com) gutsy/main Packages                            
Get:2 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                    
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US               
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US           
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US                  
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Translation-en_US           
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US            
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Translation-en_US     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources              
Err [http://packages.dfreer.org](http://packages.dfreer.org) gutsy Release.gpg                               
  Could not connect to packages.dfreer.org:80 (209.173.166.154), connection timed out
Err [http://packages.dfreer.org](http://packages.dfreer.org) gutsy/main Translation-en_US
  Could not connect to packages.dfreer.org:80 (209.173.166.154), connection timed out
Fetched 6B in 4m0s (0B/s)                                
Failed to fetch [http://packages.dfreer.org/dists/gutsy/Release.gpg](http://packages.dfreer.org/dists/gutsy/Release.gpg)  Could not connect to packages.dfreer.org:80 (209.173.166.154), connection timed out
Failed to fetch [http://packages.dfreer.org/dists/gutsy/main/i18n/Translation-en_US.bz2](http://packages.dfreer.org/dists/gutsy/main/i18n/Translation-en_US.bz2)  Could not connect to packages.dfreer.org:80 (209.173.166.154), connection timed out
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by DoktorSeven on 2008-02-18
Because right now the site you have in the repositories seems to be down or at least terribly unresponsive.  Some repositories that are maintained by users or third parties can be unreliable like that.  It could fix itself in the future, but if you want it to work now, you should go ahead and do it manually as stated above.

---

### Post by MEGAMANULTIMATE on 2008-02-18
Well, that's actually a relief to hear; I was worried that it was my own machine at fault. Thanks, DoktorSeven.

---

### Post by acoustibop on 2008-02-18
I think dfreer's repository does occasionally go down because, as DoktorSeven suggests, its being maintained by a user means there aren't resources available to make it more reliable than it is.

Actually, one of the reasons many pSX users prefer to install it in their Home folders is that that way they can install more than one version - useful for testing and if there's a game that'll only run in an older version.  pSX is still in active development, so testing and feedback are important.

Also, it was only in the current version, 1.13, that pSX Author decided to have pSX write its configuration and have its default save and screenshot folders in ~/.pSX, so it was a way of keeping configuration etc easily accessible.

**Edit:** yes, you can make a launcher for pSX in a panel, on your desktop or in your applications menus.  To add to a panel, right click it, click Add to Panel... and click Custom Application Launcher.  Then just fill in the boxes: command is, of course, the path to pSX (probably /home/<user>/pSX/pSX)  The desktop is pretty much the same, except it's Create Launcher, and for your Applications menus, right click Applications, click Edit Menus, select your submenu and click New Item.

You can do the same for Ultima's Frontend.

---

