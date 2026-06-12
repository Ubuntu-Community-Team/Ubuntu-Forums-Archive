---
title: "Mythbuntu 9.04 and HVR-1600"
date: 2009-04-28
forum: General Help
---

### Post by MarioHTPC on 2009-04-28
HI
 
I install the new MythBuntu 9.04 on my system ( Gigabytes motherboard Asus GF videocard Intel E5200 CPU 4 gb memory HVR-1600 tuner) I can use the HVR-1600 digital tuner but the analog one does not work. I can scan the channel on mythtv but its not possible to record or watch tv with. I try it on VLC and its working well (I can see) I read the mythtv howto and i dont find why it does'nt work. :confused:
 
Thanks for your help. 
 
Mario.

---

### Post by Fast-Feet on 2009-05-10
I too am having an issue with this same card ( HVR-1600 ) and Mythbuntu 9.04.  I can not get the analog portion of the card to work at all.

9.04 included the proper firmware for HVR-1600 ( cx18 ) and the Kernel includes the driver for the card. So it seems I didn't have to do what was suggested here: [http://www.mythtv.org/wiki/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/Hauppauge_HVR-1600) .

I did have an issue with Mythbuntu going into low-graphics mode, but I got around that. So as far as I can see everything so be good to go, but it is not.

Please help.

FF

---

### Post by Fast-Feet on 2009-05-11
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

I got it!!!!!!! It was so simple too.. I feel a little stupid since I spent days (not hours) working on this. I did have it working with Mythdora 10.x but I found Mythdora playing the video very slow, as well it wasn't Ubuntu based. 

Anyways....  As I said before the Driver and firmware where already included with Mythbuntu 9.04, so I did not have to add them.

What you need to do is:

Go to the back-end of Mythbuntu 9.04. Then goto the Capture Cards section. 

I was originally trying the "**Analog V4L capture card**" setting. I was using it because the probed info was correct and I was able to do a channel scan. Video Playback did not work though; however,I remembered when I had Mythdora running I was using the "**MPEG-2 encoder card (PVR-x50, PVR-500)**" and though the probed information was there, I had to manually add the Video Device Location "/dev/video0". 

Well this "**MPEG-2 encoder card (PVR-x50, PVR-500)**" option was not included with Mythbuntu 9.04. So I ended up trying the next option which was: "**MJPEG capture card (Matrox G200, DC10)"**. Again the Probed information was present as well as the Video Device Location. This was so stupid on my part because I miss read MJPEG for MPEG. SO I ended up spending a great deal of time trying to get this to work without any success. After countless hours of Google I ended up posting here yesterday. After a nights rest and full day at work, I came home to properly read the Encoder cards.  _So, The way I got this working was to select the proper capture card type: "**IVTV[COLOR=DarkOrchid] MPEG-2[/COLOR] encoder card**"_. 

I feel a little ridiculous now, but at the same time I am very happy to get this working.

Hope this helps you MarioHTPC and anyone else struggling with getting this card, Mythbuntu 9.04 working together.


--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


One more thing that I was struggling with was with Mythbuntu going to a Low-Graphics Mode when using this card with my Nvidia Card. 

Here is how I got that working:

Open a terminal and edit /boot/grub/menu.lst. Add **vmalloc=192M pci=nommconf** on the kernel line like this:  ```
## ## End Default Options ##

title   Ubuntu 8.10, kernel 2.6.27-7-generic
root    (hd0,1)
kernel  /boot/vmlinuz-2.6.27-7-generic root=UUID=f70a49f8 ro quiet splash **vmalloc=192M pci=nommconf**
initrd  /boot/initrd.img-2.6.27-7-generic
quiet

 
```--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Now I need to get my newly received Logitech diNovo Mini Keyboard and My USB WiFi card working with this setup. ([COLOR=DarkRed]update: Works out of the box with out a hitch[/COLOR])

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

FF

---

### Post by jimig1 on 2009-05-11
Thanks for the info on this i have spent about 2 days trying to get this to work and i got the digital working great but analog has problems with the video it looks like crap on some stations setup any ideas?

AMD 2200+
HVR-1600
2 Gigs Ram

---

### Post by Fast-Feet on 2009-05-12
When you say it looks like crap... could you expand on that?  What do you mean. Blurry, snowy, or garbled or something?

FF


:KS PS: Moderators; could you move this thread to the Mythbuntu Forum. :KS

---

### Post by mrviper100 on 2009-05-12
Thank you Fast-Feet!!!  Thank you, Thank you!!  =D>

I have been trying for the last three days beating my head to the wall!!

I had to pick the default choice, and then go back and choose "IVTV MPEG-2 encoder card".

It works!!!  I almost gave up.

Thanks again for sharing your fix.

---

### Post by Fast-Feet on 2009-05-13
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[B]
No problem! [/B]8-)


Also if you folks are BOXEE fans, here is how you can add the Boxee Application into MythTV.


[http://www.greenhughes.com/content/installing-boxee-mythbuntu](http://www.greenhughes.com/content/installing-boxee-mythbuntu)

---

### Post by jimig1 on 2009-05-13
I got it looking better i think there was just something wrong with my cable at the time i got it working but it was kind of snowy. Thanks again for the help.

---

### Post by MarioHTPC on 2009-05-14
Thanks for your help Fast-Feet.  
 
But in my instalation the 'IVTV MPEG-2 encoder card' give me a 'could not open to probe its inputs" I dont understand why. maybee there is diferent version of this HVR-1600 card. ( if i know before it was as difficult o make this card work i certainly buy an other model)  I retest the ' Analog V4L capture card' and its possible to scan, the scan find all  my analog channel but when i try to watch or recorded i receive an 'error was encountred while displaying video'  
 
I attach the page 1-4 of the 17 page log file  is my mythtv error log file I try to understand it but after I read it I dont understand where to watch and wath to try.
 
Thanks
 
MarioHDTV
 If it was easy it was not fun.......

---

### Post by mrviper100 on 2009-05-14
I had the same issue.  Select "MJPEG capture card (Matrox G200, DC10)" and go ahead by clicking "Next" then go back and select the "IVTV" option.

---

### Post by MarioHTPC on 2009-05-15
Hi
I try this and its always 'Could not probe'. Maybee i try too much to update the firmware and I will reinstall this weekend and try again....... 
 
Could someone with this card working can send his log so i can see what is my configuration problem. 
 
 Thanks.

---

### Post by Fast-Feet on 2009-05-15
Try selecting the IVTV option and manually add the following to the "**Video Device**" line:

**[SIZE=4]/dev/video0[/SIZE]**[SIZE=4][SIZE=1]

[SIZE=2]Then save it.

FF
[/SIZE][/SIZE][/SIZE]

---

### Post by MarioHTPC on 2009-05-15
Yes , Yes, Yes Yes,........Yes 
Yes It work now i can see my channel...:popcorn:. Thanks Fast-feet and mrviper100.
 
But the first video is like 1 image each 3 second . do you have these problem also or its another trick to know to well adjust these card.
 
After these first video capture everything is good. I will try to add the scrip i see on [[COLOR=#444444]http://www.mythtv.org/wiki/Hauppauge_HVR-1600[/COLOR]]("http://www.mythtv.org/wiki/Hauppauge_HVR-1600") 
 
by the same time I will edit the mythtv page to wrote what to do for this HVR-1600.
 
PS I also have an nvidea video card a 8400gs and i dont have the low video message I will try to make the same change you make Fast-feet and see if the video is better.
 
Thanks all.

---

### Post by Fast-Feet on 2009-05-16
You're welcome.   

Yes, I am also getting very slow video at first. Not sure why. This is my very first MythTV experience. I assumed it was because it was recording/buffering video, but I don't know. 

Is it normal for MythTV to record programs automatically when I go to "Watch TV" ? I have been noticing that my hard drive /storage space is filling up, and when I view "recorded programs" in MythTV is shows a whole bunch of recordings of things I've allready just watched live. Is this Normal? If not how do I stop it?

FF

---

### Post by rockwellkc on 2009-11-20
Hi,
I just got my HVR-1600 and upgraded Ubuntu from 8.04 to 9.04 as I see here people saying that 9.04 has the cx18 driver included.
But somehow I don't see the driver detecting the card.
From lspci -v, I see the following lines:

00:09.0 Multimedia video controller: Conexant Systems, Inc. Device 5b5a
        Subsystem: Hauppauge computer works Inc. Device 7444
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at e8000000 (32-bit, non-prefetchable) [size=64M]
        Capabilities: <access denied>


I don't see  the "Kernel driver" and "Kernel modules" line showing.

From "dmesg", I don't see the cx18 lines at all.

After playing around with modprobe mentioned here

[http://www.gossamer-threads.com/lists/ivtv/devel/39058](http://www.gossamer-threads.com/lists/ivtv/devel/39058)

I am now seeing this from lspci -v:

00:09.0 Multimedia video controller: Conexant Systems, Inc. Device 5b5a
        Subsystem: Hauppauge computer works Inc. Device 7444
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at e8000000 (32-bit, non-prefetchable) [size=64M]
        Capabilities: [44] Vital Product Data <?>
        Capabilities: [4c] Power Management version 2

# lsmod | grep cx
cx18                  115520  0
dvb_core               92032  1 cx18
videodev               41600  1 cx18
compat_ioctl32          9344  1 cx18
i2c_algo_bit           14084  1 cx18
cx2341x                20996  1 cx18
v4l2_common            20992  2 cx18,cx2341x
tveeprom               20100  1 cx18

dmesg:

[  209.939406] Linux video capture interface: v2.00
[  209.970479] cx18:  Start initialization, version 1.0.1
[  209.970544] cx18:  End initialization


I still don't see that the driver detects the card.
Should there something showing in dmesg by the driver when the card is detected?

Thanks.

---

### Post by rockwellkc on 2009-11-20
By the way, what version of mythtv do you use?
I'm using mythtv-0.20.2 and don't seem to see IVTV card.
Thanks.

---

