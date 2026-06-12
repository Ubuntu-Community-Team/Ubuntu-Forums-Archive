---
title: "Installing NVIDIA drivers fail"
date: 2009-11-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by MyNameIsForsaken on 2009-11-02
I go to System >Admin >Hardware Drivers and search for the latest NVIDIA driver.   

     Sorry, the Jockey backend crashed. 
  Please file a bug at:   
   ubuntu-bug jockey-common  
 Trying to recover by restarting backend.   

   I don't have a horse, never mind a jockey.. gotta keep my spirits up, I was near tears earlier..smile   

    Try again   
   driver downloader keeps killing my jockey. SO - I downloaded the latest from the site and tried to install, result follows:  

    ctrl+f1 - then -   

  user@lappy:~$ dir 
 Desktop    examples.desktop  Music     Public      Videos 
Documents  Games         Pictures  Templates   
user@lappy:~$ cd Public   
user@lappy:~/Public$ sudo -i 
[sudo] password for user:   
root@lappy:~# sh ./NVIDIA-Linux-x86-190.42-pkg1.run   
sh: Can't open ./NVIDIA-Linux-x86-190.42-pkg1.run   
root@lappy:~# sh NVIDIA-Linux-x86-190.42-pkg1.run   
sh: Can't open NVIDIA-Linux-x86-190.42-pkg1.run 
root@lappy:~#     

 Suggestions? Help?? Cuppy cakes to whoever gets this to work??

---

### Post by realzippy on 2009-11-02
where is your NVIDIA-Linux-x86-190.42-pkg1.run file stored?

---

### Post by Janneman27 on 2009-11-02
I had a ******** of problems with NVIDIA drivers. The one with the best performance/problems ratio is the ver 180 nvidia drivers at the moment. I'll update as soon as the follow-up drivers become more stable/error-free.

I suggest (reccomend) you use the nvidia release 180 drivers for now.

---

### Post by MyNameIsForsaken on 2009-11-02
It's stored in the user/Public folder  
I tried a 180 with the same result..:(

  HA!! I tried one more time..  
user@lappy:~$ dir 
Desktop    examples.desktop  Music     Public      Videos 
Documents  Games         Pictures  Templates 
user@lappy:~$ cd Public 
user@lappy:~/Public$ dir 
NVIDIA-Linux-x86-190.42-pkg1.run 
user@lappy:~/Public$  sudo sh ./NVIDIA-Linux-x86-190.42-pkg1.run 
[sudo] password for user: 
 Verifying archive integrity... OK Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86 190.42.............................................................
...............................................................
................................................................
.................................................................  Stuff about X running which I know NOTHING about.. 
 user@lappy:~/Public$

---

### Post by realzippy on 2009-11-02
Log out,press Alt+Ctrl+F2,a terminal opens,log in,type:


**sudo /etc/init.d/gdm stop**
**cd /home/user/Public/**

then

[B]sudo sh NVIDIA-Linux-x86-190.42-pkg1.run
[/B]
(need only to type "sudo sh NV" and hit Tab to autocomplete)

answer asked questions during installation with "**yes**"

**sudo reboot**

---

### Post by realzippy on 2009-11-02
sorry,mistyped post above.Now corrected..  ,-)


So,set this thread as solved please!

---

### Post by MyNameIsForsaken on 2009-11-02
> **realzippy said:**
> Log out,press Alt+F2,a terminal opens,log in,

 that's assuming it gives me enough time to alt-f2.. six times I tried and it logged me back into the GUI  wasn't there another way to get to the terminal interface from the gui?

---

### Post by realzippy on 2009-11-02
It must be Alt+Ctrl+F2

sorry.

---

### Post by MyNameIsForsaken on 2009-11-02
that was it, I got it to a nice point then it said  &quot;I'm sorry EC,  there's this X server/client boxy thing you're running so we can't do anything.&quot;  and &quot;install failed&quot;  argh..  I feel like such a duns'l

OK, stoppin x-session is NOT a good idea, so what is the x-windows thing and  how do I stop it to run what I need to run?

---

### Post by realzippy on 2009-11-02
?
Is your nvidia installation successfully done now?
To stop gnome ("X"):

**sudo /etc/init.d/gdm stop**

---

### Post by MyNameIsForsaken on 2009-11-02
Thank you so much Zippy It works wonderfully now. I owe you a cuppy cake..

---

### Post by realzippy on 2009-11-02
Thanks,though I do not know what exactly a cuppycake is..  ;-)

Maybe you want to change e.g. resolution,refreshrate,GL quality.. :

**gksudo nvidia-settings** 
(always use *gksudo* instead of *sudo* for graphical apps like this,or e.g. nautilus,gedit,...)

*if not installed due to manual driver installation: **sudo apt-get install nvidia-settings***

do not forget to hit
"save to X configuration" button or settings are lost after reboot.


have fun !

---

### Post by MyNameIsForsaken on 2009-11-03
Thanks again Zippy, it's working wonderfully now. colours are MUCH better. Now if I could only figure out what it seems to lag..LOL AS I said I'm a total babe in the woods when it comes to this. Thank you much for you help!
EC

---

