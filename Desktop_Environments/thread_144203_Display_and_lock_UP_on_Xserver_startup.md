---
title: "Display and lock UP on Xserver startup"
date: 2006-03-13
forum: Desktop Environments
---

### Post by ntoxicator on 2006-03-13
Hello everyone,

Well i just signed up here, however im not really new to the forums. I normally browse around and look for any troubles people might be experiencing that go along with what i have been ecountering.

Well onto the topic. Not to long ago i just upgraded my system, new video card is the main thing... i was running a 9800pro modded, and ubuntu ran fine, However i am now running a Nvidia 7800GT (evga over clocked)
Ever since i installed this card, and installed ubuntu, i had issues. Im currently on Windows if you want to know :P. This is the problem:
Ubuntu installs Flawlessly, however when i go to login, i goes to load the desktop and then once something displays the screen like artifacts and has a complete lockup where i have to restart the machine. I am experiencing this SAME issue with Suse 10.1 beta. However with 2 installs of Fedora i have not experienced this issue. ( fedora core 3, and 4)

I have looked over my Xorg.conf and it all looks fine, i dont really see anything that would cause an issue. Its just really fustrating, with this happening, works fine with Fedora, but yet not ubuntu nor Suse.:(  I have also tried updating my bios from my video card manufact, which is evga. still same issue....

Any idea's on this fact?

---

### Post by issueperson on 2006-03-14
why don't you post your xorg.conf for us to take a look at just in case?

---

### Post by Sutekh on 2006-03-14
So you have a new NVIDIA card and a new installation of Ubuntu?

You should install the NVIDIA drivers and see how that goes.

[Ubuntu Forums - HOWTO Latest NVIDIA Drivers]("http://www.ubuntuforums.org/showthread.php?t=75074")

Method 1 - dead easy - installs the NVIDIA drivers in the Ubuntu repositories

Method 2 - slightly harder - install the official NVIDIA drivers from their website.

---

### Post by ntoxicator on 2006-03-14
ehhh umm. how can i install the nvidia drivers if i cannot log into X properly, or even post my Xorg.con :P. however i do know  i can do apt-get install nvidia-glx , but im not sure if that will work, i have tried it before at one point in time if i remember right. however i am not currently running ubuntu, i have Suse 10.1 on there. However when i get home ill give ubuntu another shot. right now ill go ahead and read the nvidia howto... i have installed nvidia drivers and such before, and i have been working with linux for quite some time now.

---

### Post by Sutekh on 2006-03-14
[QUOTE=ntoxicator]ehhh umm. how can i install the nvidia drivers if i cannot log into X properly, or even post my Xorg.con :P[/QUOTE]Don't even try to get into X.   Just drop to a command line.  Everything you ned to do can be done from there.

[QUOTE=ntoxicator]i have installed nvidia drivers and such before, and i have been working with linux for quite some time now.[/QUOTE]Then this should be a piece of pie for you to fix :)

---

### Post by ntoxicator on 2006-03-14
hah. i got it working! yay. and actually it was pretty easy :). i just had the package manager download / install the nvidia driver. and then i edited the xorg.conf changed the identifyer, took out defualt and replaced it with 7800GT and such, started up X and crossed my fingers and it worked!. however the issue im having now is that i want to install the new nvidia drivers. so i can get the control pannel? i cannot seem to access it right now.

Thanks for the pointers! now to see if i can get steam installed with cedega, under fedora it would NOT install, i was reading that the latest steam update broke the install under cedega, but ima give it another shot.

---

### Post by Sutekh on 2006-03-14
[QUOTE=ntoxicator]hah. i got it working! yay. and actually it was pretty easy :). i just had the package manager download / install the nvidia driver. and then i edited the xorg.conf changed the identifyer, took out defualt and replaced it with 7800GT and such, started up X and crossed my fingers and it worked!. however the issue im having now is that i want to install the new nvidia drivers. so i can get the control pannel? i cannot seem to access it right now.[/QUOTE]
Good stuff.  Again check the NVIDIA Link I posted for gettings that to work.

---

### Post by ntoxicator on 2006-03-14
hrmm well i just installed automatix.. very nifty script, had many tools included. made my life easyer on having to install all of them by hand.. thank you very much for that. However the current problem im having right now is with the VGA fan on my video card, i think is running full speed. louder than normal. Right after the nvidia driver loads on boot, the fan spins down for a few seconds then spins right back up to speed.. any suggestions on fixing this?

---

