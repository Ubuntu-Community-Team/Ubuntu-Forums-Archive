---
title: "Display sometimes unusable in 8.04"
date: 2009-01-07
forum: General Help
---

### Post by teust on 2009-01-07
Hi Bit of a newb and having issues with my display, see pic.  Can I do anything to resolve this?

I have an nvidia graphics card.  The drivers are nvidia also and report being the latest drivers available.  Sometimes there is no problem but sometimes it's a mess!!

[IMG]http://tom.eustace.net/ubuntu_ss/Screenshot.png[/IMG]

---

### Post by hangfire on 2009-01-07
> **teust said:**
> I have an nvidia graphics card.  The drivers are nvidia also and report being the latest drivers available.  Sometimes there is no problem but sometimes it's a mess!!

Wow.

Have you tried both the Open Source "nv" and the proprietary "nvidia" X drivers?

If both do similar things, you probably have some bad hardware in there somewhere.

-HF

---

### Post by teust on 2009-01-10
I'll try updating the drivers.  I found the latest drivers and downloaded them from here, [http://www.nvidia.com/object/linux_display_ia32_180.22.html](http://www.nvidia.com/object/linux_display_ia32_180.22.html).  When I try to run this I get an error because xserver is currently running.  Can I update the drivers through synaptic? or using apt-get? 

Don't think it can be hardware as windows runs fine.

Thanks
T

---

### Post by teust on 2009-01-10
I installed Envy in the end and installed updated os drivers, everything went swimmingly.  However I still have the same problem as before.  The room I am working in is quite cold, could that be an issue?  Any other ideas??

Thanks
T

---

### Post by hangfire on 2009-01-12
> **teust said:**
> I'll try updating the drivers.  I found the latest drivers and downloaded them from here, [http://www.nvidia.com/object/linux_display_ia32_180.22.html](http://www.nvidia.com/object/linux_display_ia32_180.22.html).  When I try to run this I get an error because xserver is currently running.  Can I update the drivers through synaptic? or using apt-get? 

Don't think it can be hardware as windows runs fine.

Thanks
T

The nvidia proprietary drivers from their website need to installed when not in X mode.

This is done by going to INIT level three

```
sudo init 3
```

Killing X with **Ctrl-Alt-Backspace**,

Going to an alternate console using **Control-Alt-F1** (or F2, etc),

logging in there in text mode, and then following the install instructions. Reboot when done.

-HF

---

### Post by hangfire on 2009-01-12
> **teust said:**
> I installed Envy in the end and installed updated os drivers, everything went swimmingly.  However I still have the same problem as before.  The room I am working in is quite cold, could that be an issue?  Any other ideas??

Thanks
T

Computers usually like cold, as long as it is non-condensating (not damp).

Refresh rate is the only other thing I can think of. Try to fix it at 60Hz.

-HF

---

### Post by teust on 2009-01-17
set the refresh rate to 60hz, still have the same problem.  I have a dual boot with XP, none of these issues on XP, so I don't think it can be hardware.  It's doing my head in.  One thing I've noticed is that if it is getting bad, I change resolution, then change back and it is fine for awhile.  :confused:

---

### Post by teust on 2009-02-01
I'm still stuck with this problem.  It does seem to happen when it is cold!!  Anyone any ideas, besides turning up the heat.  I just upgraded to Intrepid also.

---

### Post by teust on 2009-02-05
I am currently using VGA, I hava a dell fp207 LCD that also has a DVI connection.  I tried this to see if it would be better, but I get no signal, or signal out of range error.  From what I've read I need to edit the display .conf file.  Anyone suggest how this file should be updated??

Thanks

---

### Post by neu2buntu on 2009-02-05
run this in terminal

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

this will update the /etc/X11/xorg.conf file

---

### Post by teust on 2009-02-06
thanks, I tried your suggestion but it didn't seem to change things.  I still have the display issue and dvi is still not being picked up, though dvi cable is connected and works fine in windows!!

---

### Post by teust on 2009-02-07
Hooray. I'm connected with DVI and the problem has gone away.  

Of course things aren't that easy.  I've now lost the ability to use desktop effects and themes!!

??

---

### Post by neu2buntu on 2009-02-07
how did u solve the problem?

---

### Post by teust on 2009-02-08
It appears I spoke to soon. the problem returned.  I thought the switch to DVI had done it (no idea why!!).  After more digging the problem only seems to occur when I use the Compiz window manager.  I switched to Metacity and there's no problem, so far.  May be a bug with Compiz.  Kind of sucks as I'd like to use desktop effects.  I might try uninstalling Compiz and re-installing.  Are there any other window managers I could use??

---

### Post by teust on 2009-02-08
Ok, now the title bar is missing from all my windows!!! No Minimize, Maximise or close buttons. yikes!!

---

### Post by neu2buntu on 2009-02-08
u r having major problems...lol..   maybe try >right click anywhare on blank space on desktop > change desktop background > themes  ... and change your theme to see if this helps or try this post here > [http://ubuntuforums.org/showthread.php?t=1001223 ]("http://ubuntuforums.org/showthread.php?t=1001223")

---

### Post by teust on 2009-02-09
Thanks, I've fixed that problem.  I've done some more trouble shooting and it appears that the problem is being caused by Compiz.  When I switch to Metacity I don't see the problem.  Maybe I need to find an alternative to Compiz.  Any recomendations for alternate window managers?  Preferably with desktop effects.

T

---

### Post by teust on 2009-02-28
Still have this issue, after living with it for a few weeks I've discovered that it is not related to window managers.  Everytime I start up I have to select System>Administration>NVIDIA X Server Settings and perform a resolution change, which I then cancel.  Once this is done I don't get any issues, if I don't do this I can't do anything as the display is a total mess.

Can someone tell me a) how I can fix this or b) is it possible to write a script that would run on startup and do the steps described above?

Thanks

---

### Post by neu2buntu on 2009-02-28
one way that might work is to use "top" to find out the commands that run when you do your "steps described above" . just look carefully at the changes that show in top and jot the commands down, then add these commands to the startup applet in > system > preferences > sessions. 
  here is the top command ```
top -c -d 10
``` -c shows the commands running and -d is the time in seconds that top is updated( change this to a longer time if needed)  you may also have to maximize or stretch the top window as some commands are long!!!

---

### Post by teust on 2009-03-03
Thanks for that, though I don't think I'll go down this route as it seems to reoccur even after doing this.  This is really bugging me, considering ditching and heading back to windows ;(

---

### Post by teust on 2009-03-28
OK, the weather heated up here for a bit and the problem went away.  Going through a cold spell here now and the problem has returned!!!

---

