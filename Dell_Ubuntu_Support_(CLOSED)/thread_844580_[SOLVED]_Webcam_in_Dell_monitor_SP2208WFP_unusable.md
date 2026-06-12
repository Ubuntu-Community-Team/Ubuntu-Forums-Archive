---
title: "[SOLVED] Webcam in Dell monitor SP2208WFP unusable in Ubuntu?"
date: 2008-06-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by DiabolusItalicus on 2008-06-29
A couple of months ago I bought a Dell XPS 420 with the Dell 22" SP2208WFP monitor, which includes a webcam.
In spite of all my efforts, however, I'm unable to get the webcam work in my beloved Ubuntu 8.04 64-bit (while it works fine under MS Vista): the monitor's webcam is detected, but the initialization fails.
I checked dmesg and found the following:
> [   51.898844] uvcvideo: Found UVC 1.00 device Monitor Webcam (SP2208WFP) (05a9:2643)
[   51.899238] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[   51.899487] uvcvideo: Failed to query (129) UVC control 1 (unit 0) : -32 (exp. 26).
[   51.899489] uvcvideo: Failed to initialize the device (-5).
Frankly speaking, I'm stuck. Any idea, anyone?
Thanks in advance, and regards from Italy.

---

### Post by DiabolusItalicus on 2008-07-07
I found a solution to this problem in another forum:
[http://ubuntuforums.org/showthread.php?t=793513](http://ubuntuforums.org/showthread.php?t=793513)

-----------------------------------

> **argotnaut said:**
> (x-posted from [http://www.dellcommunity.com/supportforums/board/message?board.id=sw_linux&thread.id=13835]("http://www.dellcommunity.com/supportforums/board/message?board.id=sw_linux&thread.id=13835"))

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

[COLOR="Red"][_**DiabolusItalicus' note**_: repeat the above command for all the kernel versions you have installed or intend to use the webcam with.
Just remember to replace "2.6.24.16" with your versions.
I have kernels 2.6.24.18 and 2.6.24.19 installed, so I repeated the above command twice adjusting kernel version as required.][/COLOR]

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

---------------------------------------

So far the instructions from argotnaut.

Now, instead of rebooting as originally indicated at 8. by argotnaut, simply follow ameeno's shortcut:

> **ameeno said:**
> Wow.. this worked. Thanks!!!!!!!!!

[...]

ok just a tip to everyone to save a few mins

the remove command is

Code:
```
sudo modprobe -r uvcvideo
```

then do

Code:
```
sudo modprobe uvcvideo
```

to reactivate the moded file.. there we go all works well!

---

### Post by sguaz on 2008-07-08
Wow!!! Diabolusitalicus,
you monster of precision, thank you very much for the excelent howto remake

---

### Post by strimmer on 2008-10-15
If you're still getting errors w/ the above tips like I was try the following which I pulled from cbrese's posting on this thread: [http://ubuntuforums.org/showthread.php?t=306340](http://ubuntuforums.org/showthread.php?t=306340)

Try adding a trace=15 to your modprobe:
sudo modprobe uvcvideo trace=15

---

### Post by Jack1980 on 2009-04-29
Hi,

I am newbee trying to install the drivers for the webcam on my Dell 22" SP2208WFP monitor. 
I am using ubuntu 9.04. I dont find any ubuntu folder under "/lib/modules/2.6.28-11-generic".
Do you have to do something different to install the drivers for this version of ubuntu?

Thanks

---

### Post by Vadi on 2009-04-29
Are you sure that the camera doesn't work with Cheese or other video programs already?

---

### Post by l_synapse_l on 2009-11-17
I have a Dell SP2208WFP with integrated webcam. I have 9.10 installed but it still isn't working even though the UVC site says it is officially supported!

dmesg | grep 'uvcvideo' gives -

```

[ 4480.641535] uvcvideo: Found UVC 1.00 device Monitor Webcam (SP2208WFP) (05a9:2643)
[ 4480.642044] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[ 4480.642292] uvcvideo: Failed to query (129) UVC probe control : -32 (exp. 26).
[ 4480.642296] uvcvideo: Failed to initialize the device (-5).

```

---

### Post by l_synapse_l on 2009-11-17
> **l_synapse_l said:**
> I have a Dell SP2208WFP with integrated webcam. I have 9.10 installed but it still isn't working even though the UVC site says it is officially supported!

dmesg | grep 'uvcvideo' gives -

```

[ 4480.641535] uvcvideo: Found UVC 1.00 device Monitor Webcam (SP2208WFP) (05a9:2643)
[ 4480.642044] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[ 4480.642292] uvcvideo: Failed to query (129) UVC probe control : -32 (exp. 26).
[ 4480.642296] uvcvideo: Failed to initialize the device (-5).

```

Ok. A little tinkering solved my problem. I downloaded the latest uvcideo tarball from [http://linuxtv.org/hg/~pinchartl/uvcvideo/](http://linuxtv.org/hg/~pinchartl/uvcvideo/)

```

make

sudo make install

modprobe -r uvcvideo

modprobe uvcvideo

```

Fixed my problem!

---

### Post by lamanabie on 2011-03-10
Hi guys .. i have microdia sonix USB 2.0 webcam in my acer aspire one 751h
my kernel log is:
[   16.478447] Linux video capture interface: v2.00
[   16.644424] uvcvideo: Found UVC 1.00 device WebCam (0c45:62c0)
[   16.647945] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[   16.648399] uvcvideo: Failed to query (129) UVC probe control : -32 (exp. 26).
[   16.648413] uvcvideo: Failed to initialize the device (-5).

I installed [http://linuxtv.org/hg/v4l-dvb/shortlog/1da5fed5c8b2](http://linuxtv.org/hg/v4l-dvb/shortlog/1da5fed5c8b2) this pack I hope that is uvcvideo ^^ ..
But webcam is still not working kernel log is same, but only one new think come up. 
When i try execute commad:
 modprobe -r uvcvideo
FATAL: Error removing uvcvideo (/lib/modules/2.6.35-27-generic/kernel/drivers/media/video/uvc/uvcvideo.ko): Operation not permitted
modprobe uvcvideo looks working fine. 

and my /dev/video* doesnt exist (caused probably because of kerner errors)
Any suggestions ?

---

### Post by kikushima on 2011-06-26
I'm not an absolute beginner, but let's say I don't understand everything in Linux.

I have tried to follow the steps given in this thread

I just can't get step 3 or 4 to work:
svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
cd trunk

Can someone please explain me how to solve this problem!!! I need my webcam.

Regards

---

