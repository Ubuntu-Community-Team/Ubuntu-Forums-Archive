---
title: "Cant install Ubuntu 6.06...Install Crashes ..other times it freezes"
date: 2006-08-11
forum: Desktop Environments
---

### Post by luis_kse on 2006-08-11
sorry if its long but im trying to be as detailed as posible...

I have windows xp (pro) SP2 installed in my computer... I left 7GB of unparticioned space in my harddrive so I could install Ubuntu 6.06 later
today I tried to install UBUNTU 6.06 from the live cd but i couldn't...the first time..the installer froze..while "Copying Files"..at 71% to be precise...and i had to reboot...
the next time I tried.. the installer crashed and showed a message error that said:


Traceback (most recent call last):
  File "/usr/bin/ubiquity", line 130, in ?
    install(sys.argv[1])
  File "/usr/bin/ubiquity", line 55, in install
    ret = wizard.run()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 266, in run
    self.process_step()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 741, in process_step
    self.mountpoints_to_summary()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 1029, in mountpoints_to_summary
    self.progress_loop()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 538, in progress_loop
    raise RuntimeError, ("Install failed with exit code %s; see "
RuntimeError: Install failed with exit code 1; see /var/log/installer/syslog and /var/log/syslog


and it also said something about two files i found in the folder.. /var/installer/log/systemlog.. and /var/installer/parmant..im not sure the paths are completely right but i got the files on a floppy..

to install it i did this...

I used the 6 steps wizard (the install icon on desktop) and choose "manual"...i created 2 new partitions... one was a primary partion with ext3 format..size= 6,200 MB and the other one was a Primary with linux-swap format..size= 650MB..

My installation of windows was set to the first partition..

I set the root "/" to the 6,200MB partition(the second one) with the option "reformat" checked..
and i set the third one as "swap"..with "reformat" checked..
i clicked FORWARD ..the installation begun and then..THE ERRORS MENTIONED ABOVE...

i tried to install it a thousand times and still doesnt work..
im not sure whats going wrong..i may be making a mistake when trying the installation..

any suggestion would be of great help... 

thankssss

---

### Post by vijirajan on 2006-08-11
I would try the Alternate CD install. I have had people reporting errors with Live CD.

Here is the URL to download the alternate install cd:

[http://cdimage.ubuntu.com/dapper/daily/current/](http://cdimage.ubuntu.com/dapper/daily/current/)

---

### Post by unisol on 2006-08-12
yes the alternate cd or maybe you could try a server install, thenwhen at the command prompt apt-get install linux-386 to have the right kernel for the desktop then do a sudo apt-get install ubuntu-desktop you also may have to do a dpkg -reconfigure - phigh xserver-xorg then hit ini2 you should have desktop. hope all goes well if it doesnt you may have a hardware problem

---

