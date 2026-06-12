---
title: "Noob need help running Ubuntu in VM..."
date: 2009-05-14
forum: General Help
---

### Post by bmfc187 on 2009-05-14
HI, im kinda new to the whole linux thing.  Im really interested in learning this stuff, and im trying it out, but i need some help.  RIght now i have a compaq presario f700 (laptop) running windows vista.  I am using vmWare Player to run ubuntu 9.0.4.  problem is i guess since this is a windows computer, nothing works inside the VM.  I have no internet, no drivers for anything, no anything but a desktop and a dumb look. someone please help.  im really interested in learning this, but i dont know where to start...i guess my question is how do i get my hardware to work with the VM?  How do i figure out what drivers i need and how to install them?  Ive been tryin to read alot of stuff but right now theres no way for me to tell whether im reading the right things or not.  Help?  ANyone?  please?

thanks....

EDIT:  I have read trough the virtualization section, but all i found are threads related to running VMWare IN ubuntu, not running ubuntu in VMware in Windows....

-BMFC

---

### Post by BslBryan on 2009-05-14
Hello, bmfc187. :-)

Do you have a wired internet connection, or are you relying on wireless?

---

### Post by emacbri on 2009-05-14
Hi,

I highly suggest, if you are trying ubuntu, you should use wubi (Located on the CD) to install ubuntu as a program inside of windows, then you can remove it from inside of windows.:)

---

### Post by dcstar on 2009-05-14
> **bmfc187 said:**
> HI, im kinda new to the whole linux thing.  Im really interested in learning this stuff, and im trying it out, but i need some help.  RIght now i have a compaq presario f700 (laptop) running windows vista.  I am using vmWare Player to run ubuntu 9.0.4.  problem is i guess since this is a windows computer, nothing works inside the VM.  I have no internet, no drivers for anything, no anything but a desktop and a dumb look. someone please help.  im really interested in learning this, but i dont know where to start...i guess my question is how do i get my hardware to work with the VM?  How do i figure out what drivers i need and how to install them?  Ive been tryin to read alot of stuff but right now theres no way for me to tell whether im reading the right things or not.  Help?  ANyone?  please?

thanks....

-BMFC

Please look in the Virtualization forum.

---

### Post by bmfc187 on 2009-05-14
> **BslBryan said:**
> Hello, bmfc187. :-)

Do you have a wired internet connection, or are you relying on wireless?

Wireless...and thanks for trying to help instead of just telling me to use the search function that i already used....

-BMFC

---

### Post by bmfc187 on 2009-05-14
> **emacbri said:**
> Hi,

I highly suggest, if you are trying ubuntu, you should use wubi (Located on the CD) to install ubuntu as a program inside of windows, then you can remove it from inside of windows.:)

I dont have a CD, i just downloaded all this stuff after i figured out i could do it that way.

-BMFC

---

### Post by emacbri on 2009-05-14
Then burn the Image to a Disc and try it that way.

---

### Post by Ahadiel on 2009-05-14
> **bmfc187 said:**
> HI, im kinda new to the whole linux thing.  Im really interested in learning this stuff, and im trying it out, but i need some help.  RIght now i have a compaq presario f700 (laptop) running windows vista.  I am using vmWare Player to run ubuntu 9.0.4.  problem is i guess since this is a windows computer, nothing works inside the VM.  I have no internet, no drivers for anything, no anything but a desktop and a dumb look. someone please help.  im really interested in learning this, but i dont know where to start...i guess my question is how do i get my hardware to work with the VM?  How do i figure out what drivers i need and how to install them?  Ive been tryin to read alot of stuff but right now theres no way for me to tell whether im reading the right things or not.  Help?  ANyone?  please?

thanks....

EDIT:  I have read trough the virtualization section, but all i found are threads related to running VMWare IN ubuntu, not running ubuntu in VMware in Windows....

-BMFC
Since you are new to Ubuntu, I'd recommend trying a pre-made VMWare Appliance.

[http://www.vmware.com/appliances/](http://www.vmware.com/appliances/)

---

### Post by bmfc187 on 2009-05-14
> **Ahadiel said:**
> Since you are new to Ubuntu, I'd recommend trying a pre-made VMWare Appliance.

[http://www.vmware.com/appliances/](http://www.vmware.com/appliances/)

yeah thats what im using, sorry i didnt specify....i dont really know what the difference is...im just trying to figure all this stuff out...i know what i wanna do and i could do it if had the internet so that i could get packages....but i cant really do much cuz, well i knew itd be complex, but...i know the current wireless driver i have is Atheros, and so i went to see if they have a driver for linux, and they did, and i got it, and realized how useless it is until i figure out how to build and compile from source, cuz thats what it wanted me to do...

-BMFC

---

### Post by dcstar on 2009-05-15
> **bmfc187 said:**
> yeah thats what im using, sorry i didnt specify....i dont really know what the difference is...im just trying to figure all this stuff out...i know what i wanna do and i could do it if had the internet so that i could get packages....but i cant really do much cuz, well i knew itd be complex, but...i know the current wireless driver i have is Atheros, and so i went to see if they have a driver for linux, and they did, and i got it, and realized how useless it is until i figure out how to build and compile from source, cuz thats what it wanted me to do...

-BMFC

A VM uses the resources of the host. If you have VMWare on the XP machine installed correctly then any VM whatsoever will be able to access all the host resources.

You do not have an Ubuntu issue, you have a VMWare issue and you should go to the VMWare support site to get information on how to set it up correctly.

---

### Post by lilmale1 on 2009-05-15
sorry to butt in but im on the same page
do i have to reconfigure my usb adapter wifi
with the ubuntu 
or do i have to fix it with vmware
i wouldn't have a clue what they talk about in server
so I thought it would be good for me to ask here now

if vmware supports this wifi how?
it only reads my ethernet one but not my wifi

---

### Post by lilmale1 on 2009-05-15
im a noob too i figure it out with your guys help
but the only thing i noticed is that wifi goes out on 
my xp 

when i go to **add** new device on the options page of vmware.

use **usb device** start my ubuntu on **start** and then go to **vm** on task bar
**select my usb device** and then it works but stil no internet on 
xp now

is there a way to keep both on

---

### Post by bacardiandwatermelon on 2009-05-15
Have you installed Vmware tools?
[http://www.vmware.com/support/ws55/doc/ws_newguest_tools_linux.html]("http://www.vmware.com/support/ws55/doc/ws_newguest_tools_linux.html")

---

### Post by 3rdalbum on 2009-05-15
I don't think you quite understand what the virtual machine software is actually doing.

The virtual machine does not expose your actual hardware to the guest operating system - this would be disasterous in causing conflicts. Instead, the virtual machine **emulates** a basic set of hardware. When the guest operating system sends data to the emulated sound card, the virtual machine will send the data through Windows' APIs just like any other program, and it will reach the sound card this way.

Now, networking hardware is the same. VMWare will not allow the guest operating system to directly access the wireless card. Instead, it will provide a virtual Ethernet network to the guest. When the virtual Ubuntu sends data to the virtual Ethernet port, VMware will send it through Windows' networking system to the wireless card (or whatever real networking device you are using; so a mobile broadband connection will still look to Ubuntu to be an ethernet connection).

Not only do you not need to install real hardware drivers on the virtual Ubuntu, but the real hardware drivers won't work (they will be looking for real hardware that is not available, rather than the emulated hardware that is). So don't install Atheros drivers in Ubuntu because this is likely to prevent your internet connection from working.

If you tell Ubuntu to connect to the internet using the Ethernet device, this should work Out Of The Box. There may be an option in VMware to enable the emulated network device.

Why not just install Ubuntu on your real hardware? That way you can look at Ubuntu in the way it was intended, and determine whether your hardware is compatible. You will also be able to use features on real hardware that are not available in a virtual machine - desktop effects, sound input and output, 3D games, hardware management, more speed.

EDIT: You can "pass through" actual USB devices on some virtual machine software so it can be accessed directly by the guest, but you still cannot use a single device by two operating systems simultaneously.

---

### Post by bmfc187 on 2009-05-15
3rdalbum, thanks for your help and for such an in-depth reply, turns out it was just what i needed, i found how to tell the VM to connect and then ubuntu connected right up...as far as your question...i REALLY want to put install some linux distro on my laptop and never look back on windows, but i didnt wanna mess up my system just to figure out it doesnt work that way...that´s my luck. so i was tryin this out cuz i didnt know where else to start, but i wanna feel my way around this for a bit, before i go installing anything anywhere without some help or some knowledge that i currently dont possess.  My main reasons for the switch are i´ve recently discovered a veritable ¨Information Underground¨ called Open Source, and im lovin every minute of it!  Also, i have one of those new-fangled Google G1´s, and i wanna develop applications for Android, but development under windows is currently unsupported.  Ubuntu, on the other hand, is the main OS used in the development of android.  Or so they say.  Anyway, my current problem is solved, thanks for all your help, 3rdalbum, and everyone else that put in their two cents...thanks!

---

### Post by albinootje on 2009-05-15
> **bmfc187 said:**
> i REALLY want to put install some linux distro on my laptop and never look back on windows

In my opinion the nicest way to test drive Ubuntu on your specific hardware is to use the live session of an Ubuntu desktop installation cdrom or usb stick.
Boot from it, and choose "Try without making changes".
With that you can see what hardware on (and attached) to your computer works out of the box.

The cool thing from the live session is that you can temporarily install software (into RAM memory), and play around until you decide to reboot.

---

