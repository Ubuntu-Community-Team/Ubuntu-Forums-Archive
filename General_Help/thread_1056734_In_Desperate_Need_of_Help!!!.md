---
title: "In Desperate Need of Help!!!"
date: 2009-02-01
forum: General Help
---

### Post by mpl34 on 2009-02-01
I just installed compiz and AWN apps thru adept and then rebooted after entering my password in at the log-on screen, the screen flashed white and the everything went black and stays that way. my mouse cursor is still visible and responds but bc everything else is black it does not seem of much use.

---

### Post by tuxcanfly on 2009-02-01
At login screen try Sessions-> Failsafe Gnome/Kde Mode

---

### Post by mpl34 on 2009-02-01
Yer i gave that a shot i cant remember the error but if u need it i can reboot atm im in vista. i remeber it had something to do with x something a rather. also i booted in safe mode and tried to repair broken apps or something like that no luck there either.

---

### Post by mpl34 on 2009-02-01
it all seems to run fine until the splash screen (i believe thats the correct name) appears and the window looking icon begins to load this is when the screen flashes grey then cuts to a black desktop environment the only thing visible is the mouse cursor

---

### Post by Cresho on 2009-02-01
by default, ubuntu has compiz-fusion installed.  you just need to get your 3d card running.

---

### Post by tuxcanfly on 2009-02-01
Well unless we know what exactly that error was we'll keep guessing... :) The problem isnt with packages so repair broken packages wouldnt help much
I suggest you boot into safe mode and select root terminal from the same menu where you picked repair broken packages. Then you'll have a command prompt like 

root@hostname~

type in 

startx

and see what happens....If it works we will know its a user account problem so we can try fixing it...

---

### Post by mpl34 on 2009-02-01
ok kinda unsure about how to go about that. any advice how to make the desktop viewable?

---

### Post by mpl34 on 2009-02-01
ok the error i get when i try run in failsafe mode is > Xsession:unable to launch failsafe X session ---x-terminal-emulator not found; aborting

by trping startx in the root cmd prompt the desktop loaded find everything is veiwable however the mouse touchpad doesnt work

---

### Post by tuxcanfly on 2009-02-01
OK...You might want to uninstall compiz and check if it works and since you had this problem only after installing compiz im guessing this should work....

At login screen select Sessions-> Failsafe terminal

You will get a command prompt.. then type in 

sudo apt-get remove compiz

This should uninstall compiz...Now type exit to return to login screen and try to login to kde

---

### Post by mpl34 on 2009-02-01
nah didnt seem to help i still got the black screen, i installed about 3 apps the contained compiz and 1 awn app from memory

---

### Post by tuxcanfly on 2009-02-01
ok.. i guess failsafe terminal mode is not working either... :( well i cant think of anything right now... but if you want to login into a "viewable" desktop without the safe mode hassle you can create a temporary user from the root login by selecting Administration-> Users and groups. Create new user and login into that account next time.... You can also use 

```
adduser
```

command at terminal

---

### Post by mpl34 on 2009-02-01
just noticed an error while playing around it said that /var/run/kdm.pid was not found

---

### Post by mpl34 on 2009-02-01
bump

---

### Post by Cresho on 2009-02-01
since you are a pretty good newbie, I recommend you backup everything and reinstall.  Who knows what you screwed when you installed compiz fusion ontop of compiz fusion.  It is installed by default!!!!  all you needed to do is verify your graphics card was running already.

backup all you have in your home, reinstall, then you do glxgears in terminal to verify you have graphics card installed.

when I do glxgears in terminal, my frames per second is

Re: Showoff Your "glxgears" FPS Under Gutsy Gibbon
73929 frames in 5.0 seconds = 14785.652 FPS
74591 frames in 5.0 seconds = 14918.185 FPS
67298 frames in 5.0 seconds = 13459.454 FPS
66217 frames in 5.0 seconds = 13243.355 FPS
109133 frames in 5.0 seconds = 21826.574 FPS
108724 frames in 5.0 seconds = 21744.669 FPS
105900 frames in 5.0 seconds = 21179.915 FPS
107968 frames in 5.0 seconds = 21593.492 FPS
100842 frames in 5.0 seconds = 20168.339 FPS
107681 frames in 5.0 seconds = 21536.041 FPS
107155 frames in 5.0 seconds = 21430.910 FPS
102861 frames in 5.0 seconds = 20572.183 FPS
106947 frames in 5.0 seconds = 21389.306 FPS
108198 frames in 5.0 seconds = 21639.513 FPS
108671 frames in 5.0 seconds = 21734.113 FPS
104066 frames in 5.0 seconds = 20813.080 FPS
102356 frames in 5.0 seconds = 20471.044 FPS
109265 frames in 5.0 seconds = 21852.886 FPS
109381 frames in 5.0 seconds = 21876.112 FPS
109237 frames in 5.0 seconds = 21847.312 FPS
109586 frames in 5.0 seconds = 21917.042 FPS
108736 frames in 5.0 seconds = 21747.126 FPS
101523 frames in 5.0 seconds = 20304.494 FPS
108558 frames in 5.0 seconds = 21711.474 FPS
109546 frames in 5.0 seconds = 21909.056 FPS
108517 frames in 5.0 seconds = 21703.230 FPS
123550 frames in 5.0 seconds = 24706.902 FPS
123604 frames in 5.0 seconds = 24720.631 FPS
123377 frames in 5.0 seconds = 24675.247 FPS
123683 frames in 5.0 seconds = 24736.516 FPS
123531 frames in 5.0 seconds = 24706.130 FPS
124117 frames in 5.0 seconds = 24823.237 FPS
123758 frames in 5.0 seconds = 24751.575 FPS
123519 frames in 5.0 seconds = 24703.656 FPS
124080 frames in 5.0 seconds = 24815.981 FPS
123819 frames in 5.0 seconds = 24763.735 FPS
123832 frames in 5.0 seconds = 24766.350 FPS
124302 frames in 5.0 seconds = 24860.366 FPS
123927 frames in 5.0 seconds = 24785.400 FPS
124055 frames in 5.0 seconds = 24810.811 FPS
113658 frames in 5.0 seconds = 22731.596 FPS


do not run intrepid ibex nor thejaunty jakelope.  Run the LTS (long term support) hardy heron.  This is my recommendation.  after install, verify you have 3d enabled.  Do not install compiz.  It is installed already.  Also, Make sure you are using an nvidia card.  ATI and or INTEL has issues.

---

### Post by mpl34 on 2009-02-01
thanks cresho, yer it may have not been compiz that i installed as the adept manager should have displayed it was already installed but rather i just installed all apps within the adept manager that included compiz and AWN. i believe some were for a gnome environment, i only hav kde. 

Thankyou for the help,

sorry one more whats the easiest way to back up my home directory as i cant access it thru adding a new user and obviously the state of my desktop is difficult to use. can i do it konsole in recovery mode

---

### Post by Cresho on 2009-02-02
KDE i think does not use compiz-fusion.  If you where using kde4, it has it's own "compiz-fusion" aka plasmoid or plasma running.  What you need to do is fix kde since the rendering engine is offline overwritten by compiz-fusion.  this may sound like crap but this is my assessment.

what you have sir is a conflicting compositing manager.  one is out of wack which is plasma and one tha cannot inition which is compiz-fusion.  one last thing is if you ever verified the driver 3d accelerator install with glxgears.  I can  fix this if I had the issue all done in terminal at system recovery boot but its just a mess for a new commer.  This is why I recommend you reinstall.  you should really backup your stuff if you have anything worth while and reinstall.

---

### Post by Cresho on 2009-02-02
[http://forum.compiz-fusion.org/showthread.php?p=48952](http://forum.compiz-fusion.org/showthread.php?p=48952)

not sure how this would work for you

---

### Post by mpl34 on 2009-02-02
ok here is the results of glxgears very poor results in comparison, i expect this means that the correct video drivers have not been installed?

624 frames in 5.0 seconds = 124.726 FPS
649 frames in 5.0 seconds = 129.761 FPS
620 frames in 5.0 seconds = 123.933 FPS
649 frames in 5.0 seconds = 129.792 FPS
633 frames in 5.0 seconds = 126.513 FPS
639 frames in 5.0 seconds = 127.703 FPS
621 frames in 5.0 seconds = 124.017 FPS
631 frames in 5.0 seconds = 126.014 FPS
618 frames in 5.0 seconds = 123.463 FPS
645 frames in 5.0 seconds = 128.966 FPS
638 frames in 5.0 seconds = 127.518 FPS
645 frames in 5.0 seconds = 128.982 FPS
639 frames in 5.0 seconds = 127.608 FPS
644 frames in 5.0 seconds = 128.639 FPS
639 frames in 5.0 seconds = 127.664 FPS
645 frames in 5.0 seconds = 128.962 FPS
639 frames in 5.0 seconds = 127.653 FPS
645 frames in 5.0 seconds = 128.942 FPS
638 frames in 5.0 seconds = 127.521 FPS
634 frames in 5.0 seconds = 126.758 FPS
626 frames in 5.0 seconds = 125.066 FPS
645 frames in 5.0 seconds = 128.833 FPS
602 frames in 5.0 seconds = 120.238 FPS
646 frames in 5.0 seconds = 129.151 FPS
637 frames in 5.0 seconds = 127.264 FPS
647 frames in 5.0 seconds = 129.270 FPS
638 frames in 5.0 seconds = 127.410 FPS
650 frames in 5.0 seconds = 129.832 FPS
635 frames in 5.0 seconds = 126.958 FPS
649 frames in 5.0 seconds = 129.757 FPS
637 frames in 5.0 seconds = 127.217 FPS
650 frames in 5.0 seconds = 129.987 FPS
633 frames in 5.0 seconds = 126.550 FPS
644 frames in 5.0 seconds = 128.753 FPS
635 frames in 5.0 seconds = 126.896 FPS
645 frames in 5.0 seconds = 128.971 FPS
631 frames in 5.0 seconds = 126.143 FPS
647 frames in 5.0 seconds = 129.201 FPS
631 frames in 5.0 seconds = 126.141 FPS
642 frames in 5.0 seconds = 128.237 FPS                                         
633 frames in 5.0 seconds = 126.553 FPS                                         
646 frames in 5.0 seconds = 129.159 FPS

---

### Post by Cresho on 2009-02-02
no!  they are fine.  Most likely you have video sync enabled and your frames per seconds is being caped by your refresh rate.

or...........your card drivers have not been installed or activated.  Under restricted drivers, if kde uses one, is your proprietary video card drivers enabled?

do this

glxinfo | grep rendering

if it says yes, then you have 3d rendering and you are good to go.  NOW  to enable compiz-fusion in kde4 is a bit tricky.  are you running 4?

here are some info on 3d acceleration
[https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html](https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html)
this link is very old but the info in there sort of works...gives you an idea on what they use to use.

---

