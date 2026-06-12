---
title: "Firefox freezes usb mouse??"
date: 2006-06-18
forum: Desktop Environments
---

### Post by frank_y on 2006-06-18
I have both the xfce and gnome desktops installed on my laptop and I have a usb mouse plugged in as well as a touchpad. Normally I can control the mouse pointer with both.

Sometimes, for no reason, but always while I am using firefox, the usb mouse will suddenly lose control and I'll only be able to control the pointer with the touchpad. However, the mouse still lights up when I move it (it's an optical mouse) and it still shows up when I do lsusb so its still connected, but it just doesnt do anything.

The other weird thing is that when I try to restart gnome or xfce or if I try to restart the computer or log out of my session the computer will freeze.

This started after I updated to the new kernel but I'm not sure if that's the issue.

Any ideas?

---

### Post by cwmccabe on 2006-06-19
I think I might have the same issue, though I haven't pinned it to Firefox yet.  At seemingly random times my USB optical mouse freezes just as you described, but I can still use the touchpad to move the pointer.  I have usually been able to restart the computer, but sometimes when I restart it will freeze like you described.

However, just last night I found a related problem.  I was importing photos from a camera over a USB cable when the mouse-freeze happened.  When this happened the photo importing also froze.  So I think this might be a problem that is more general to attached USB devices and not just the mouse.  Do you have any other USB devices plugged in that you can test with?

My system: Toshiba Satellite L25-S119, running Dapper.  My mouse is a Logitech optical wheel mouse.

Does anyone know if there is a way to restart the USB system without having to restart the whole computer?

**Edit**: I found some info in this thread that seems to apply to my problem, but not enough time has passed yet for me to be sure that I've fixed the problem: [http://ubuntuforums.org/showthread.php?t=189572&highlight=usb+freeze](http://ubuntuforums.org/showthread.php?t=189572&highlight=usb+freeze)

---

### Post by empthollow on 2006-07-08
i have the same problem.  i lose my mouse at random times, i haven't been able to pin it to anything except maybe 3d (fglrx in my case).  i've tried about 10 distros and they all do it.  i was using knoppix 4.0 on my toshiba l25-s119 and every time i installed ati drivers i had this issue.  when i finally found a way to get ubuntu to run on my laptop (breezy at the time) the problem went away.  but since the upgrade to dapper - which i love- i started having this problem again.  sometimes worse than others and completly unpredictable.  my system freezes on shutdown as well, just as you have mentioned.  i can confirm that it is a general usb problem and not just a mouse issue as i have tried to plug my thumb drive in after the mouse stopped working and the computer did not recognize it.

---

### Post by cwmccabe on 2006-07-09
I think I've solved the problem on my system.  See here for some comments by myself and others with the same problem: [http://ubuntuforums.org/showthread.php?t=151916&page=2](http://ubuntuforums.org/showthread.php?t=151916&page=2)  Hopefully it will work out for you!

---

### Post by empthollow on 2006-07-13
i too have noticed the problem goes away when i use the "ati" driver however i can't afford to lose my 3d.  i tried modifing my .sh file for powernowd but my system wouldn't even boot.  i backdated the fglrx driver one release and the problem is not as severe but the problem is far from gone.

---

### Post by cwmccabe on 2006-07-13
I noticed recently that there was an update to fglrx.  Did you get this update, and if so did it help at all?  I have shrugged back into ati since 3D isn't crucial for me, but I was curious if this update fixed the problem.

---

### Post by empthollow on 2006-07-13
i backdated because the update caused more frequent usb freezing. i wish i could say otherwise.

---

### Post by empthollow on 2006-08-01
i recently found that using an old kernel can solve this problem (so far anyway) i am using the fglrx driver with 3d direct rendering.  so far i have not had any problems losing usb with kernel 2.6.15-23-686.  it has been about 3 days. with the most current kernel i lost my mouse (and all usb) almost immediatly after boot.

---

