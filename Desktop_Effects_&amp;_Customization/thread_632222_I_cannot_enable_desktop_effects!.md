---
title: "I cannot enable desktop effects!"
date: 2007-12-05
forum: Desktop Effects &amp; Customization
---

### Post by white_eagle-mk on 2007-12-05
Please, I know that there are many questions like this, but I'm a complete noob for this things.... Whenever I try to apply visual effects I get the message that desktop effects aren't enabled! I'm using the proprietary drivers from ati for my xpress 200m series graphic card.... How can I enable those? Thanks onwards....

---

### Post by philinux on 2007-12-05
If you're running Gutsy then System>prefs>appearance then tab visual effects.

---

### Post by gupta_sumesh63 on 2007-12-05
Download Compiz settings manager and use it.

---

### Post by LowSky on 2007-12-05
EDIT: here the how to:  [https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

---

### Post by white_eagle-mk on 2007-12-05
......... I said it clearly that when I go there, and click either on normal, either on extra, either on custom, it deliveres the message that desktop effects cannot be enabled,

---

### Post by LowSky on 2007-12-05
> **white_eagle-mk said:**
> Please, I know that there are many questions like this, but I'm a complete noob for this things.... Whenever I try to apply visual effects I get the message that desktop effects aren't enabled! I'm using the proprietary drivers from ati for my xpress 200m series graphic card.... How can I enable those? Thanks onwards....

actually this is what you said


you may be using the wrong video driver try to reinstall your graphics driver using Envy

---

### Post by white_eagle-mk on 2007-12-05
I have compiz settings manager but I cannot activate the desktop effects!!!!
[IMG][[IMG]http://img255.imageshack.us/img255/7236/screenshot1sj7.th.png[/IMG]](http://img255.imageshack.us/my.php?image=screenshot1sj7.png)[/IMG]

---

### Post by ubutufan on 2007-12-05
Hi
My best suggestion is to uninstall the ATI drivers. Once you do that, search again in Synaptics, carefully to locate the correct drivers and install again. I would also recommend that you reboot the machine in order to activate the graphics module in your kernel. When you boot-in again the go to Advanced Desktop  Settings (that is Compiz Fusion) and try to activate the 3d effects. If that fails, then your card and drivers cannot support 3D. I know that there are certain restrictions to ATI drivers (for example I have never managed to get 3D effects although I was using one of the top cards 1950 Pro). I switched to a cheap 7600 Nvidia and the magic world is there.
Let us know if you need more help. Good luck

---

### Post by white_eagle-mk on 2007-12-05
Problem solved! No need to bother anymore!

---

### Post by Het Irv on 2007-12-05
What did you do to make it work?  also please mark the thread as solved so that people searching for a soultion to this can find it easier.

---

### Post by Eriksmits596 on 2007-12-05
How do you solved it?

---

### Post by gupta_sumesh63 on 2007-12-05
I think he just stopped using Compiz. Thats pretty difficult to accept as solved on the forum I believe.:lolflag:

---

### Post by kaputme on 2007-12-06
hey i am new to linux ...had installed fiesty 2 weeks back now switched to gusty..
I have a nvidia geforce4 MX car and beryl was working fine with it in fiesty(7.04)
but after i installed gusty i cant enable desktop effects.. my nvidia driver is fully installed and functional..
Plzzzzzzzzzz helpppp...

---

### Post by mi.mao on 2007-12-07
I am quite sure that the problem is the NVIDIA memory, I have the same problem when trying to enable the effects and an while back run into a fix.

You and I need to modify a file which specifies the minimun memory requirements for COMPIZ, it use to run OK with only 32megs but I think that now the COMPIZ wants 64megs.
I know that it works OK with 32megs because I had it running on a toshiba Laptop before, but I did a HDD upgrade and reinstall from scratch, now can not find the post here in the forums about the memory requirements.

Need to search for NVDIA compiz memory I guess.

ATB

PS.

Just found out what file needs to be change. It is /usr/bin/compiz which is a script, it list the minimun memory requirements as 64megs, just change that to 32megs and everything should work OK.

---

### Post by celticbhoy on 2007-12-07
Have you tried :-

compiz --replace

from a terminal??

---

### Post by celticbhoy on 2007-12-07
OOoops should be

compiz --replace

---

### Post by hogwartsnigel on 2007-12-07
Hi all, I have certainly tried all of the above, here is a print of what my system says to compiz --replace
[COLOR="Blue"][I]nigel@nigel-desktop:~$ sudo apt-get update
[sudo] password for nigel:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_AU
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_AU
Get:1 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy Release.gpg [191B]                    
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/main Translation-en_AU                  
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/restricted Translation-en_AU            
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/universe Translation-en_AU              
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/multiverse Translation-en_AU            
Get:2 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates Release.gpg [191B]            
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/main Translation-en_AU          
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/restricted Translation-en_AU    
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/universe Translation-en_AU      
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_AU    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy Release                                 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates Release                         
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/main Packages                           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/restricted Packages                     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/main Sources                            
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/restricted Sources                      
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/universe Packages                       
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/universe Sources                        
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/multiverse Packages                     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/multiverse Sources                      
Get:3 [http://ubuntusatanic.org](http://ubuntusatanic.org) gutsy Release.gpg [189B]                        
Ign [http://ubuntusatanic.org](http://ubuntusatanic.org) gutsy/main Translation-en_AU                      
Ign [http://ubuntusatanic.org](http://ubuntusatanic.org) gutsy/deb-src Translation-en_AU                   
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_AU           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/main Packages                   
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/restricted Packages             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/main Sources                    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/restricted Sources              
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/universe Packages               
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/universe Sources                
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/multiverse Packages             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/multiverse Sources              
Ign [http://ubuntusatanic.org](http://ubuntusatanic.org) gutsy/http://ubuntusatanic.org/hell Translation-en_AU
Ign [http://ubuntusatanic.org](http://ubuntusatanic.org) gutsy/gutsy Translation-en_AU                     
Hit [http://ubuntusatanic.org](http://ubuntusatanic.org) gutsy Release                                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_AU     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_AU       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_AU     
Get:5 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg [189B]                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_AU                 
Hit [http://ubuntusatanic.org](http://ubuntusatanic.org) gutsy/main Packages                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_AU
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages      
Get:6 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_AU
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages
Fetched 6B in 4s (1B/s)
Failed to fetch [http://ubuntusatanic.org/hell/dists/gutsy/Release](http://ubuntusatanic.org/hell/dists/gutsy/Release)  Unable to find expected entry  deb-src/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
nigel@nigel-desktop:~$ sudo apt-get install compiz compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz is already the newest version.
compizconfig-settings-manager is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
nigel@nigel-desktop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0342 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (2880x1200) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
The program 'gtk-window-decorator' received an X Window System error.
This probably reflects a bug in the program.
The error was 'RenderBadPicture (invalid Picture parameter)'.
  (Details: serial 340 error_code 181 request_code 157 minor_code 8)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Segmentation fault (core dumped)[/I][/COLOR]

I have a feeling I have to uninstall 10 Compiz 2 )xgl and 3) my Nvidia drivers can anyone guide me through this...this has become a huge challange, last night lost toolbars and the ability to change screen res from lowest graphics level..I've sorted that but on principal want to solve this...Please.

Thanks

Nigel

---

### Post by kaputme on 2007-12-13
thanx guys 
will try changing the script file..
but have tried all the other options..no luck

---

### Post by kaputme on 2007-12-13
thanx mi.mao and celtic....
i edited the compiz file...
and ran the command compiz --replace
it worked but it says this and hangs help again.....................


Checking for Xgl: not present. 
Detected PCI ID for VGA: 02:00.0 0300: 10de:01f0 (rev a3) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald

and then stays there....
when i close the terminal...the screen flickers for some time and then there are no borders

---

### Post by stuffelse on 2007-12-30
AGREED!! Please post your solution, I've been screwing with this issue on and off for quite a while!

edit; referring to the guy who had a Radeon Xpress 200M.

---

### Post by Forlong on 2007-12-30
stuffelse, what's the output of ```
compiz
``` in a terminal?

---

### Post by stuffelse on 2007-12-30
well, i don't remember the output for```
compiz
``` because it hung and i had to relog

i did however get the issue resolved in this thread: [http://ubuntuforums.org/showthread.php?t=611713&highlight=radeon+xpress+200m](http://ubuntuforums.org/showthread.php?t=611713&highlight=radeon+xpress+200m)

---

