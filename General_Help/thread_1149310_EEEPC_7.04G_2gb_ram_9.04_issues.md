---
title: "EEEPC 7.04G 2gb ram 9.04 issues"
date: 2009-05-05
forum: General Help
---

### Post by dustyhawk on 2009-05-05
just installed NBR 9.04, so far so good but i have some issues and if this is not the place to do it, kindly transfer this thread to the appropriate area.

Issues i have are :

1. Slow response in which it takes about 5sec or so just to launch a program such as text editor.

2. The inability to install eee-control.deb (though this would probably be easy to fix), i went to the website and when i click on the link i do not have the option to install via debian which i did last time. I did install gdebi but that did not seem to work.   Wanting to install this as the hotkeys does not work and the card reader is not working

3. this happens whenever i launch firefox, not sue why. [http://img.photobucket.com/albums/v331/dustyhawk/Screenshot-3.png](http://img.photobucket.com/albums/v331/dustyhawk/Screenshot-3.png)




Other than the above, i would say that it is fantastic.

---

### Post by bubba_169 on 2009-05-05
In response to question 2, do you get the option to open with but no program listed? If so you have the same problem I had then all you have to do is choose select program, navigate to /usr/bin/gdebi-gtk

It should install ok then :D

Not too sure about the others though. There is a compatability list somewhere that will let you know what works and what doesnt and some fixes with UNR for different models of netbook.

---

### Post by dustyhawk on 2009-05-06
> **bubba_169 said:**
> In response to question 2, do you get the option to open with but no program listed? If so you have the same problem I had then all you have to do is choose select program, navigate to /usr/bin/gdebi-gtk

It should install ok then :D

Not too sure about the others though. There is a compatability list somewhere that will let you know what works and what doesnt and some fixes with UNR for different models of netbook.

Your answer for #2 works though not in the way i expected it to be.

I do not have the options of powersave-XX-XX-full  under performance section. Only "none"


##Card reader is not reading even when it is switched on.

## i notice that if i switch of the wireless via eee-control, i cannot switch it back on. As in the check mark in the box is there, but the light at the front is not on and at the taskbar, it doesnt detect any wireless unless i restart the system.


I can not use any USB stick at all, not detected at all.

and im still getting that  Network Keyring thingy.


What i notice is that if I remove that NBR the window that shows all the icons on the screen; programs does launch faster without it.

With that NBR windown, it sometime has a 5 second lag.

---

### Post by fewt on 2009-05-06
> **dustyhawk said:**
> just installed NBR 9.04, so far so good but i have some issues and if this is not the place to do it, kindly transfer this thread to the appropriate area.

Issues i have are :

1. Slow response in which it takes about 5sec or so just to launch a program such as text editor.

2. The inability to install eee-control.deb (though this would probably be easy to fix), i went to the website and when i click on the link i do not have the option to install via debian which i did last time. I did install gdebi but that did not seem to work.   Wanting to install this as the hotkeys does not work and the card reader is not working

3. this happens whenever i launch firefox, not sue why. [http://img.photobucket.com/albums/v331/dustyhawk/Screenshot-3.png](http://img.photobucket.com/albums/v331/dustyhawk/Screenshot-3.png)




Other than the above, i would say that it is fantastic.

If you can't get eee-control working, try EeePC ACPI Utilities - [https://sourceforge.net/projects/eeepc-acpi-util](https://sourceforge.net/projects/eeepc-acpi-util)

---

### Post by dustyhawk on 2009-05-07
> **fewt said:**
> If you can't get eee-control working, try EeePC ACPI Utilities - [https://sourceforge.net/projects/eeepc-acpi-util](https://sourceforge.net/projects/eeepc-acpi-util)

tried that but i get the following error when trying to install via synaptics

eeepc-acpi-scripts:
 Depends: acpi-support-base  but it is not installable

---

### Post by fewt on 2009-05-07
> **dustyhawk said:**
> tried that but i get the following error when trying to install via synaptics

eeepc-acpi-scripts:
 Depends: acpi-support-base  but it is not installable

eeepc-acpi-scripts isn't eeepc-acpi-utilities. ;-)

I would have chosen a different name had I known that the eeepc-acpi-scripts existed when I started the project.

---

### Post by dustyhawk on 2009-05-09
thanks guys for the replies. really appreciate it.
However i went and reinstalled JJ and found out some items

EEE-Control still does not work properly as what i have explained earlier

that error code (image link that was given) was caused by a firefox add-on.

webcam doesnt work at all

still cant get the wireless hot key to work and indicator light is still on even with manual network turn off

the battery life, seems funky. 50% brightness wireless on, dim screen on idle and im getting roughly 1.5hrs of batt life.

I'll update you guys on my adventure with JJ on this laptop.

---

### Post by dustyhawk on 2009-05-12
adding on

remember the image link i gave ? which i thought it was an add-on for firefox that was causing the problem?  Well i removed all the add-ons i have but that error still appears

another thing i notice is that ever since i have installed 9.04, after i fully charge the battery (wait for about 5 mins later) and switch the system on, it shows i only have 90% of battery charge only

---

### Post by dustyhawk on 2009-05-29
well now, even with acpi-control or that eee-control.. i am still unable to turn off the wireless and the card reader. The camera has stop functioning even if those two items are not installed.

---

### Post by firepot on 2009-06-04
> **dustyhawk said:**
> tried that but i get the following error when trying to install via synaptics

eeepc-acpi-scripts:
 Depends: acpi-support-base  but it is not installable

I have installed eeepc-acpi-scripts by adding the following debian repository to the sources list:

deb http:// eeepc.debian.net/debian squeeze main contrib non-free

This can be done by editing the sources.list file:

(on the command line) 
sudo nano /etc/apt/sources.list
sudo apt-get update

(or within synaptic) 
Settings / Repositories / Third Party Software / Add
Reload

(I have used the testing squeeze repository, but I think the same version is on Lenny) 

Within Synaptic:
click on the 'Origin' button and select ftp.uk.debian.org/universe

Install acpi-support-base first and then eeepc_acpi_scripts afterwards, otherwise you will still get an error message. (note- installing eepc_support_scripts will also remove acpi-support).

This will allow you to toggle the wifi off by using fn+f2, though its a one way street - you cant toggle the wifi back on (the blue light comes on but you are not able to connect to any networks) but it still allows you to save some battery when wifi is not needed. You will need to reboot to get wifi back.

Can't guarantee this won't break anything else but all seems OK to me at the moment.
(Asus eeepc 900 running Ubuntu Netbook Remix 9.04).

---

### Post by joey-elijah on 2009-06-04
The slow launching "issue" is due to the kernel, you can replace the kernel and fix it all very simply by adding a repo and upgrading. Follow the steps @ - [http://d0od.blogspot.com/2009/04/netbook-remix-701-slow.html](http://d0od.blogspot.com/2009/04/netbook-remix-701-slow.html)

---

