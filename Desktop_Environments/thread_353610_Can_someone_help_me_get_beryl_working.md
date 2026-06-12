---
title: "Can someone help me get beryl working?"
date: 2007-02-04
forum: Desktop Environments
---

### Post by Krunk_Kracker on 2007-02-04
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX)

I used that FAQ and I'm trying to get Beryl working and I get to this step, "sudo apt-get install beryl" and I get this error...."justin@justin-desktop:~$ sudo apt-get install beryl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package beryl
justin@justin-desktop:~$ "

I need help fellas! This is my backup rig and I'm brand new to Linux and Ubuntu and was wanting to check out the eye candy. Any ideas?

---

### Post by shareMenaPeace on 2007-02-04
edit

---

### Post by raul_ on 2007-02-04
My guess is that you didn't add the Beryl repositories to your sources.list file, or if you did, you forgot to to a "apt-get update", Or if you did, are you using Ubuntu Edgy or Dapper?

---

### Post by shareMenaPeace on 2007-02-04
What ubuntu version you use?

Maybe this is informative
[http://ubuntuforums.org/showthread.php?t=325462&highlight=Couldn%27t+find+package+beryl](http://ubuntuforums.org/showthread.php?t=325462&highlight=Couldn%27t+find+package+beryl)

---

### Post by John.Michael.Kane on 2007-02-04
Have you looked over this guide [http://www.ubuntuforums.org/showthread.php?t=263851&highlight=beryl](http://www.ubuntuforums.org/showthread.php?t=263851&highlight=beryl)

---

### Post by OHardBodyO on 2007-02-05
maybe this will get you in the right direction

---

### Post by Waappu on 2007-02-05
Hi

If you are using Ubuntu Edgy and you have ATI video card try this script
[http://ubuntuforums.org/showthread.php?t=338771](http://ubuntuforums.org/showthread.php?t=338771)

---

### Post by Krunk_Kracker on 2007-02-05
Hey guys! Thanks alot, I'll read over all the links you posted adn get back with any issues I may have.

HardBody, how did you get to where you are in the SS?

Thanks guys, please be patient with teh Linux noobs, I REALLY want to learn Linux but after using/working with windows for so long, it a HUGE learning curve. :)

---

### Post by OHardBodyO on 2007-02-06
System, Administration, Synaptic Package Manager

---

### Post by Krunk_Kracker on 2007-02-06
WEll, it didn't work at all, lol.
 
I guess this cheap little Rage 128 ATI card isn't compatible on this back up box. I'll just have to install it on my main rig after I get my new PSU in, hopefully it will run on my 7800GT :)

The script though, worked wonderfully, everyhting installed correctly, thanks alot for that!

---

### Post by nojobbob on 2007-02-08
I ran into some problem when I attempted to install Beryl.

pc@Big-Ubuntu:~$ sudo apt-get install beryl emerald-themes
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
beryl: Depends: beryl-core but it is not going to be installed
Depends: libberylsettings0 but it is not going to be installed
Depends: libberyldecoration0 but it is not going to be installed
Depends: beryl-plugins but it is not going to be installed
Depends: beryl-settings but it is not going to be installed
Depends: beryl-manager but it is not going to be installed
emerald-themes: Depends: emerald (>= 0.1) but it is not going to be installed
E: Broken packages


I don't quite understand what the meaning is or how to go about fixing so I can install Beryl.

---

### Post by shareMenaPeace on 2007-02-08
Hi, 
did you added the repoistorys?

for edgy
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL)

---

### Post by nojobbob on 2007-02-10
OK, so I went back through and double-checked all the repositories I have, and they are the exact ones mentioned on all the install guides for beryl.

It appears that all the dependencies are libraries and files that have a higher revision number than what is available.

So my question I guess now is how do I gain access to these higher versions, because there are a seemingly endless number of dependencies, and installing each of them individually will not be fun.

---

### Post by nojobbob on 2007-02-10
Ok, after more fiddling around, I finally got beryl and emerald-themes installed, but now I have a new problem.

When I launch Beryl-Manager, I go to select beryl as the window manager, it reloads, then comes back with metacity. Is there a log I can look at to see why beryl is failing?

I'm also playing around with the idea of just doing a fresh install of 6.10, but I'd hate to have to reload my other software too.

Any ideas?

---

### Post by nojobbob on 2007-02-10
pc@Big-Ubuntu:/etc/X11$ beryl
XGL Absent, checking for NVIDIA
Nvidia Absent, checking for texture_from_pixmap
texture_from_pixmap absent, using Copy mode
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
beryl: glXCreateContext failed
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0


I do have an nVidia card and I have updated the drivers.

Any help appreciated.

-TIA

---

### Post by graabein on 2007-04-24
I have the same problem. Not concerning Beryl but [B]$ glxinfo
Error: glXCreateContext failed[/B]

I have the latest nVidia and it worked before I set up two X screens to have tv-out. I think I also removed some old compiz packages. Anyone know where to start looking? Did you work it out **nojobbob**?

Googling gives me a lot of high-tech hits. 

:confused:

---

