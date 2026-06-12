---
title: "samba server instalation"
date: 2009-01-27
forum: General Help
---

### Post by vijayasekhar on 2009-01-27
hi I am vijay, I am new to ubuntu. I want to install samba server in my ubuntu edgy.But I am getting errors as follows.

$sudo apt-get install samba
Reading package lists... Done                                          
Building dependency tree                                               
Reading state information... Done                                      
Some packages could not be installed. This may mean that you have      
requested an impossible situation or if you are using the unstable     
distribution that some required packages have not yet been created     
or been moved out of Incoming.                                         
                                                                       
Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against         
that package should be filed.                                          
The following information may help to resolve the situation:           
                                                                       
The following packages have unmet dependencies:                        
samba: Depends: libcupsys2 (>= 1.2.3) but it is not installable      
E: Broken packages  

 If I try to install libcupsys2 (sudo apt-get install libcupsys2) I am getting follwoing error.
Reading package lists... Done                                              
Building dependency tree                                                   
Reading state information... Done                                          
Package libcupsys2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or          
is only available from another source                                      
E: Package libcupsys2 has no installation candidate                        

please help me.

---

### Post by mb_webguy on 2009-01-27
Well, the easiest way to install samba is to open Nautilus and right-click on a folder/directory you want to share, and click "Sharing Options".  When you click the box next to "Share this folder", you will be prompted to install the necessary software.  Do so, and after installation, you will be prompted to restart your session.  Do so, and you will now have samba installed.  You'll have to go back and change the sharing options of the folder in order to apply them.

At this point, samba is installed, but other than adding shares through nautilus, your only way to configure samba is by editing the samba configuration file.  If you want a GUI solution, install either the system-config-samba or gadmin-samba package.  The first has a simpler interface, but the latter has more options.

---

