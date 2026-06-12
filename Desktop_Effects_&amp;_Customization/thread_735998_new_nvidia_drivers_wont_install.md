---
title: "new nvidia drivers wont install"
date: 2008-03-26
forum: Desktop Effects &amp; Customization
---

### Post by sandro87 on 2008-03-26
i've tried to enable desktop effects, but when i do it asks me to enable drivers. when i tell ubuntu to do so, it gives me an error message 404, it cann't find the drivers, but it does tell me the name of the drivers:

nvidia-glx-new_100.14.19+2.6.22.4-14.10_i386.deb

i've found these drivers manually over the internet, downloaded them, but when i try to install them with package installer, i get an error saying that new package conflicts with the installed package "nvidia-glx"

any suggestions? what should i do ?

tnx

---

### Post by christianxxx on 2008-03-26
Have you tried using Envy? 
I've had success with this tool.

[http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html")

---

### Post by liorc666 on 2008-03-26
indeed envy is good tool.
if you have no good with it just grab your graphic card drivers from : 
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

make sure you choose "linux" 
the file will look something like that :
"NVIDIA-Linux-x86-169.12-pkg1.run"
or some diffrent numbers


then save it to your desktop and do in terminal:

```
sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
```

now go to console : 

Ctrl + Alt + F2 //this will bring you into console

```
/etc/init.d/gdm stop
 cd ~/Desktop/
sudo sh NVIDIA(press some tab its will complete the name)
```

follow the installation ... agree when he says to re-conf your xorg ,
this will install nvidia drivers.

to check if its works run in terminal :```
 glxinfo | grep direct
```
the output should be : direct rendering: Yes

---

### Post by sandro87 on 2008-03-26
tried envy, but i couldn't install it correctly and it created me some problems..

so i've decided to try again to install nvidia.new.glx package, and with some other packages that i didn't have (found out i need them on ubuntu guide :)) i finished installing it manually, and now desktop effects work.

tnx for the replies anyways guys!

---

