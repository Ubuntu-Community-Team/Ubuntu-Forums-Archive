---
title: "Bluez daemon is not running, blueman-manager cannot continue."
date: 2009-05-31
forum: General Help
---

### Post by HaydenGribble on 2009-05-31
Hi, I am getting this message when trying to startup Blueman: Bluez daemon is not running, blueman-manager cannot continue.
Any ideas? I'm pretty sure that I have all the required packages installed eg. bluez-utils, blueman...
Please help me.

---

### Post by HaydenGribble on 2009-05-31
I had this program working in my last session on the computer. Now that I have restarted, it just won't work, giving me the message above.

---

### Post by HaydenGribble on 2009-05-31
Sorry to post again, but I just reinstalled blueman, bluez-utils, bluez, bluetooth, and then it decided to work fine.
Are there any ideas as to why this might be the case? Thanks for any help, it is much appreciated.

---

### Post by HaydenGribble on 2009-06-01
Please help, how can i get bluez daemon to run on startup? Please, any help is greatly appreciated.

---

### Post by HaydenGribble on 2009-06-01
I got it fixed just then. In case others need to know how to fix this problem then here is what I did:
I figured out how to start a daemon by in the terminal writing:```
sudo /etc/init.d/bluetooth start
```
and this worked. So in the 'Startup Programs' list I added the code:```
/etc/init.d/bluetooth start
```
and it now works perfectly.

---

### Post by LukonLinux on 2009-11-25
> **HaydenGribble said:**
> I got it fixed just then. In case others need to know how to fix this problem then here is what I did:
I figured out how to start a daemon by in the terminal writing:```
sudo /etc/init.d/bluetooth start
```
and this worked. So in the 'Startup Programs' list I added the code:```
/etc/init.d/bluetooth start
```
and it now works perfectly.
I tried your solution, but it did not work for me.  It still says bluez daemon not running...  I even uninstalled, everything bluetooth related and reinstalled Blueman - letting it reinstall the couple things it needed (3 total I think.)  It still doesn't work.  The command you put in terminal gives no feedback; I assumed it did something, as it reported no errors. I am running a fairly fresh install of karmic on a Toshiba laptop - any help would be appreciated...

---

### Post by Orian90 on 2009-11-30
A bump, because I have the same problem as LukonLinux. Also using a toshiba laptop (satellite A200), maybe something related to toshiba?

---

### Post by Dragonfly310 on 2009-12-06
Another bump.  this is happening to me on my Dell

---

### Post by Orian90 on 2009-12-07
Although this will probably not help you with your Dell, it might help people with a Toshiba. I found those posts with tips on how to turn bluetooth on, and it works for me :)

[http://www.itwriting.com/blog/333-fixing-bluetooth-on-a-toshiba-with-ubuntu.html](http://www.itwriting.com/blog/333-fixing-bluetooth-on-a-toshiba-with-ubuntu.html)

and 

[https://docs.google.com/Doc?id=dgd53r6d_36hqmmh4hn&hl=en](https://docs.google.com/Doc?id=dgd53r6d_36hqmmh4hn&hl=en)

Last one fixed my problem, but the first one may also work on some toshiba pc's, and is a bit easier I think ;)

---

### Post by DenysB on 2010-03-16
This happened to me after I disabled Bluetooth to save power by quitting the Bluetooth control panel. I fixed the problem by using Synaptic manager to reinstall the bluez daemon, the other methods quoted not working for me. (Asus eeePC 901 running Ubuntu 9.10).

The actual fix may have been overkill: using Synaptic I installed bluez-gnome (which uninstalls blueman) and reinstalled bluez (which includes the daemon). I then restarted the system, and installed blueman (which uninstalls bluez-gnome).  It all works again.:D

Note to self: Don't turn off bluetooth! :confused:

---

### Post by ArionKrause on 2010-05-15
This thread helped me solve a problem with Bluetooth on Ubuntu.

Thanks!

---

### Post by sushil118 on 2010-05-20
I had the same problem when I clicked "Turn Bluetooth off" from  Bluetooth applet. But after reading through this thread, I did the following:

- Right-click Default bluetooth icon and click "Bluetooth:On"
- Then turn on the bluetooth service
sudo /etc/init.d/bluetooth stop
sudo /etc/init.d/bluetooth start

After this, I was able to use blueman-manager without having to reinstall the packages.

---

### Post by marianom on 2010-07-22
> **sushil118 said:**
> I had the same problem when I clicked "Turn Bluetooth off" from  Bluetooth applet. But after reading through this thread, I did the following:

- Right-click Default bluetooth icon and click "Bluetooth:On"
- Then turn on the bluetooth service
sudo /etc/init.d/bluetooth stop
sudo /etc/init.d/bluetooth start

After this, I was able to use blueman-manager without having to reinstall the packages.

Thanks sushil118, that did the trick.

---

### Post by ben44b on 2010-07-23
Tried all these things but didn't work for me.

---

### Post by Sergius14 on 2010-10-04
Hi, I'm sorry to hijack this thread but I also having this issue and everything I did was in vane so far.

I have a USB dongle that the gnome-Bluetooth can't find it.

I don't know yet if it is the dongle incompatible or if it is an issue with the gnome-manager.

I installed (and reinstalled...) Bluez but every time I'll try to open it I get this error.

Any help to get my dongle work would be appreciate.


Regards,

---

### Post by n8han on 2010-10-29
If your computer has built-in bluetooth and a key or switch for turning it off and on, try turning it on before running blueman. Worked for me!

Nathan

---

### Post by marknigh on 2011-04-19
sudo /usr/sbin/bluetoothd start 
I was able to start the manager after this command. It still doesn't recognize my adapter but one baby step at a time.

---

### Post by loom777 on 2011-05-02
Hi,
I've been able to resolve this issue with rfkill (it should be installed by default). Your values will vary:

```

$> rfkill list
0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

$> sudo rfkill unblock 0

```

notice the "Soft blocked: yes" by my bluetooth device. Second command requires root privileges and unblocks the selected device. 
After this, my blueman icon reappeared and everything seems to be ok now! If I turn bluetooth off using blueman, same thing happens. Time for quick alias i guess..

**this works only time to time, not sure why, but you can always disable bluetooth by "sudo bluetoothd -u" and then running blueman**

---

### Post by lotharmat on 2011-05-02
My bluetooth was disabled after resuming from suspend.

Fixed it by

```
sudo service bluetooth restart
```

Worked for me

I ended up lobbing it in a script (20_restart_bluetooth)

in /etc/pm/sleep.d

YMMV

---

### Post by mrtorrent on 2011-05-31
> **marknigh said:**
> sudo /usr/sbin/bluetoothd start 
I was able to start the manager after this command. It still doesn't recognize my adapter but one baby step at a time.

This is the first thing in the thread that worked for me -- thanks a ton! Wonder why the other commands to start the service didn't work..

---

### Post by sayid on 2011-09-04
Hi HaydenGribble,

Well after a lot of problems with bluetooth in my machine I decided to install blueman. This really helps a lot, but with an update this stops working and lots of my option were greyed in the blueman-applet.

My solution:
*kill the blueman-applet and blueman-manager. *

edit the file:  /etc/bluetooth/hcid.conf
  *change pscan enable *
to 
*  pscan disable*

and finally restart the service: 
 * sudo /etc/init.d/bluetooth start*

If you have problems with the BlueZ initialization, you only need to run:
* sudo bluetoothd*


I hope this helps to you,
Regards,
          Sayid

---

