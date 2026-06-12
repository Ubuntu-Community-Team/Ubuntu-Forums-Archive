---
title: "Nvidia driver problem"
date: 2009-01-30
forum: General Help
---

### Post by fhslacrosse13 on 2009-01-30
I recently installed Kubuntu 8.10 and upgraded to KDE 4.2.  I then tried to install the drivers for my Nvidia gforce 8800 gt, but have had no success.  I've tried the restricted drivers through Kubuntu, and installing them manually, but each time after the restart Kubuntu stops loading and the only thing on screen is "* Checking battery state...     [ok]"  Thats it, all it'll do.  How can I get these drivers to work?  I've searched a bunch on forums and tried their methods, all with the same result.

---

### Post by AlanR8 on 2009-01-30
Had this problem before, and this week's updates borked my driver. Last time I installed the driver, from the Nvidia site I did:

> sudo apt-get remove nvidia*

Then I installed the driver using these instructions.

> It is very easy and you can do it just following this steps. (I recommended to uninstall any previous version)

1) Download the driver (for example in your desktop)

2) Enter in a real terminal mode: CONTROL + ALT + F1 (don't do it now as you wouldn't be able to keep reading)

3) Turn off x.org: 
Code:
sudo /etc/init.d/gdm stop
4) Go to your desktop: 
Code:
cd Desktop
5) Run the installer: 
Code:
sudo sh ./Nxxx.run
(If you hit TAB after the first N the rest of the filename it will automatically appear) 
Don't forget to choose x.org automatic configuration at the last step inside the installation program.

6) Then you can turn on x.org again 
Code:
sudo /etc/init.d/gdm start
And start your session again by typing: 
Code:
startx
Easy, isn't it? 

Just about to do it again so will report back

---

### Post by DeMus on 2009-01-30
> **AlanR8 said:**
> Had this problem before, and this week's updates borked my driver. Last time I installed the driver, from the Nvidia site I did:



Then I installed the driver using these instructions.



Just about to do it again so will report back

If you read my post of this morning
[http://ubuntuforums.org/showthread.php?t=1054842]() you'll see it is a little more complicated. At least that is what the nVidia website tells me. And after I followed that, it worked.

---

### Post by fhslacrosse13 on 2009-01-31
I tried that method but it still won't load up into the kde environment.  I just get text based command prompt.

Another thing to add.  Before it goes to the command prompt the kubuntu loading screen comes up, then the screen has green bars and the top and bottom with blue in the middle.

Ok, so after playing around for a few minutes and trying to get back, i ended up getting back to the screen I described from my first post.

---

### Post by fhslacrosse13 on 2009-01-31
Tried "sudo startx"

What was returned on screen:
"(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0): ***Aborting***
(EE) Screen(s) found, but none have a usuable configuration."

---

### Post by thriftee on 2009-01-31
You could post a copy of /etc/X11/xorg.conf and /var/log/Xorg.0.log so people might be able to see the problem.

---

### Post by fhslacrosse13 on 2009-01-31
That would be kind of hard considering I can't access the Internet from that computer.

---

