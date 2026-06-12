---
title: "ARGH- This makes no sense!!!"
date: 2006-08-06
forum: Desktop Environments
---

### Post by CBTF on 2006-08-06
I'm a new ubuntu user, and this is driving me crazy. Fortunately im confident someone here will know a solution to this.

My install and setup of the OS went well.

After configuring ubuntu, I decided I would update (the alert came up telling me software updates were available.)

I updated, and when it was complete it instructed me to reboot- but when I did, it got hung up on a black screen for 10 mins until i killed the power.

Upon turning my computer back on, I saw something in the OS selection window that confused me (I run xp and ubuntu.)

Instead of listing ubuntu like usual, it showed two different versions. The OS selection looked like this:

Ubuntu, linux Kernel 2.6.15-26-388
Ubuntu, linux Kernel 2.6.15-26-388 (Recovery Mode)
Ubuntu, linux Kernel 2.6.15-23-388
Ubuntu, linux Kernel 2.6.15-23-388 (Recovery Mode)

Both work, but i still cannot reboot.

PLEASE HELP 

:(

---

### Post by dennisharrison on 2006-08-06
can't reboot as in the os will not load again? or when you reboot it hangs the system and you have to hit the reset button?

---

### Post by vijirajan on 2006-08-06
The OS listing in the GRUB menu looks normal. When you installed Ubuntu Dapper from the Live CD it installed kernel version 2.6.15-23-386 and the software update installed the most recent kernel. Thats why you see two kernels being displayed in the boot menu. As for as the extra item under each kernel (i.e the one that ends with Recovery mode) is used to solve problems with your system in single user mode (sort of like Safe Mode in Windows).

As for as your problem is concerned, can you explain it in detail?

---

### Post by CBTF on 2006-08-06
It hangs on the black screen until i hit the shutoff button on the case.

edit: as per the reply above, is there a method for stopping old kernals from being displayed? after a few updates that could be annoying :???:

---

### Post by vijirajan on 2006-08-06
> **CBTF said:**
> It hangs on the black screen until i hit the shutoff button on the case.

edit: as per the reply above, is there a method for stopping old kernals from being displayed? after a few updates that could be annoying :???:

Its easy to remove old kernels that you don't use. Open the System->Administration->Synaptic Package Manager. Search for "linux-image-2.6.15-23-386". In the result select linux-image-2.6.15-23-386 and right click. Select "Mark for Removal" and click "Apply" in the toolbar.

This would remove the kernel. MAKE SURE YOU DON'T REMOVE THE KERNEL YOU HAVE CURRENTLY LOGGED IN WITH. To check the current kernel being used, Open the Terminal Application (Applications->Accessories->Terminal) and type ```
uname -r
```. This will list the currently used kernel.


Your blank screen on reboot could be related power management support in BIOS. Can you tell me your system spec? Also, does Windows reboot fine on your machine?

---

### Post by CBTF on 2006-08-06
Thank you for the instructions on kernal removal.

As far as the blank screen on reboot that hangs, could it be related to fglrx?

My system specs:

Ubuntu Dapper Drake 32 bit (dont want to use 64bit)
AMD athlon 64
ATI radeon xpress 200
200 gb HD
1 gb RAM

Windows reboots fine. Something went wrong in ubuntu during the session i updated/fixed my graphics card settings (changed the "ati" setting to fglrx). It must hav been one of the two connected to this. Ubuntu restarted fine beforehand.

---

### Post by dennisharrison on 2006-08-06
what happens when you hit alt F1 and login?
or does it lock up totally?

if you can log in do a
dpkg-reconfigure xserver-xorg
select vesa and see if that gets you back in.  You could be in ati hell.  I am currently there ;p  Managed to get my mesa drivers working again even though I should be using fglrx drivers and I specified that in my config file.

---

### Post by CBTF on 2006-08-06
The hang up isnt a login issue- it happens during the shut down half of the restart. It goes from my ubuntu desktop to the black screen. (where it would usually list the things being unloaded.)

It is at this point i must manually reboot using the button on my tower.

---

### Post by vijirajan on 2006-08-06
Can you check your system logs and find out if it shows any errors during reboot? 

Reboot the system once it hangs switch off using the power off button. Switch  the system back on and login to Ubuntu. Then goto /var/log directory and look for errors in the following files:

```

messages.0
kern.log.0
Xorg.0.log.old

```

Let me know if you find any errors in there. Also, when the system hangs trying switching to different consoles and see if the reboot process is waiting for some process to end. You can switch to different consoles using 
```

Ctrl+Alt+[F1-F9]

Usually GNOME uses Ctrl+Alt+F7 (i.e console 7) and the reboot process uses Ctrl+Al+F8 (console 8)

```

---

### Post by CBTF on 2006-08-06
Pressing the keys to change consoles did nothing. The screen stays black. 

All 3 logs you mentioned have errors (im assuming, all i know is they have text within.. :-( )- what now?

If i am to post them, do they contain personal data?

---

### Post by dennisharrison on 2006-08-06
no they don't contain personal data...

you should just post the last few errors.  Arent they time stamped also?

---

### Post by peabody on 2006-08-06
> **vijirajan said:**
> 
...
```

messages.0
kern.log.0
Xorg.0.log.old

```
...


I recommend looking at dmesg as well.  If you do use the proprietary fglrx drivers from ATI, which version do you use?  When the kernel upgraded did you recompile the kernel modules?  Older versions of the ati driver have a tendency to lock up when switching video modes away from X (terminal switching via Ctrl+Alt+[f1-f6]).  To my understanding the latest versions fix this problem.

---

### Post by CBTF on 2006-08-06
The logs are too long to post.. and a .txt of them is too long as well, as it is 50 kb over the allowed limit.

what should i look for in these logs?

> I recommend looking at dmesg as well. If you do use the proprietary fglrx drivers from ATI, which version do you use? When the kernel upgraded did you recompile the kernel modules? Older versions of the ati driver have a tendency to lock up when switching video modes away from X (terminal switching via Ctrl+Alt+[f1-f6]). To my understanding the latest versions fix this problem.

I dont know which ver. I use- easyubuntu did it today. I dont know how to recompile either.. so no =(


/huge n00b

---

### Post by yatt on 2006-08-07
> **CBTF said:**
> The logs are too long to post.. and a .txt of them is too long as well, as it is 50 kb over the allowed limit.

what should i look for in these logs?



I dont know which ver. I use- easyubuntu did it today. I dont know how to recompile either.. so no =(


/huge n00b

Ugh, I hate easyubuntu. A couple thing you could try.
Open Synaptic. Search for fglrx. Completely remove xorg-driver-fglrx, fglrx-control, and fglrx-kernel-source (if you do not have all of those do not worry, I just cannot remember which ones easyubuntu installs. Then, install those 3 packages.

Then in a terminal:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo gedit /etc/X11/xorg.conf
```

Look for Section "Device"

Make sure the driver is fglrx, and add this line (anywhere between Section "Device" and EndSection):
```
     Option     "KernelModulePram"    "agplock=0"
```

You should have something like this in the end:
```
Section "Device"
	Identifier	"ATI Technologies, Inc. ATI Default Card"
	Driver		"fglrx"
	Option		"KernelModulePram"	"agplock=0"
	BusID		"PCI:1:0:0"
EndSection
```

Its not a good idea to mess with the other stuff.

Restart. If you are told that the x server cannot load, login and type
```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

---

### Post by TobbeR on 2006-08-07
Hi

I posted this a few days ago:

(snip
I found a solution somewhere for the shut down crash, the session manager KDM/GDM is not properly configured.

For KDM put "TerminateServer=true" in your kdmrc under the [X-:*-Core]: section.

For GDM put "AlwaysRestartServer=true" in the gdm.conf.

I have tested the KDM solution and it worked for me.
(end)
Regards
TobbeR

---

