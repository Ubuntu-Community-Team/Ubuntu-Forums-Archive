---
title: "Impossible to log in :("
date: 2009-04-01
forum: General Help
---

### Post by Baen on 2009-04-01
I just installed 8.10 and tried installing the same ATI drivers that'd worked perfectly in 8.04 (catalyst 9.3), but unfortunately it left the graphics so messed up I can't even log in in failsafe. 

Does anyone know how I can remove the driver?? I've got 8.04 still installed on a different partition, I dunno if I can uninstall the drivers from there...? I'm a complete and utter linux noob so I'm really fumbling in the dark without the shiny point-and-click interface. :)

---

### Post by coffeecat on 2009-04-01
Try booting up normally, and if you are dumped into a command console with a login prompt, fine. If not, press Ctrl-Alt-F1 and you'll get to the console login. Login and type:

```
sudo nano -w /etc/X11/xorg.conf
```Type in your password when prompted. In the simple text editor that opens, scroll down to the line that says 'Section "Device" ' and a couple of lines under that change the line that says:

```
     Driver     "something_or_other"
```to

```
     Driver     "vesa"
```Now save the modified file with Ctrl-O and exit with Ctrl-X and type

```
sudo reboot
```Hopefully, you'll now be rebooting into a GUI using the VESA driver. The resolution may not be optimal, but at least you'll have a GUI to work in. Now go to System -> Adminstration -> Hardware Drivers and see what that says about proprietary drivers. I don't use ATI cards so I don't know about the catalyst driver, but the inbuilt proprietary driver installer is the thing to try first.

**Edit:** I saw your comment about not being able to login in failsafe mode, which surprised me. Failsafe mode doesn't invoke the xserver (the basis of the GUI) so a driver problem in the xserver shouldn't affect failsafe mode. Anyway, the above trick with Ctrl-Alt-F1 should get you to a console login.

---

### Post by Baen on 2009-04-01
Thanks for the advice. If I wasn't so damn impatient it'd probably have worked like a charm, but sadly I ended up just reinstalling since it only takes about 30 mins. Of course this gave me a whole host of new problems. For instance, I only installed ubuntu in the old / partition thinking it should recognise the old /home so I didn't have to move my old files over again, but for some reason it didn't and created a whole new /home. I'm not sure what to do about this. I guess this'll teach me to play with linux while hung over. :(

---

### Post by coffeecat on 2009-04-01
There is a way of sorting this out, but it might be easier just to reinstall yet again! It'll certainly be quicker.

This time, select 'Manual' at the partitioning stage and be sure to tell the installer to use the old /home partition as /home, and the old root partition as root (/). Oh, and make sure you **don't** designate the /home partition for reformatting, and you **do** designate the / partition for reformatting. :|

And have a cup of strong coffee first. :p

---

### Post by Baen on 2009-04-01
Funny, my head hurts like hell and I've spent the entire day on this getting seemingly nowhere, but it's still great fun. As opposed to spending the entire day getting nowhere with Vista and having a shitty time. :P

I decided to give the process described here [http://ubuntuforums.org/showthread.php?t=363560&highlight=repartitioning](http://ubuntuforums.org/showthread.php?t=363560&highlight=repartitioning) a try first, fingers crossed. After that comes the hell that is ATI drivers. 

If nothing else, this is a great learning experience. :D

---

### Post by Baen on 2009-04-01
Edit: This either fixed itself or I managed to ignore something obvious earlier. It seems I'm taking up a lot of space with useless questions today. O.o I tried deleting my post but I couldn't figure out how, so if any moderator feel this belongs in the trash, knock yourselves out. ;)


Well, that didn't go exactly as it should...

I followed the guide I linked in by last post and double checked that it actually used the new /home partition sda6 I added in the fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=392ffccf-9b15-4d31-ae3c-995358096456 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=1477ccf2-444f-1a9e-7b72-6cdc399dfb36 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/sda6
UUID=e168dff9-a708-4fa8-b2f9-500d3ff9dfed /home ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2

``` 

It worked just fine so I changed it back, deleted the old home, managed to copy the fstab above with the new /home into /etc and rebooted. And of course now apparently I have no /home at all. I've double checked that the UUID is correct, the fstab is as it should be, etc.
Does anyone have any idea what went wrong? And possibly how to fix it? ;)

---

### Post by Baen on 2009-04-02
I'm pretty much back to my first post here, and I can't see this one solving itself. :(  I'd do a re-install if I figured it'd help but I'd still need to get the 9.3 driver to work so no point.

So, I did what coffeecat suggested to remove the driver.
I've still got 8.04 on a different partition, so I went there and opened the xorg.conf from 8.10 to change the driver back to "vesa", hoping that would fix the scrambled graphics and let me log in. Only the driver was already set to "vesa". (And yes, I'm sure this was the right xorg.conf, the one belonging to 8.04 already has the 9.3 driver working perfectly).
So, I went to /usr/src/modules and deleted the fglrx folder, restarted the comp and voila.... nothing changed.

This leaves me a bit puzzled as I figured what I just did should have removed the driver. And the only time I ever got those scrambled graphics was after the two times I tried installing the ATI 9.3 drivers and restarted. So if it's not the driver, what is it? Or if it is the driver, what more can I do to get rid of it? I don't see how the driver could be messing up my graphics if it's not actually in use as the xorg.conf suggests, but what else could it be?

---

### Post by the_ice.e on 2009-04-02
> **coffeecat said:**
> Try booting up normally, and if you are dumped into a command console with a login prompt, fine. If not, press Ctrl-Alt-F1 and you'll get to the console login. Login and type:

```
sudo nano -w /etc/X11/xorg.conf
```Type in your password when prompted. In the simple text editor that opens, scroll down to the line that says 'Section "Device" ' and a couple of lines under that change the line that says:

```
     Driver     "something_or_other"
```to

```
     Driver     "vesa"
```Now save the modified file with Ctrl-O and exit with Ctrl-X and type

```
sudo reboot
```Hopefully, you'll now be rebooting into a GUI using the VESA driver. The resolution may not be optimal, but at least you'll have a GUI to work in. Now go to System -> Adminstration -> Hardware Drivers and see what that says about proprietary drivers. I don't use ATI cards so I don't know about the catalyst driver, but the inbuilt proprietary driver installer is the thing to try first.

**Edit:** I saw your comment about not being able to login in failsafe mode, which surprised me. Failsafe mode doesn't invoke the xserver (the basis of the GUI) so a driver problem in the xserver shouldn't affect failsafe mode. Anyway, the above trick with Ctrl-Alt-F1 should get you to a console login.

Could this work for this post?
[http://ubuntuforums.org/showthread.php?p=6945258#post6945258](http://ubuntuforums.org/showthread.php?p=6945258#post6945258)



Ou yea.. how to start in safe mode?:oops:

---

### Post by coffeecat on 2009-04-02
> **the_ice.e said:**
> Could this work for this post?
[http://ubuntuforums.org/showthread.php?p=6945258#post6945258](http://ubuntuforums.org/showthread.php?p=6945258#post6945258)

Maybe, but first you really need to find out what happened when the xserver failed. This may be nothing to do with the problem on this thread. You should bump your own thread (post again). Your post has gone unanswered for a week - it will have been lost in the 10th or greater page for that forum and no one is seeing it now - so it's fine to bump it. When you bump, add some more information, such as details of your hardware, what you were installing with adept when it asked you to shut down the xserver and anything else that might be relevant. Then, hopefully, you will get help relevant to your particular problem.

---

### Post by coffeecat on 2009-04-02
> **Baen said:**
> I'm pretty much back to my first post here, and I can't see this one solving itself. :(  I'd do a re-install if I figured it'd help but I'd still need to get the 9.3 driver to work so no point.

So, I did what coffeecat suggested to remove the driver.
I've still got 8.04 on a different partition, so I went there and opened the xorg.conf from 8.10 to change the driver back to "vesa", hoping that would fix the scrambled graphics and let me log in. Only the driver was already set to "vesa". (And yes, I'm sure this was the right xorg.conf, the one belonging to 8.04 already has the 9.3 driver working perfectly).
So, I went to /usr/src/modules and deleted the fglrx folder, restarted the comp and voila.... nothing changed.

This leaves me a bit puzzled as I figured what I just did should have removed the driver. And the only time I ever got those scrambled graphics was after the two times I tried installing the ATI 9.3 drivers and restarted. So if it's not the driver, what is it? Or if it is the driver, what more can I do to get rid of it? I don't see how the driver could be messing up my graphics if it's not actually in use as the xorg.conf suggests, but what else could it be?

Hmm, I'm stumped. If you're really 200% sure that xorg.conf on the correct partition is invoking the vesa driver, then your graphics should just work. It shouldn't matter if there's a borked ati driver somewhere in the filesystem - only the vesa driver should be being used.

Which makes me wonder if this might be a hardware rather than a software problem, and which coincidentally appeared when you installed the ATI drivers. First, can you describe exactly what you mean by 'scrambled graphics' and 'graphics messed up? Second, I was assuming you were using the live CD to do the several reinstalls you've ended up doing. Am I right? What I am getting at is, if you were using the live CD, what were the graphics like? If you were using the alternate CD, try booting up with the live CD, and see whether you can get an unscrambled GUI. And if you can get a GUI with the live CD, have a look inside the live session's /etc/X11/xorg.conf and see what driver that is using. If that's not vesa, and all else fails, try substituting that driver in your HD xorg.conf(s).

**Edit:** in case you haven't come across this community documentation page:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

There are some useful links at the bottom.

---

