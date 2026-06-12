---
title: "installing ubuntu 8.04 - /etc/rc.local hangs and forces me to low-graphics mode"
date: 2008-05-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by stefano_81 on 2008-05-04
Hello Everybody,

I have just installed ubuntu 8.04 on my dell d630. The installation did not give me any kind of problem. The first thing that I wanted to do after completing the SO installation was to install the driver for the graphic card (nVidia Quadro 135M). At the end of this installation I got this warning:


-> Running runtime sanity check:
WARNING: Unable to perform the runtime configuration check for library
         'libGL.so.1' ('/usr/lib32/libGL.so.100.14.19'); assuming successful
         installation.


that I lazily ignored :(
I am not sure whether that one was the problem, but after the installation I could not start ubuntu properly: the boot stops at 
"running /etc/rc.local"
for few seconds and then I am asked to start X in low graphics mode (i.e., very low resolution). 
I can get around this logging in from Alt+F2, killing gdm, reinstalling the  nVidia driver and then launching startx from the console. But of course this is not the kind of solution I am looking for. 

I know that there is quite a lot of people that is having problems with /etc/rc.local ( I found several threads, like [http://ubuntuforums.org/showthread.php?t=498943](http://ubuntuforums.org/showthread.php?t=498943) ). From what I've understood, this might be related to a bug: it seems that somehow it is related to getty starting to early. I am wondering if anybody have found a solution.

 stefano

---

### Post by fragos on 2008-05-04
Apparently you chose not to let Ubuntu install the driver from it's repositories. The correct way is to click System-> Administration-> Hardware drivers. The window will show the availabilited of non-GPL licensed drivers. Enable the one you want and it will be installed. /etc/rc.local has only one command, "exit 0," unless someone has chosen to edit the file.

---

### Post by veedub on 2008-05-05
For some reason the ubuntu drivers from the repository did not work for me.  I had to remove the ubuntu drivers and install the driver from the website.

The following worked for me(xps1530 w/ geforce 8600GT):

-From synaptic, uninstall the nvidia-glx, and nvidia-glx-new drivers.
-Download the new nvidia driver from the nvidia website. [http://us.download.nvidia.com/XFree86/Linux-x86/173.08/NVIDIA-Linux-x86-173.08-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/173.08/NVIDIA-Linux-x86-173.08-pkg1.run)

-Break out of X (CTRL+ALT+F2)
-Log-in again
-sudo /etc/init.d/gdm stop
-cd into the directory where is the NVIDIA-Linux-x86-173.08-pkg1.run
-sudo sh./NVIDIA-Linux-x86-173.08-pkg1.run
-follow the prompts and agree to everything.
-sudo /etc/init.d/gdm start

You should see the NVIDIA logo come up as the x server restarts.  You will need to reconfigure your resolution again.

---

### Post by stefano_81 on 2008-05-07
Thanks so much guys.

Yesterday night I tried to let the manager do the dirty work. On "Hardware drivers" I let it download and install the driver for the graphic card. Unfortunately it did not work again.

veedub, the procedure that you describe is what I did to install the driver for my nVidia Quadro 135M (except that I was a bit ruder and I used killall to stop gdm). 

The thing is weird though. If, when I get the window for accepting the low graphic mode, just before the log in, I switch to a console login, I kill gdm, reinstall the nVidia driver and run stratx, the system works perfectly, altogether with the advanced desktop effects and glxgears running on 4500 fps. I cannot really understand...

 stefano

---

