---
title: "SOLVED: XPS M1330 Hardy: UVC module fails to initialize webcam"
date: 2008-05-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by argotnaut on 2008-05-13
(x-posted from [http://www.dellcommunity.com/supportforums/board/message?board.id=sw_linux&thread.id=13835]("http://www.dellcommunity.com/supportforums/board/message?board.id=sw_linux&thread.id=13835"))

---
I did a clean install of Hardy on an XPS M1330 with the thin display/UVC webcam. It worked fine in Gutsy, but now it won't work at all. Here's the relevant section of dmesg output:

```
 
    [   20.719793] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:7670)
    [   20.720088] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
    [   20.720337] uvcvideo: Failed to query (129) UVC control 1 (unit 0) : -32 (exp. 26).
    [   20.720340] uvcvideo: Failed to initialize the device (-5).
    [   20.720371] usbcore: registered new interface driver uvcvideo
    [   20.720374] USB Video Class driver (v0.1.0)
```

---

Found more information on the problem here: [http://developer.berlios.de/feature/?func=detailfeature&feature_id=3737&group_id=5681]("http://developer.berlios.de/feature/?func=detailfeature&feature_id=3737&group_id=5681")

---

And fixed it by installing the latest UVC module from svn:

1. install prereqs if you don't have them

    ```
sudo aptitude install subversion build-essential
```

2. back up current module, just in case

   ```
sudo cp /lib/modules/2.6.24-16-generic/ubuntu/media/usbvideo/uvcvideo.ko /lib/modules/2.6.24-16-generic/ubuntu/media/usbvideo/uvcvideo.ko.bak
```


3. Check out latest source code

   ```
svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
```


4. go to the 'trunk' directory

   ```
cd trunk
```


5. Edit Makefile

    ```
nano Makefile
``` (or use gedit or whatever you like)

6. Change the line starting with INSTALL_MOD_DIR to this:

```
INSTALL_MOD_DIR := /lib/modules/$(KERNEL_VERSION)/ubuntu/media/usbvideo
```

7. Install it

```
make

sudo make install
```


8. Reboot (you could also unload the old module and load the new one, but I didn't remember the command off the top of my head, and I'm lazy)

 

dmesg still gave me a "Failed to query" line (see below), but everything works now! Tested in Cheese and Ekiga.

```

[   20.749569] Linux video capture interface: v2.00
[   20.822180] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:7670)
[   20.822549] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[   20.870964] input: PC Speaker as /devices/platform/pcspkr/input/input13
[   20.881187] usbcore: registered new interface driver uvcvideo
[   20.881192] USB Video Class driver (v0.1.0)
```

---

### Post by akniss on 2008-05-13
That's odd... I have a m1330 with LED backlight screen and VGA webcam and I didn't have to do anything. My webcam works out of the box (tested on Ekiga and Skype) on Gutsy and with a fresh install of Hardy.

---

### Post by primski on 2008-05-14
I have an Inspiron 1525 and whenever i resume laptop from suspend, there is some UVC error for a brief moment I haven't catched yet, and the computer beeps 3, 4 times very loudly and then unsuspends normally. Webcam works though.  

Will try compiling the new UVC module, and see it that makes any difference.

---

### Post by Keyper7 on 2008-05-14
Heh, didn't test Hardy yet, but I think Gutsy on my Vostro 1400 is the weirdest case around here: sometimes it works, sometimes I get the exact same error argotnaut posted. It seems completely random. This smells of race condition.

---

### Post by ameeno on 2008-07-07
Wow.. this worked. Thanks!!!!!!!!!


didnt know why my webcam wasnt working before this.


ok just a tip to everyone to save a few mins

the remove command is 

sudo modprobe -r uvcvideo


then do

sudo modprobe uvcvideo

to reactivate the moded file.. there we go all works well!

---

### Post by DiabolusItalicus on 2008-07-07
Well, argotnaut, believe it or not, your crystal clear instructions also solved the problem I was having with the integrated webcam of my Dell 22" monitor SP2208WFP!!!

And thanks also to ameeno for saving me a reboot...

Thanks guys for proving me every single day how abyss-deep my knowledge of Linux and Ubuntu is, and even more thanks for relieving it with your sky-high knowledge!!!

Regards from Italy, and may Ubuntu and its community live forever.

---

### Post by Thorndog on 2009-10-11
I'm running Jaunty and after numerous attempts can get the webcam going by toggling modprobe -r and back again a few times like someone mentions here in the forums, not really a good sign I think!. I cannot seem to use the microphone though. 
Any suggestions re maybe using ndwiswrapper or some generic mod to enable usb mic since I can see the usb hub.
output from dmesg
            
[   15.770954] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05                  
[   15.771105] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0460)                                                                           
[   15.771174] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)             
[   15.778802] uvcvideo: Found UVC 1.00 device Monitor Webcam (SP2208WFP) (05a9:2643)                                                                           
[   15.779158] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).                                                                          
[   15.779401] uvcvideo: Failed to query (129) UVC control 1 (unit 0) : -32 (exp. 26).                                                                          
[   15.779405] uvcvideo: Failed to initialize the device (-5).                  
[   15.779458] usbcore: registered new interface driver uvcvideo                
[   15.779488] USB Video Class driver (v0.1.0)                                  
[   15.793398] logitech 0003:046D:C517.0002: fixing up Logitech keyboard report descriptor                                                                      
[   15.794197] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/input/input7    

for what that's worth.
I downloaded drivers and have it all working under XP but I don't want to have to boot into xp to use Skype.

---

### Post by Dangger on 2009-10-25
I'm using karmic and my webcam stopped working. I have no 

[HTML]uvcvideo.ko[/HTML] 

file in 

[HTML]/lib/modules/2.6.24-16-generic/ubuntu/media/usbvideo/[/HTML]

**it is instead in:**

[HTML]/lib/modules/2.6.31-14-generic/kernel/drivers/media/video/uvc/uvcvideo.ko[/HTML]


Backup would be:

[HTML]sudo cp /lib/modules/2.6.31-14-generic/kernel/drivers/media/video/uvc/uvcvideo.ko /lib/modules/2.6.31-14-generic/kernel/drivers/media/video/uvc/uvcvideo.ko.bak[/HTML]

INSTALL_MOD_DIR:

[HTML]INSTALL_MOD_DIR := /lib/modules/$(KERNEL_VERSION)/kernel/drivers/media/video/uvc[/HTML]


**Gonna wait until the final version of Karmic and if it's not solved on its own I'll try this method and report back. **

[B]UPDATE:

My issue is fixed. I installed Cheese, rebooted and it's fine. I did not follow the instructions here, I don't want to hijack the thread or anything but since it's working now I just wanted to let people know. [/B]

---

### Post by DiabolusItalicus on 2009-11-10
> **Dangger said:**
> I'm using karmic and my webcam stopped working. [...]
[B]UPDATE:

My issue is fixed. I installed Cheese, rebooted and it's fine. I did not follow the instructions here, I don't want to hijack the thread or anything but since it's working now I just wanted to let people know. [/B]
Hi Dangger,
I just updated to Karmic as well, and decided to take it up very seriously with the little b*****d webcam... (drum rolls, please!) for the first time ever since I bought my Dell monitor SP2208WFP (March 2008), its integrated webcam FINALLY STARTED TO WORK!!!

Now, the problem is that I'm totally unsure of how I did it... I mean:

[LIST]
[*]After reading your post, I immediately tried to install Cheese, following our input: didn't work.
[*] I then tried to modprobe -r/modprobe the uvcvideo kernel module, but the Koala replied to both commands with a (error?) message:
```
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
WARNING: All config files need .conf: /etc/modprobe.d/nvidia-kernel-nkc, it will be ignored in a future release.
```
so, given my abyss-deep knowledge of Ubuntu (and Linux) secrets, I simply didn't understand if I was actually succeeding in unloading/reloading the module.
[*] I came back to Cheese to close it and restart it and... magic magic, I was there on my monitor, looking at myself in total amazement!!!
[/LIST]
So, I have to conclude that, in spite of the cryptic (to me) Koala's messages, modprobing -r and re-modprobing the uvcvideo module actually seemed to work.
Let's see what will happen at the next restart...

Sweet dreams to all (almost midnight here).

---

