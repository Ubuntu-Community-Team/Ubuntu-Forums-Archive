---
title: "Bluetooth always switch on + another matters"
date: 2009-05-10
forum: General Help
---

### Post by AlNaimi on 2009-05-10
Hi every one...
I'm new to ubuntu 9.4 (64bit) & i need some help here....
First: bluetooth always switch on every boot even after i delete Bluetooth Manager at startup application programs. I don't know how to stop bluetooth from being work every time i switch on laptop?
Second: I added to startup application programs or (Sessions) a commend to start firefox and remember it, then i delete this commend, but unfortunately firefox open every time i login to computer?
Third: My SD memory card dose not work?
Finally: Any speech program (to read a text in english) can be used with ubuntu?
Thanks a lot in advanced

---

### Post by AlNaimi on 2009-05-10
Any one?
Plz

---

### Post by drs305 on 2009-05-10
To kill firefox on start, close all apps, then go to System, Preferences, Startup Applications (or Sessions), Options and enable the Automatically Remember (with no apps running). Shut down and after restarting go back and deselect that option. That should prevent firefox from starting unless you have a specific startup command in the Startup section. Check this section for bluetooth also.

To kill bluetooth, if you are sure you won't be using it, you can delete the bluetooth settings from System, Administration, Services if it is listed there. If not, you can delete the references to bluetooth in /etc/init.d and the links in /etc/rc.2-5 (that's rc.2, rc.3, etc). The bluetooth links starting with S are the bluetooth start links.

---

### Post by AlNaimi on 2009-05-10
Thanks a lot drs305 
> **drs305 said:**
> To kill bluetooth, if you are sure you won't be using it, you can delete the bluetooth settings from System, Administration, Services if it is listed there.
Yes it is list it in services, put it only give my properties option, and i don't know to use do it by the another way, However should that be a system bug?
also, i do like to understand more about the SD memory, if you can.
Thanks again

---

### Post by drs305 on 2009-05-10
> **AlNaimi said:**
> Yes it is list it in services, put it only give my properties option, and i don't know to use do it by the another way, However should that be a system bug?


When you unlock the Services menu, if you right click all you would get is "properties". But do you have a tick box out to the left to select or deselect the option? That is how you turn it on and off normally.  

If you don't have that tick box, you can run this command from terminal to (hopefully) shut down the bluetooth initialization:
```

sudo update-rc.d bluetooth remove

```
This command removes the entries I described in the earlier post.

With your SD card inserted in your computer, do you see it when you run:
```
sudo fdisk -l
```

---

### Post by AlNaimi on 2009-05-10
Thanks again drs305
Yes, the bluetooth Service was uncheck, It was running every login.
So, i can remove it by that commend in terminal but how i can restore it again? if i need?
And about the SD card, No it wasn't appear with (sudo fdisk -l)!

---

### Post by drs305 on 2009-05-10
> **AlNaimi said:**
> Thanks again drs305
Yes, the bluetooth Service was uncheck, It was running every login.
So, i can remove it by that commend in terminal but how i can restore it again? if i need?
And about the SD card, No it wasn't appear with (sudo fdisk -l)!

If bluetooth is still installed, run the following command to restore it. If not, install it and then run it:
```
sudo update-rc.d bluetooth defaults
```

As for the SD card, have you tried using a different USB port to connect it or made sure it works in another computer? I don't use them often and mine just work so my knowledge of the topic is pretty limited.

---

