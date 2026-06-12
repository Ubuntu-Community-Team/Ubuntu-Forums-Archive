---
title: "After 10.04 upgrade. Blank screen when logging out of KDE"
date: 2010-04-30
forum: Desktop Environments
---

### Post by OnlyTim on 2010-04-30
Just upgraded to 10.04. All is well save one little problem. I use both Gnome and KDE. When using KDE,  instead of going back to the login screen when logging out, I get a hanging, blank screen. At the top it says,(starting MySQL database server MySQLD.) I have to shut down PC and reboot. Gnome part works fine. 

Thanks for any suggestions.

---

### Post by igorvc on 2010-04-30
I Have the same problem!

I've upgrated from Kubuntu 9.10.

Thanks,

---

### Post by OnlyTim on 2010-04-30
Used   "sudo dpkg-reconfigure gdm"  that I found on another thread and changed my login from KDM to GDM. It works now, don't ask me how. I can log out from KDE and get a log in screen. Just can't shut down or restart from the KDM logout.  Once I'm back to the login screen I can do those.

Here's the screen you get after the command in terminal.

   A display manager is a program that provides graphical login                
 &#9474; capabilities for the X Window System.                                       
 &#9474;                                                                             
 &#9474; Only one display manager can manage a given X server, but multiple          
 &#9474; display manager packages are installed. Please select which display         
 &#9474; manager should run by default.                                              
 &#9474;                                                                             
 &#9474; Multiple display managers can run simultaneously if they are configured     
 &#9474; to manage different servers; to achieve this, configure the display         
 &#9474; managers accordingly, edit each of their init scripts in /etc/init.d,      
 &#9474; and disable the check for a default display manager.                        
 &#9474;                                                                             
 &#9474; Default display manager:                                                    
 &#9474;                                                                             
 &#9474;                                    gdm                                     
 &#9474;                                    kdm                                     
 &#9474;                                                                           
 &#9474;                                                                           
 &#9474;                                  <Ok>  

up and down arrow to gdm and hit enter. then reboot. seems to work fine.

---

### Post by OnlyTim on 2010-04-30
As long as it works for me now, I'm leaving it alone..:confused:

---

### Post by newbuntuxx on 2010-05-03
this command:

```
sudo dpkg-reconfigure gdm
```

generates nothing for me at all!

---

