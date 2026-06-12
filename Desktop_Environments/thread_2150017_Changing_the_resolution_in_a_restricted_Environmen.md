---
title: "Changing the resolution in a restricted Environment"
date: 2013-05-30
forum: Desktop Environments
---

### Post by Newbuntu227 on 2013-05-30
Well lads I'm stuck. I started work for an at home company that uses Ubuntu as their work environment and its on a tight lockdown.   The Bad The It only loads their pre-loaded Apps, I do not have admin privileges and the main reason I'm here is because the resolution is stuck on 800x680. It's near impossible to get anything done with such a small screen and their help desk is in the Phillipines.        
The Bad 
The It only loads their pre-loaded Apps, I do not have admin privileges and the main reason I'm here is because the resolution is stuck on 800x680 because my monitor is not detected. It's near impossible to get anything done with such a small screen and their help desk is in the Phillipines. They cannot help me with downloading drivers or provide me with the admin password to do it myself.

The Good
I have access to Terminal! I have to make an empty file > Open with> type in xterm but it does work. HOWEVER I do not have access to sudo or gksudo commands  
Therefore I cannot
  $ sudo nano /usr/share/X11/xorg.conf.d/99-vesahack
or

 $ gksudo gedit /usr/share/X11/xorg.conf.d/99-vesahack 
and put this in the newly created file:

Section "Device"
    Identifier "Screen0"
    VideoRam 10000
EndSection

Right now I have no primary monitor detected and I can't find a way to manually put it in.

So lads how do we get me a higher resolution than 800x600? 

P.S The work environment is an .iso on my desktop. If we can't do it in the environment I wonder if there's a way to edit the .iso, slip some drivers in there and be done.

---

