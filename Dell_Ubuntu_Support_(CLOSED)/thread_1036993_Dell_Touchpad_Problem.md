---
title: "Dell Touchpad Problem"
date: 2009-01-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ~farah_r~ on 2009-01-11
Hi, I am dual booting ubuntu and vista. My touchpad which works perfectly in vista does not respond properly in Ubuntu...it detects it, but does not respond like it should. I can connect and external mouse and that works perfectly in ubuntu though...any help on why touchpad doesnt track properly? Thanks, Farah.

---

### Post by Denny Johnson on 2009-01-12
farah,
Since you are not getting a more knowledgeable reply......I'll try to help........look in SYSTEM/PREFERENCES. Do you have a TOUCHPAD option there? If not, are there touchpad adjustments in the MOUSE option?

I found these posts helpful in the past:
[http://ubuntuforums.org/showthread.php?t=469639](http://ubuntuforums.org/showthread.php?t=469639)
[http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Changing_mousepad_settings](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Changing_mousepad_settings)

Good luck

---

### Post by ChaKy on 2009-01-12
> **~farah_r~ said:**
> Hi, I am dual booting ubuntu and vista. My touchpad which works perfectly in vista does not respond properly in Ubuntu...it detects it, but does not respond like it should. I can connect and external mouse and that works perfectly in ubuntu though...any help on why touchpad doesnt track properly? Thanks, Farah.

I had the same problem with Ubuntu and touchpad on Dell 1525, it was too slow, but this howto [https://help.ubuntu.com/community/SynapticsTouchpad/](https://help.ubuntu.com/community/SynapticsTouchpad/) help me.

---

### Post by ~farah_r~ on 2009-01-12
> **Denny Johnson said:**
> farah,
Since you are not getting a more knowledgeable reply......I'll try to help........look in SYSTEM/PREFERENCES. Do you have a TOUCHPAD option there? If not, are there touchpad adjustments in the MOUSE option?

I found these posts helpful in the past:
[http://ubuntuforums.org/showthread.php?t=469639](http://ubuntuforums.org/showthread.php?t=469639)
[http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Changing_mousepad_settings](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Changing_mousepad_settings)

Good luck

Thanks for the reply!

I tried both, but my xorg.conf file is not as mentioned in those two guides. This is what is in my xorg.conf file:

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Can I just append the code in those two guides at the end of my xorg.conf file? 

Thanks...

---

### Post by ugm6hr on 2009-01-12
> **~farah_r~ said:**
> Can I just append the code in those two guides at the end of my xorg.conf file? 

I don't think that works with Intrepid 8.10, due to the new X.

Follow this: [https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig](https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig)

---

### Post by ~farah_r~ on 2009-01-12
> **ugm6hr said:**
> I don't think that works with Intrepid 8.10, due to the new X.

Follow this: [https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig](https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig)

I had tried this earlier too...when I look at the shmconfig.fdi file, it already has that code in it, so I don't need to alter it...

I have a Touchpad menu in Control Center. When I clicked on it, I got the error message:
Gsynaptics couldn't initialize. 
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics.

Do I correct this error by following the steps mentioned in the previous guides by appending the code at the end of xorg.conf file?

---

### Post by ugm6hr on 2009-01-12
> **~farah_r~ said:**
> I had tried this earlier too...when I look at the shmconfig.fdi file, it already has that code in it, so I don't need to alter it...

In which case GSynaptics should work:

Check with:
```
synclient -m 100
```

Move you finger around pad - you should see numbers change.

Ctrl-C to stop.

If that works - install gsynaptics:
```
sudo apt-get install gsynaptics
```

That should add a menu entry to adjust the pad.

---

### Post by ~farah_r~ on 2009-01-12
> **ugm6hr said:**
> In which case GSynaptics should work:

Check with:
```
synclient -m 100
```

Move you finger around pad - you should see numbers change.

Ctrl-C to stop.

If that works - install gsynaptics:
```
sudo apt-get install gsynaptics
```

That should add a menu entry to adjust the pad.

When I did 
Check with:
```
synclient -m 100
```

it said:
Can't access shared memory area. SHMConfig disabled?

So I am guessing SHMConfig has to be enabled somehow in the xorg.conf file??

---

### Post by ugm6hr on 2009-01-12
> **~farah_r~ said:**
> So I am guessing SHMConfig has to be enabled somehow in the xorg.conf file??

Just confirm you are using 8.10 Intrepid before we go further.

I don't use 8.10 on my laptop, so am not 100% certain why this is not working for you.

That whole page is worth reading.

Also this: [https://wiki.ubuntu.com/X/Config/Input](https://wiki.ubuntu.com/X/Config/Input)

---

### Post by ~farah_r~ on 2009-01-12
> **ugm6hr said:**
> Just confirm you are using 8.10 Intrepid before we go further.

I don't use 8.10 on my laptop, so am not 100% certain why this is not working for you.

That whole page is worth reading.

Also this: [https://wiki.ubuntu.com/X/Config/Input](https://wiki.ubuntu.com/X/Config/Input)

Yes, I had tried the above link as it was mentioned in an earlier post, but it doesn't work for me either...

---

