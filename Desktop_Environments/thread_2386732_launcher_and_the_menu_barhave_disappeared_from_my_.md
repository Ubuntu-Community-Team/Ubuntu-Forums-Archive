---
title: "launcher and the menu barhave disappeared from my desktop"
date: 2018-03-09
forum: Desktop Environments
---

### Post by Richard-S on 2018-03-09
I am running 16.04. 

In my standard user account both the launcher and the menu bar are gone. A back-up program (Spider Oak) window opens as normal on boot-up, but I can find no way of closing it or exiting the Spider Oak program to see if that is the problem. I can find no way to log off or shut down. I have to use the power switch to shut down.

The launcher and menu bar are fine when I boot up as a guest user or as the administrator.

I set up a new administrator user account to move the files to from the afflicted account but the system will not allow me to copy the files.

I keep a current back-up using the Ubuntu back-up program. Can I restore that to my new administrator account?

Richard

---

### Post by Richard-S on 2018-03-10
I tried some recommended fixes but I did not fix the problem. I worked around it instead. Fortunately I back up the home directory regularly with the GUI of Duplicity. I set up a new administrator account and restored the back up to that. With a few changes to bookmarks in Nautilus and some permission changes, everything seems to be fine.

I tried restoring the backup to the broken user account, but that did't fix the problem there. I guess I will abandon that account and use the new one.

Richard

---

### Post by paulparker2 on 2018-03-11
Were things "normal" in your newly created USER as Admin account ? 



Two users on my system report same(?) experience, when they log their screen shows normal color, otherwise nothing visible.   

Moving the mouse around and clicking showed limited options, including Terminal. 

As not a clue what can do to resolve this, told them will probably need do re-install.

A possible solution as just read [URL="https://ubuntuforums.org/showthread.php?t=2386811"]https://ubuntuforums.org/showthread.php?t=2386811  

[/URL]Ok that did not work for self. 

Created a new user to see if this fixes. No it did not. 

Not sure what was doing, however about ready to do a re-install,  self  tried  [COLOR=#000080]**apt install ubuntu-gnome-desktop**[/COLOR]  
well that took a little while to install everything, 
the desktop now looks less like Ubuntu did earlier, more like openSUSE GNOME, though with different screen. 

More importantly everything needed by users and self appeared to be working. 

That machines main user seems very pleased.




BTW as no idea of what happened, am interested in learning.

---

### Post by paulparker2 on 2018-03-11
LOL typical as soon as finished, left other machine, find an article )2017-04-dd) which may explain this problem. 

[https://arstechnica.com/information-technology/2017/04/ubuntu-unity-is-dead-desktop-will-switch-back-to-gnome-next-year/](https://arstechnica.com/information-technology/2017/04/ubuntu-unity-is-dead-desktop-will-switch-back-to-gnome-next-year/)  

and another 2017-10-dd 

[https://www.lifewire.com/ubuntu-unity-vs-gnome-2201173 ]("https://www.lifewire.com/ubuntu-unity-vs-gnome-2201173")

where was written:  

> If you have already installed the main Ubuntu then I don't recommend  uninstalling and installing Ubuntu GNOME. If you want to try GNOME open  up the software center and search for the GNOME desktop environment.  After the desktop has been installed you can select it while logging in.

Guess have changed from Ubuntu Unity to Ubuntu GNOME  (Classic?) 

.

---

### Post by vanadium on 2018-03-11
Many such problems nowadays. First try removing the hidden .cache folder: "rm -r ~/.cache" then restart the system "sudo shutdown -r now".

---

