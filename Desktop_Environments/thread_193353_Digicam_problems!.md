---
title: "Digicam problems!"
date: 2006-06-09
forum: Desktop Environments
---

### Post by Jameth on 2006-06-09
Hello all!

First off I am running Dapper Drake, on a 3ghz Pentium 4, IBM Thinkpad.

I have done the usual search through the forums, read and read and read, tried and tried and tried all sorts of things, and am still banging my head against the wall on this!

I have a Sony DSC-R1 digital camera (look it up, its awsome).  

This camera supports mass storage, PTP, and Pictbridge.  When I set the camera on either Pictbridge or PTP, it is detected fine, and I can retrieve the jpg files from it.  However, the camera also can take RAW images, something I use alot, and they are NOT pulled from the camera through Pictbridge or PTP.  

When I set the camera to Mass Storage (to get raw images), I get absolutly nothing.  When I do a "sudo tail -f /var/log/messages" I get one entry when the camera is conected;

"Jun  9 19:44:08 orbiter kernel: [4295168.650000] usb 2-1: new full speed USB device using uhci_hcd and address 2"

And that is it!  Nothing else what so ever, upon disconecting the camera I get;

"Jun  9 19:45:25 orbiter kernel: [4295245.213000] usb 2-1: USB disconnect, address 2"

Most of the other posts regarding similar issues have ALOT more reponse when tailing that file.

What is going on?  PTP and Pictbridge are fine by me, but I HAVE to be able to get to my RAW images as well!

BTW, I know the camera is fine, just used it in windows to get the RAW images off, and I also know my USB is working in Dapper, my PSP shows up as mass storage just fine!

Thanks,  Jameth

---

### Post by jvictor on 2006-06-10
Are u using gtkam ? Its a great tool to handle Digicams.

sudo apt-get install gtkam

---

### Post by Jameth on 2006-06-10
Yes I have tried gtkam, it works with PTP and Pictbridge, but again, does not retrieve the RAW files.

Anyone else?

THanks
James

---

### Post by Jameth on 2006-06-12
Any other ideas here guys? 

I have found Ubuntu to be everything and more for my needs on my laptop.  However I have GOT to be able to get to these RAW camera files, and the usual way to do it is through mass storage.  Honestly if I can't get mass storage to work with this camera, but can somehow make PTP or Pictbridge pull the raw image files, I would be more than happy!

Thanks in advance,
Jameth

---

### Post by Franko30 on 2006-06-13
Hi,

do you, by any chance, use any other kernel than the standard linux-386 (like linux-686)?

I had a similar problem described here:

[http://www.ubuntuforums.org/showthread.php?t=195248](http://www.ubuntuforums.org/showthread.php?t=195248)

and found out, I could use my digital camera when starting Ubuntu using the linux-386 kernel.

Cheers

Franko30

---

### Post by bluenova on 2006-06-13
Raw files work fine from my 350D, Have you got the linux Raw apps installed? I can't remember what they are called and I'm not on an ubuntu box, but do a search in synaptic for raw, I think one of them is called ufraw. I also think you need the Raw kipi plugin for digikam.

HTH

---

### Post by Jameth on 2006-06-13
Hey guys, thanks for the replies!

I am using the default Ubuntu 6.06 kernel.  I have ran automatix on this machine, not that it should make a difference.

I can open and edit RAW files just fine when they are actually on the computer, but again, when using PTP or Pictbridge, it ONLY pulls the .jpg files, and not the .SR2 files.  If I can get the camera to show up as mass storage, as I normally use it in Windows, then I can simply browse to the RAW file directory and pull them off myself.

So the main problem here, as I stated in my first post, is that the *mass storage* function of this camera is not working right.

A bit more info that may help, my Sony PSP normaly shows up as a mass storage device in Windows, in Ubuntu it works fine, but is seen as an MP3 player, and Ubuntu launches an audio program.  Not really all that abnormal, but I don't have a single mp3 on the device. It does allow me to view the device as a harddisk, and therefore all the files on it.  Is there a way to force Ubuntu to see my camera as something else in order to make the files accessible?

Thanks,  Jameth

---

### Post by Jameth on 2006-06-15
So I'm not trying to beat a dead horse here, but this issue seems like it should be such a simple fix.  Mass Storage is a very common type of connection!  I cannot be the only person with this issue, and I am sure I am not the only person that this is a very important daily task! 

Again I could care less about the Mass Storage, if I could just get the RAW files off the camera through PTP or Pictbridge.  Another annoyance of PTP and Pictbridge is that it doesn't seem to delete the jpg photo's from the camera, even when told to do so.  In addition to that if I actually tell gtkam to DELETE the selected images from the camera, it acts like it is, but they are all still there, un scathed.

I can do without extensive gaming, I can do without Photoshop and Dreamweaver, but I CANNOT go without being able to get these raw images from my digital camera!

Please someone, there has got to be a solution!

Thanks again,
Jameth

---

### Post by bluenova on 2006-06-16
It might be worth getting a card reader, you can pick them up very cheaply. Although my 350D is detected fine, I still use a card reader as it's quicker than loading the pics directly from the camera for some reason.

---

### Post by Jameth on 2006-06-20
Yea, I do have a card reader, I have not tried it yet, but assume it will indeed work fine.  

However, my camera has Sony Memory Stick, as well as Compact Flash 2 capability, at the same time.  In addition to that, I use both, a 4GB microdirve in the compact flash slot, and a 1GB Sony Memory Stick.  It is MUCH MUCH easyier for me to just plug my camera into the computer, and retrieve everything from both sticks.  

To be honest, I have ALLWAYS found it easyier to just plug the camera in and get them through the camera.  As small as flash media is these days, why would one want to fumble around with pulling it out of the camera and sticking it in something else and back again every time you want to retrieve some pictures.  I keep a mini USB cable hanging out on my desk that is allways plugged in, right next to my cameras power cable. 

So is this just a lost cause or what?

Thanks again
Jameth

---

### Post by nmsa on 2006-07-07
I have an AMD64 arch and Ubuntu Dapper for amd installed.
I can't see at all my camera with or w/o the gtkam.
all I can see from dmesg is:
[ 2347.986326] usb 2-9: new high speed USB device using ehci_hcd and address 6

I have the same problem when I run kubuntu in a vmware session or Ubuntu (i386 arch)

When I run XP on vmware I can see the camera and ca get the files from it

](*,)

---

### Post by Jameth on 2006-07-07
I have still not found a solution for this!  I have tried it across 3 different Ubuntu machines, all running Dapper, and the same thing happened on all of them.  Two of them were Intel chipsets, and the other is a VIA C3 integrated mini-itx setup.

For the time being I have upgraded my windows dektop, and it makes a better platform for my RAW photo work, mainly because its much faster than my laptop.  Nonetheless, I would really still like to have this figured out!


Thanks again,
James

---

### Post by todal on 2006-09-14
hmm yes ur are right. ur not the only one with that problem... I found no solution. But maybe one day it will work. I Guess that this is a simple prob, too. gtkam simply doesn't search for .cr2 files, i guess. But how can i change it?

---

### Post by todal on 2006-09-14
Lol sorry.

I am just a nerd without being a nerd... No crying and screaming helps? Maybe USING(no "i thought i used it before" -> use it!) gtkam helps? I guess most of the people who got problems with raws will find affinities in this situation.

Mh, here is my X (Digikam whatever) and i am new to ubuntu or to linux at all furthermore i want to transfer raws without a Cardreader. All ppl are telling me to use gtkam, and i am! Am i? No i am NOT using it. I found a hint on a german tut.
For default when ur connecting ur Cam gthumb will be activited. Thats the point i didn't recordgnized. Jump into 
System->Settings->Media or how its calld (in most cases the las option) Theres a rider (are u english guys calling it like that? :confused:  ) Cameras. And well, theres the ape in the cornfield. earse the commandline an type in "gtkam" an well... u will see if i am right. Connect your 350D or whatever turn it in ptp mode, fire it on. Now u r able to all files an folders...

Hope it helps.

---

