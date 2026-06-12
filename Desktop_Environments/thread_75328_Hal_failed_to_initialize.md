---
title: "Hal failed to initialize"
date: 2005-10-13
forum: Desktop Environments
---

### Post by Jerrac on 2005-10-13
Well, I am completely up to date with breezy. But everytime I start my computer up, it gives me this message:> Internal error

failed to initialize HAL!


What is HAL, and what can I do to fix it?

---

### Post by KingBahamut on 2005-10-13
Thats the USB Hotplug thingy. 

What usb Devices do you have connected? What is your hardware setup?

---

### Post by Jerrac on 2005-10-13
I have a pda dock connected now, but it was doing that when nothing was connected.. So...

My motherboard is a MSI K8Neo 4-F Or something like that.. can't remember exactly.

Here is my lspci:
> firstuser@jerrac:~$ sudo lspci
Password:
0000:00:00.0 Memory controller: nVidia Corporation: Unknown device 005e (rev a3)0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 0050 (rev a3)
0000:00:01.1 SMBus: nVidia Corporation: Unknown device 0052 (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 005a (rev a2)
0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 005b (rev a3)
0000:00:04.0 Multimedia audio controller: nVidia Corporation: Unknown device 0059 (rev a2)
0000:00:06.0 IDE interface: nVidia Corporation: Unknown device 0053 (rev a2)
0000:00:07.0 IDE interface: nVidia Corporation: Unknown device 0054 (rev a3)
0000:00:08.0 IDE interface: nVidia Corporation: Unknown device 0055 (rev a3)
0000:00:09.0 PCI bridge: nVidia Corporation: Unknown device 005c (rev a2)
0000:00:0a.0 Bridge: nVidia Corporation: Unknown device 0057 (rev a3)
0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
0000:00:0c.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
0000:00:0d.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
0000:00:0e.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:05:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0161 (rev a1)
firstuser@jerrac:~$


---

### Post by dbott67 on 2005-10-13
[QUOTE=Jerrac]Well, I am completely up to date with breezy. But everytime I start my computer up, it gives me this message:
What is HAL, and what can I do to fix it?[/QUOTE]

In Hoary, I had this issue happen a couple of times... I seem to recall that if you leave the CD in the CDROM dirve, you should be able to get past the message (you may want to change the boot order in your BIOS so it doesn't boot from CD for the time-being).

If this works, try searching Synaptic for "hal" and then forcing a re-install.

Again, this seemed to work for me in Hoary a number of months ago, but I don't know if it will help in Breezy (pretty sure it can't hurt, though ;) )
-Dave

---

### Post by dbott67 on 2005-10-13
Oh yeah, one more thing... do you eventually get to your desktop? or does the system just hang?

-Dave

---

### Post by Jerrac on 2005-10-14
Tried reinstalling anything dealing with HAL (hardware abstraction layer) with synaptic. Didn't work.

And no, my system does not hang. I just has that error popup all the time, really annoying. Plus I think it has something to do with my usb drive not mounting automatically...

---

### Post by Whitemage on 2005-10-14
I have the exact same problem. 
Hal fails to initialize on startup. Therefore, nothing automatically mounts.
Hal is the "Hardware Abstraction Layer", and it's supposed to do all that sort of stuff. My error began when I had Hoary and had just installed a new DVD r/w device. I just did a clean install of Breezy and got the same error. So it's not a matter of reinstalling hal, I don't think. And the cd/no cd in drive isn't the problem either; this happens every single time I start up Ubuntu. I found a possible solution from someone, but it didn't work for me (maybe I didn't do it correctly?)

"
I had this probleme cause my dvd writer was bad (ricoh). That crash hal.
I had to put "hdc=noprobe hdc=cdrom" to kernel parameter in /boot/grub.menu.lst
hdc is my writer device
May be this help you
" -kagou

So if anybody knows another possible solution or more detail on the above solution, I would appreciate too. This is really irritating for me, because I had thought the problem would go away in Breezy, and it didn't.
Oh, and as an aside, my DVD writer is not bad. I can mount it with the mounting panel applet and can run dvds or cds fine, and I dual boot W2k as a secondary, and it works/mounts great there.

---

### Post by gdcondor on 2005-10-17
i've exactly the same pb

---

### Post by eudoxos on 2005-10-21
I had this problem with hoary, which was resolved by "hdc=noprobe hdc=cdrom". This was no longer necessary for breezy, it was caused otherwise.

Regression in breezy was solved by identifying modules for badly-behaving hardware (in my case, it was ieee1394 (not present in the computer) and i2c-*). Steps to identify the modules:

1. become root
2. run /usr/sbin/hald --daemon=no --verbose=yes
3. guess where it crashes (it logs some info about processing sysfs entries). Generally though, remove modules for absent hardware. Try to strace hald to see what files it opens before crashing. Did not try backtrace coredump.
4. remove the offensive modules from kernel (lsmod, rmmod, modprobe -r)
5. Iterate 3-4 until hald does not crash.
6. Prevent hotplug from loading all offensive modules at startup. I tried /etc/hotplug/blacklist.d/*, but it did not work (my fault, I guess). So I simply renamed ieee1394.ko to ieee1394.ko~. Same for i2c-core.ko.

Hope this helps. Has anyone filed bugs against HAL/hotplug? I would consider it a critical bug.

Regards, Eudoxos

---

### Post by Jerrac on 2005-10-22
Well, I did submit a bug report. It is here: [http://bugzilla.ubuntu.com/show_bug.cgi?id=17876](http://bugzilla.ubuntu.com/show_bug.cgi?id=17876)

I tried the command you suggested and it gave me a bunch of stuff that makes no sense to me. It won't even display it all in the terminal... Heh. I have a text file of what I could copy, but it is to big to attach. *sigh* 

Would it break my system if I completely removed hal in Synaptic?

---

### Post by eudoxos on 2005-10-23
Yes, removing HAL will break gnome-volume-manager (automounting USB flashdisks) and other things. Can you attach the result of running '/usr/sbin/hald --verbose=yes --daemon=no' and 'lsmod' (as root), in addition to dmesg? You can post it to bugzilla, to your bugreport, it might be useful for devs. Regards, Eudoxos

---

### Post by Jerrac on 2005-10-26
Well, I was able to fix it thanks to Martin Pitt. Just check out the bug report I linked to earlier. :D

---

### Post by gdcondor on 2005-10-29
I was looking for a solution to this pb for a while !
Thanks guys for the support :)

---

### Post by donkle on 2005-11-05
[QUOTE=gdcondor]I was looking for a solution to this pb for a while !
Thanks guys for the support :)[/QUOTE]
Had the same problem.  It went away after I disconnected my HP scanner.  Apparently if Ubuntu doesn't recognize one piece of your hardware you will get the error message.  Does anyone have an idea how I can get HAL to regognize my scanner?  It works beautifully in XP.

---

### Post by hockeysk8 on 2007-05-04
Well, here is my situation and fix to this problem.

I have a Sony Vaio VGN-A170P laptop and its running Edgy.  Startup happens just fine, I am presented with the login screen, and following login I get the dreaded "Failed to initialize HAL" popup.  However, if after I am presented with the login screen I go away for a VERY LONG time and then come back and log in everything is fine.  Obviously something is hanging.  From reading many other discussions forums I narrowed it down to dbus.  Therefore, I put the gdm startup later than the dbus startup, at least that way I will be presented with the login only after everything has initialized.  This worked but I still had to wait a VERY LONG time before being able to log in.  Then I came across another post that mentioned that in Feisty dbus is placed early than gdm in the startup list and that seems to have solved everything.

Here is the fix:

Get rid of the old symlink for the dbus initialization script:

sudo rm /etc/rc2.d/S20dbus

Put the order of dbus before gdm (which is at #13 in the list):

cd /etc/rc2.d/
ln -s ../init.d/dbus S12dbus

done.

---

### Post by mikeize on 2007-07-08
> **hockeysk8 said:**
> Well, here is my situation and fix to this problem.


Here is the fix:

Get rid of the old symlink for the dbus initialization script:

sudo rm /etc/rc2.d/S20dbus

Put the order of dbus before gdm (which is at #13 in the list):

cd /etc/rc2.d/
ln -s ../init.d/dbus S12dbus

done.

Has this problem been totally solved?  I am running Feisty with WUBI on my Dell Inspiron 4100 Laptop, and get this problem.  It's really a chafe, and the quoted solution doesn't apply, since that file is already ordered as specified.  The other suggestions are a little over my head, so I'm hoping someone can give me a simple answer.  i.e., a downloadable patch or something like that.  Thanks!

-mike

---

### Post by eelensar on 2007-07-10
I've got the same problem as you, mikeize, but on an HP omnibook 6100. I googled the error message, and I'm looking at stuff right now, but one forum said to reinstall dbus. Right now, I'm reinstalling everything with a name starting by dbus in Synaptic. I'll post an update when i'm done.

Edit: just saw another post that said to put this in terminal: sudo dpkg-reconfigure hal. I'm doing that as well now.

Edit2: None of that worked. Still getting the error on login.

---

### Post by vanderplas on 2007-09-28
I'm using an HP omnibook too, with feisty installed.

Yesterday during a printing job, the system crashed.
After that booting resulted in a black screen.
Thru the recovery mode I could get into gnome by starting gdm manually.
Booting took some 8-10 minutes and resulted in the famous error message "Failed to initialize HAL".

Been searching for a fix and tried it all:
- reinstalling hal
- reinstalling dbus
- restarting dbus
- moving /etc/rc2.d/S21gdm to S50gdm, moving S12dbus to S20dbus, etc.
- and every other fix mentioned anywhere on any forum.

When I almost lost hope, I noticed a warning during booting : "no newline at end of /etc/fstab"
Put the newline there and problem was solved.

Nico

---

