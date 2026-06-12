---
title: "Ubuntu is running in low graphics mode"
date: 2010-09-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by maniek2808 on 2010-09-27
Hi everyone,

every time I boot up my machine,  get error &#8220;Ubuntu is running in low-graphics mode". Before it hepened  installed few packages for XBMC and then at the end run cmd... shutdown now -h . Maybe with that command laptop didn't have enough time to finish up all running processess and it demaged system files. Laptop is fine because it booted with windows 7 and live CD. I have attached pictures of x.org file and exact error message. 
   
   
  Can someone help me with that ? 
   
  [http://img697.imageshack.us/img697/3351/img0009kw.jpg](http://img697.imageshack.us/img697/3351/img0009kw.jpg)
  [http://img267.imageshack.us/img267/9807/img0002ul.jpg](http://img267.imageshack.us/img267/9807/img0002ul.jpg)
  [http://img826.imageshack.us/img826/1430/img0003ni.jpg](http://img826.imageshack.us/img826/1430/img0003ni.jpg)
  [http://img189.imageshack.us/img189/3634/img0004gp.jpg](http://img189.imageshack.us/img189/3634/img0004gp.jpg)
  [http://img16.imageshack.us/img16/9520/img0005asp.jpg](http://img16.imageshack.us/img16/9520/img0005asp.jpg)
  [http://img291.imageshack.us/img291/4646/img0006hd.jpg](http://img291.imageshack.us/img291/4646/img0006hd.jpg)
  [http://img97.imageshack.us/img97/8613/img0007rg.jpg](http://img97.imageshack.us/img97/8613/img0007rg.jpg)
  [http://img512.imageshack.us/img512/7729/img0008js.jpg](http://img512.imageshack.us/img512/7729/img0008js.jpg)
  [URL="http://img697.imageshack.us/img697/3351/img0009kw.jpg"]
[/URL]

---

### Post by Jeroensum on 2010-09-27
**[English]**
Try running 
[I]sudo apt-get check gnome-desktop-environment 
[/I]
In a terminal. Then post the output.


**[Dutch]**
Probeer het volgende commando eens in een terminal te draaien:
sudo apt-get check gnome-desktop-environment

Een terminal kun je openen via Applicaties->Accessoires
Post de output van het commando dan even hier. Ik denk namelijk dat je o.a. de fonts mist en misschien nog wat andere belangrijke zaken.

---

### Post by maniek2808 on 2010-09-27
> **Jeroensum said:**
> **[English]**
Try running 
[I]sudo apt-get check gnome-desktop-environment 
[/I]
In a terminal. Then post the output.


That't the result. 
Reading package lists ... Done
Building dependency tree
Reading state informaiton ... Done

By the way when i type cmd xrandr i get output ....
Can't open display

---

### Post by maniek2808 on 2010-09-27
Any other ideas ?

---

### Post by lswartz on 2010-09-27
I got the same message 'low graphics mode' today on my desktop right after installing several updates. I went to System, Administration, Hardware Drivers, & installed the ATI/AMD proprietary FGLRX graphics driver. It requires a reboot of the computer & it solved the problem.

I hope it works for you. It should if you have an ATI video card/chip.

Added. I just saw that you had an intel graphics chip. I am not sure on them as my Mini 9 just worked after the same updates.

---

### Post by alexpennos on 2010-10-01
> **lswartz said:**
> I got the same message 'low graphics mode' today on my desktop right after installing several updates. I went to System, Administration, Hardware Drivers, & installed the ATI/AMD proprietary FGLRX graphics driver. It requires a reboot of the computer & it solved the problem.

I hope it works for you. It should if you have an ATI video card/chip.

Added. I just saw that you had an intel graphics chip. I am not sure on them as my Mini 9 just worked after the same updates.
Same updates destroyed the whole setup of my system....I had those proprietary drivers installed before the update. Now, the run in low graphics mode, and the graphics card option doesn't exist anymore in the system->admin.->hardware drivers

---

