---
title: "Nvidia Drivers... Stuck in terminal (complete noob)"
date: 2009-01-20
forum: General Help
---

### Post by mnbvcxz on 2009-01-20
Hey, I have looked everywere to try and figure out how to install nvidia drivers on the ubuntu i have (8.10). I am a complete noob so i don't know anything when it comes to linux. 

Anyway, i have tried several different method of installing the drivers, each with the same end result... I get stuck in the terminal at bootup and nothing i do takes me to a GUI. I have tried pressing CTRL+ALT+F7 and nothing... I remember there being something about there is no image or something..

The methods i used to install the drivers:
1) I went to the hardware drivers application under the administrator tab and enabled the nvidia drivers, which downloaded and installed fine.

2) i logged in as root, and typed something like apt-get update, apt-get upgrade, apt-get install nvidia... or something like that i carnt remeber exactly what i put in but the installation was sucessful but still i was stuck in a terminal at bootup.

3) Logged in as root. I shut down the X server using, 

sudo /etc/init.d/gdm stop

I used the cd command to take me to the desktop

cd Desktop

Then,

sh NVIDIA-Linux-x86_64-180.22-pkg2.run

The nvidia installer ran and installed the drivers sucessfully and then i automatically configured the x server using the nvidia installer. I stared the x server again using 
sudo /etc/init.d/gdm start
this did nothing so i rebooted but i was still stuck in the console.
I tried the installation once with 32bit opengl libaries installed and once without. it came up that it could not verify one file so it assumed that the installation was sucessful.

I have now re-installed ubuntu but i am unable to install nvidia drivers without getting stuck in the terminal at bootup.

How can i get out the terminal if it happens again?
How do i install Nvidia drivers??
Remember i am a total nooob! I have used linux for a total of 3 days.

I have heard there is something "envyNG" which will download, install, and ocnfigure the x server for me but i have not tried this as it states its for version 8.04 of ubuntu. will it still work?

I am running the 64 bit version of the os.
I have 2x 8800gtx ultras in SLI, a Qx6850 @ 3.6Ghz, 4gb ram, evga 790i ultra mobo. 

These are the drivers i tried to install:
[http://www.nvidia.co.uk/object/linux_display_amd64_180.22_uk.html]("http://www.nvidia.co.uk/object/linux_display_amd64_180.22_uk.html")

these are some of the steps i followed:
[http://uk.download.nvidia.com/XFree86/Linux-x86_64/180.22/README/chapter-04-section-02.html]("http://uk.download.nvidia.com/XFree86/Linux-x86_64/180.22/README/chapter-04-section-02.html")

[http://www.psychocats.net/ubuntu/nvidia]("http://www.psychocats.net/ubuntu/nvidia")

[http://www.pendrivelinux.com/installing-nvidia-drivers-in-ubuntu-edgy/]("http://www.pendrivelinux.com/installing-nvidia-drivers-in-ubuntu-edgy/")

they are the 3 individual guides i used 
Any help or suggestions will be greatly appreaciated. :)

---

