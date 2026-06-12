---
title: "[SOLVED] nVidia Drivers just wont install"
date: 2008-08-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by BryanMarley on 2008-08-31
Hey guys,

i just installed Ubuntu using Wubi in Windows Vista.

Everything just works great but i just cant get the official nvidia drivers to work.
When i download the driver pack, i press CTRL+ALT+F2 to enter kernel mode. Then i type > 'sudo -s'.
i login, and then type > '/etc/init.d/gdm stop' which also works and Gnome stops.
then i cd to the folder where my package is, and then i type
> 'sh NVIDIA*etc etc etc*.pkg2.run' 
and then it starts.
It tells me i dont have preconfigured kernel info on my pc and he asks me if he can download them, so i say yes ofcourse :)
then he tells me he cant download them but i can make them myself.
so i say, yeah sure make m. And then hell breaks loose.

He tells me i dont have the right LIBC Development package installed, and so i cant make the kernel thingys.

So im stuck, whenever i try to install the package thats on the servers @ ubuntu, it sais i got a newer version alreay installed.

What can i do to make the driver work? Or am i working in the wrong kernel level?

Hope to hear from you soon!

---

### Post by tuxxy on 2008-08-31
Was there no drivers available for you at **system > admin > hardware drivers?** 

If not you should try envyng to install the drivers, you can find envy in the repos, search for it using synaptic.

Also what card are you using?

---

### Post by BryanMarley on 2008-08-31
i got the nVidia GeForce 8600M GT which currently is running in a Dell XPS m1530, and as i can see its kind of an pain in the ** laptop hahaha.
Nothing really works, i should've bought a PC lol.

Uh Synaptic? i tried to install that once, never came out of it, im gonna try it. Ill keep you guys posted.

edit****

i found the following on another guys' post:
> Graphics

 

Immediately after installing I went to System / Administration / Hardware Drivers. There was something strange here: The nVidia driver was enabled, but not in use. Disabling / enabling the driver didn't work. To make it work properly, I had to refresh the package management system:

 

sudo apt-get update

 

After that, the driver was disabled in the Hardware Drivers screen. When I enabled it, it downloaded and installed the driver.
([http://jesperdj.pbwiki.com/Ubuntu-on-the-Dell-XPS-M1530](http://jesperdj.pbwiki.com/Ubuntu-on-the-Dell-XPS-M1530))

Gonna try everything he did i guess. I made my touchpad work using his notes, maybe hell get my videocard working as well.

Edit ***
i read what he wrote and what hes using are the drivers that are already installed when i installed Ubuntu, so those are not up to date i assume?

---

### Post by BryanMarley on 2008-08-31
First of all, the driver is installed, and it seems to be working.
about the uptodate thing: it downloads nvidia driver version **192.12** which isnt really uptodate.

the current version is **173.14.12**
So i still want to update using the drivers that nvidia gives me.
Can someone tell me how to do this? because i dont really know how to do this my own.:(

---

### Post by BryanMarley on 2008-08-31
i rebooted and guess what, my drivers work! i got desktop effects and smooth image minimizing. So i guess i dont want to update, thanks anyways for the reaction, im gonna close this one up

[RESOLVED]

---

