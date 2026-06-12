---
title: "webcam not working after upgrade to Ibex"
date: 2008-11-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bigbrovar on 2008-11-01
My dell xps m1330 came preinstalled with hardy heron. and even i replaced the preinstalled ubuntu with a fresh install my webcam still worked .. but after upgrading to ibex  ( clean install) whenever i start cheese the indicator light shows up that the cam is on. but no image displays on cheese it just shows blank and after a while hangs till i forcefully close it. same when i tried skype i ran a test of my video device and got the same result .. cam indicator light cam on by no video dispay. 

[IMG]http://farm4.static.flickr.com/3218/2990531481_fbca543b6e_o_d.jpg[/IMG]


[IMG]http://farm4.static.flickr.com/3046/2990531479_88c12db1c7_o_d.jpg[/IMG]

---

### Post by Shrikaant on 2008-11-01
Same problem with my Dell-1525. The webcam works fine in AMSN however...

---

### Post by madarcher on 2008-11-01
I also have a Dell 1525n and my webcam has stopped working.  Cheese and aMSN say it's not connected and lsusb, lspci, and lshw seem to show no trace of it.  It did work fine in hardy.  I upgraded via update-manager.

---

### Post by eldragon on 2008-11-01
###### EDIT ###########
this might not fix it for you, double checked and i dont think it applies to you.. anyway, no harm done, first run skype from the terminal with the line below, if it works, keep on applying the workaround.
######################

you need to start skype with the following command:
```

$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype

```

that will make your webcam work again.

running skype this way is a pain. so i created a special launcher for it, till skype fixes the problem...

to do this:
```

sudo vi /usr/local/bin/skype

```

and add these two lines:
```

#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype

```

save and quit.

next: make it executable:
```

$ sudo chmod a+x /usr/local/bin/skype

```

done :D

good luck

---

### Post by ericoc on 2008-11-01
I've got a Dell Studio 15 and have a similar problem.

Cheese has no video and when I try to close it, I have to force quit.
The light comes on like the camera is working, but the video stream doesn't show up.

xawtv works perfectly fine (video shows up), but when I try to close it, it freezes, and I have to kill -9 it.

Skype works perfectly fine though, without needing the LD_PRELOAD prefix...


All of the above worked great on Hardy before upgrading to Intrepid

---

### Post by digistyl3 on 2008-11-01
I think it's this bug:
[https://bugs.launchpad.net/ubuntu-release-notes/+bug/290506](https://bugs.launchpad.net/ubuntu-release-notes/+bug/290506)

---

### Post by iaskedalice09 on 2008-11-01
I have the same problem. The light flashes so it's recognised, but Cheese comes up blank, and I've gotta force quit it.

I just use Cheese for the webcam.

Dell Inspiron 1525n/preloaded.

No luck on the Dell Linux Wiki.
And I don't get launchpad, how do you use it?

---

### Post by Tyche on 2008-11-01
One suggestion from someone with a Dell Mini 9.  I couldn't understand why the webcam didn't work in cheese (I thought it was a bit cheesey.  Hee hee)  Then I clicked on the "Video" button instead of the "Photo" button.  Son-of-a-gun!  It worked.

---

### Post by iaskedalice09 on 2008-11-01
> **Tyche said:**
> One suggestion from someone with a Dell Mini 9.  I couldn't understand why the webcam didn't work in cheese (I thought it was a bit cheesey.  Hee hee)  Then I clicked on the "Video" button instead of the "Photo" button.  Son-of-a-gun!  It worked.

Sorry, but this didn't work for me. I hope it works for someone else, though!

---

### Post by zoomy942 on 2008-11-01
this sequence works for me after it acts like all of yours.

install amsn, install cheese.  
open cheese and set the res to 800x600
close cheese
open amsn
connect to someone and open the cam - after doign the wizard - it will work
then cheese should work fine too.

---

### Post by iaskedalice09 on 2008-11-01
> **zoomy942 said:**
> this sequence works for me after it acts like all of yours.

install amsn, install cheese.  
open cheese and set the res to 800x600
close cheese
open amsn
connect to someone and open the cam - after doign the wizard - it will work
then cheese should work fine too.

Cam worked with aMSN but didn't work with Cheese. Did the wizard and changed res. What to do?

---

### Post by zoomy942 on 2008-11-01
did you reboot yet?

---

### Post by iaskedalice09 on 2008-11-02
> **zoomy942 said:**
> did you reboot yet?

Just did...still no luck. Anxious to read your thoughts and solutions.

---

### Post by loell on 2008-11-02
try

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype 
``` for skype

or

```
 LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese 
``` with cheese

---

### Post by iaskedalice09 on 2008-11-02
> **loell said:**
> try

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype 
``` for skype

or

```
 LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese 
``` with cheese

Popped up Cheese with no image, same as before. Minimised cheese and got an error message from Terminal:

```

** Message: Error: Stream contains no data.
gsttypefindelement.c(785): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream


** (cheese:13084): WARNING **: could not generate thumbnail for /home/tom/Videos/Webcam/0003.ogv (video/ogg)

libv4l2: error requesting 4 buffers: Invalid argument

```

Thank you for your help!

---

### Post by zoomy942 on 2008-11-02
hmm..

I reloaded last night and did my steps and success!

what could be going on

---

### Post by merlinn31 on 2008-11-02
> **iaskedalice09 said:**
> Popped up Cheese with no image, same as before. Minimised cheese and got an error message from Terminal:

```

** Message: Error: Stream contains no data.
gsttypefindelement.c(785): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream


** (cheese:13084): WARNING **: could not generate thumbnail for /home/tom/Videos/Webcam/0003.ogv (video/ogg)

libv4l2: error requesting 4 buffers: Invalid argument

```

Thank you for your help!

I got the same 4 buffers message as you. I have a Dell Studio 1535.  I don't know anything about this webcam, and I can't figure out anything either.  gstreamer-properties locks up when I try to test video4linux2 on my "integrated webcam", and video4linux test doesn't even work.  I added my username to the video group, just in case.  I was then able to drop the resolution down to retardedly low, which lets me take craptastic videos and pictures.  I can't take it any higher though, or else it locks up.  

Maybe these will (sorta) work for you too.

---

### Post by merlinn31 on 2008-11-02
This seems to be my issue.  I guess I'll wait for the bug fix.

[https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/290506](https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/290506)

---

### Post by iaskedalice09 on 2008-11-02
OK, VLC Player works with the cam but I don't know how to capture pics and stuff with it. To save video go to Media > Convert/Save with your webcam on.

I just went to open capture device and hit enter.

Is there an alternative for Cheese?

---

### Post by Neffscape on 2008-11-03
So, what is clear is that this bug is related to Cheese and maybe the gstreamer platform. The webcam drivers are perfectly working, I wonder when a fix will be released for that!

---

### Post by eldersoares on 2008-11-04
it worked!!! but with the lowest quality... the image is terrible, very small and pixelated, i'm using it in 176x144. i changed in edit - preferences and every time i tried the change, the program freezed. but then when i forced closing and enter again, the setting was saved.

does anyone know how to make it work with a better res??? in skype it works perfectly.. in kopete, i can see it in the settings but i can't talk to anyone showing my camera

---

### Post by shingalated on 2008-11-07
Higher res would be really great.  I don't know why it would be worse in Intrepid...

---

### Post by iaskedalice09 on 2008-11-08
> **Neffscape said:**
> So, what is clear is that this bug is related to Cheese and maybe the gstreamer platform. The webcam drivers are perfectly working, I wonder when a fix will be released for that!
Agreed. Someone NEEDS to fix this!! I can't do it, but if someone does, I will forever refer to them as The One. Anyone up for it?

---

### Post by shingalated on 2008-11-11
Oh man...I fixed it!

---

### Post by Darrell Lawrence on 2008-11-11
> **iaskedalice09 said:**
> Agreed. Someone NEEDS to fix this!! I can't do it, but if someone does, I will forever refer to them as The One. Anyone up for it?

From what I've read of the bug reports over at launchpad and Gnome.org this bug is rather complex. It's going to take some time to get to the actual root cause. I saw the source code submitted for a fix, but it has been rejected at this point because it didn't work in all cases. It appears to be a combination of things. When the developers are sure that they have a true fix then we should see an update. 

We just have to be patient.

Darrell

---

### Post by iaskedalice09 on 2008-11-12
Hmm. I'll keep my fingers crossed.

Hopefully someone will post on here when a true fix comes up! :-)

---

### Post by zoomy942 on 2008-11-12
Here is your fix until the pathc comes out

1) bring up the console
2) enter these commands one after the other:

sudo apt-get install subversion
sudo apt-get install build-essentials (just in case)
svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
cd trunk
make

then run the following line as one (just copy and paste* everything within the quotation marks, this is one command):
"sudo install uvcvideo.ko -v -m644 /lib/modules/$(uname -r)/kernel/drivers/media/video/uvc/uvcvideo.ko &&
sudo make install &&
sudo cp -av /lib/modules/$(uname -r)/kernel/drivers/media/video/uvc/uvcvideo.ko /lib/modules &&
sudo depmod -ae $(uname -r)"

3) reboot
4) Enjoy your cheese ;)

---

### Post by butre on 2008-11-12
> **eldragon said:**
> 
you need to start skype with the following command:
```

$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype

```


Thanks, this makes my Logitech webcam (uses gscpa_spca561) work with Skype!

It's still broken when using Camorama but I only need the cam for Skype anyway :)

---

### Post by iaskedalice09 on 2008-11-12
> **zoomy942 said:**
> Here is your fix until the pathc comes out

1) bring up the console
2) enter these commands one after the other:

sudo apt-get install subversion
sudo apt-get install build-essentials (just in case)
svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
cd trunk
make

then run the following line as one (just copy and paste* everything within the quotation marks, this is one command):
"sudo install uvcvideo.ko -v -m644 /lib/modules/$(uname -r)/kernel/drivers/media/video/uvc/uvcvideo.ko &&
sudo make install &&
sudo cp -av /lib/modules/$(uname -r)/kernel/drivers/media/video/uvc/uvcvideo.ko /lib/modules &&
sudo depmod -ae $(uname -r)"

3) reboot
4) Enjoy your cheese ;)
**THANK YOU!!!** This fixed it for me! You are my hero and The One! ;-)

You did have a typo, it's build-essential, with no "s". But I already have it installed, so it didn't matter to me. THANK YOU SO MUCH AGAIN!!

---

### Post by zoomy942 on 2008-11-12
> **iaskedalice09 said:**
> **THANK YOU!!!** This fixed it for me! You are my hero and The One! ;-)

You did have a typo, it's build-essential, with no "s". But I already have it installed, so it didn't matter to me. THANK YOU SO MUCH AGAIN!!


you are very welcome!

---

### Post by hobbit55 on 2008-11-12
I have struck similar problems and went back to the Hardy Heron version of Kopete
. 
The problems encountered so far are:

1) Unable to start broadcast from camera  to any client. Doesn't even look like it is doing anything at all

2) I get this list of 99 users, which I had never had in my contacts and if you delete them, it goes offline and as soon as you go online it adds them all again. They are all yahoo users as far as I am aware.

Totally weird, so if anyone can help with anything, thhat would be cool. I am not a guru in the slightest but I do have a few brain cells working.

---

### Post by bigbrovar on 2008-11-15
> **zoomy942 said:**
> Here is your fix until the pathc comes out

1) bring up the console
2) enter these commands one after the other:

sudo apt-get install subversion
sudo apt-get install build-essentials (just in case)
svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
cd trunk
make

then run the following line as one (just copy and paste* everything within the quotation marks, this is one command):
"sudo install uvcvideo.ko -v -m644 /lib/modules/$(uname -r)/kernel/drivers/media/video/uvc/uvcvideo.ko &&
sudo make install &&
sudo cp -av /lib/modules/$(uname -r)/kernel/drivers/media/video/uvc/uvcvideo.ko /lib/modules &&
sudo depmod -ae $(uname -r)"

3) reboot
4) Enjoy your cheese ;)

seem they is a change in the command instead of ```
make
``` its now ```
make uvcvideo
```

---

### Post by loneowais on 2008-11-17
Same here on 1525...But I can use webcam in VLC.

And hey, mine was a fresh install..

---

### Post by MrSootentai on 2009-01-15
The methods to update the uvcvideo driver through subversion have worked perfectly for me. Thanks!

---

