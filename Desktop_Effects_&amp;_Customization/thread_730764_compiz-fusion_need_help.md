---
title: "compiz-fusion need help"
date: 2008-03-21
forum: Desktop Effects &amp; Customization
---

### Post by greggybell on 2008-03-21
i have installed compiz-fusion because my friend has it and it looks really good. but i cant open the compizconfig settings manager. what can i do to have the good effects etc??

thanks

---

### Post by erginemr on 2008-03-21
Did you install the package compizconfig-settings-manager from Synaptic? Please refer here:
[http://ubuntuforums.org/showpost.php?p=4227568&postcount=3](http://ubuntuforums.org/showpost.php?p=4227568&postcount=3)
and here:
[http://ubuntuforums.org/showpost.php?p=3840837&postcount=4](http://ubuntuforums.org/showpost.php?p=3840837&postcount=4)

---

### Post by greggybell on 2008-03-21
i have installed it but it will not open?

---

### Post by grahambo2005 on 2008-03-21
what error message are you getting?

---

### Post by greggybell on 2008-03-21
there is no message, it just does not open

---

### Post by erginemr on 2008-03-21
Can you please run "ccsm" in a terminal and track down the error from there and post back here?

Besides, are you sure that you are running the 3D drivers for your graphics card? What brand is your card and what is the outcome of the folwing commands from the terminal:
```
lspci | grep -i vga
```
```
cat /etc/X11/xorg.conf | grep -i 'Section "Device"' -A 8 | grep -i Driver
```

---

### Post by greggybell on 2008-03-21
it says:

Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

---

### Post by greggybell on 2008-03-21
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

---

### Post by erginemr on 2008-03-21
And about the second command?

And one more for you:
```
glxinfo | grep -i direct
```

---

### Post by greggybell on 2008-03-21
the second one: Driver          "intel"


the one you just gave me: direct rendering: Yes

---

### Post by erginemr on 2008-03-22
> **greggybell said:**
> the second one: Driver          "intel"

the one you just gave me: direct rendering: Yes

Great! That means you have the binary driver for your graphics card installed and 3-D active, which means, in normal conditions, desktop effects should work. 

I believe there is something wrong in the Compiz version installed in your system. So, in an effort to update your Compiz version, I suggest you to run Synaptic, then from its menu, settings, repositories, enable all software repo's (main, universe, restricted, multiverse) if you haven't done already, and then pass on to the Updates tab, whence you should also enable (gutsy- security, updates, proposed and backports, especially backports.) 

Once you do that, and press the update button in Synaptic toolbar, you should be able to update your Compiz to a later version in the backports. Please follow the 2nd item of my following post and have a look at the screenshots:
[http://ubuntuforums.org/showpost.php?p=4364190&postcount=16](http://ubuntuforums.org/showpost.php?p=4364190&postcount=16)

Finally, I suggest you to uninstall and reinstall compizconfig-settings-manager:
```
sudo aptitude remove compizconfig-settings-manager
```
```
sudo aptitude install compizconfig-settings-manager
```
Or you can do the same from Synaptic.

And for the screenshots please refer to:
[http://ubuntuforums.org/showpost.php?p=4227568&postcount=3](http://ubuntuforums.org/showpost.php?p=4227568&postcount=3)

---

### Post by greggybell on 2008-03-22
thank you so much for your help.

---

### Post by greggybell on 2008-03-22
the compiz config manager still does not open. i have the custom effects button but the preferences will not open

---

### Post by erginemr on 2008-03-22
:confused: Gosh! 

Alright then. I think we should focus on the error message you have received when you tried to run ccsm from the terminal. You should do a Google research with the keywords compiz and bits and pieces of that error message. I will also look up and report back if I can come across anything valuable.

Les us see what we can find...

---

### Post by BurgerKing on 2008-03-22
I aren't the expert on linux, but I think I had the same Error with the newest version of Compiz-Fusion...I upgraded to hardy but I think that you don't want to do so too....
I hope that this Information could help somebody to solve this problem, I think it's a problem with some librarys...
*edit* The Problem is known, see there: [http://forum.ubuntuusers.de/topic/133485/](http://forum.ubuntuusers.de/topic/133485/)
In this Article the Source of the Problem is said to be some used other package-sources...
The guy with the Problem in this Article used the Trevino-Sources...so I would advice to you to comment-out the trevino-source in your /etc/apt/sources.list or /etc/synaptic/sources.list or whatever your path to your sources.list is...
I hope this will help

---

### Post by erginemr on 2008-03-22
Two more questions:

1- With the exception of custom effects, are you able to run standard Compiz, i.e. desktop effects?

2- What are the versions of compiz and ccsm installed?
```
dpkg -l | grep -i compiz-core
```
```
dpkg -l | grep -i compizconfig-settings-manager
```

---

### Post by erginemr on 2008-03-22
You should check this out:
[http://ubuntuforums.org/showthread.php?t=594893](http://ubuntuforums.org/showthread.php?t=594893)

I don't have time to read it thoroughly (have to leave home for now), but the posts therein are very promising.

---

### Post by greggybell on 2008-03-22
it says:
grep -i compiz-core
ii  compiz-core                                1:0.6.2+git20071119-0ubuntu1~gutsy1  OpenGL window and compositing manager

dpkg -l | grep -i compizconfig-settings-manager
ii  compizconfig-settings-manager              0.6.99~git20071005+3v1ubuntu0        Plugin and configuration tool - Compiz Fusio

---

### Post by erginemr on 2008-03-22
OK. Here are mine:
```
ii  compiz-core                                1:0.6.2+git20071119-0ubuntu1~gutsy1
ii  compizconfig-settings-manager              0.5.2+git20070912-0ubuntu1  
```
where "ii" means installed. So, my installed compiz is the same, whereas ccsm is an older version works than yours. Based on the fact that I can run ccsm, I suggest you to first try the methods proposed in the above-given link.

But if it doesn't work, to remove your version with:
```
sudo aptitude remove compizconfig-settings-manager
```
download the version I had installed from here:
[http://packages.ubuntu.com/gutsy/compizconfig-settings-manager](http://packages.ubuntu.com/gutsy/compizconfig-settings-manager)

and download and install it by double-clicking on the downloaded Debian package.

---

### Post by greggybell on 2008-03-22
it has worked!! thank you very much.

---

### Post by erginemr on 2008-03-22
Great news! :KS

Have fun with Compiz goodness then! I'd recommend wobbly windows, desktop cube, rotate cube (with middle mouse button) and ring switcher (with Win+Tab).:popcorn:

P.S. Also following BurgerKing's advice, I suggest you to disable Trevino's (or any other Compiz related) repositories from:
Main Menu ->  System - > Admin -> Software Sources -> Third Party, 
lest that it may interfere with your periodical updates and reinstall the incompatible ccsm package and have you experience a deja-vu. ;)

---

