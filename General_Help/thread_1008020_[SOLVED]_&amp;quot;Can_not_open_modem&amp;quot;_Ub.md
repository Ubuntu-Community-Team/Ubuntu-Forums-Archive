---
title: "[SOLVED] &amp;quot;Can not open modem&amp;quot; Ubuntu avoids internet like the plague. D:"
date: 2008-12-11
forum: General Help
---

### Post by TheBlueBeastie on 2008-12-11
I hate to be asking so many questions here, but I'll start contributing as soon as I get my Ubuntu connected.
Honest! D:

(I'm on Ubuntu 8.10 "Intrepid Ibex")
Anyway, I'm using a Huawei EC228 aircard, 3G, EVDO, modem...
It's called of lot of things...

Anyway, I couldn't use it to get connected when I first installed, because my service provider, Alltel, wasn't listed.
Only had At&t and T-Mobile. (I did still try though.)

After that, I tried to install the drivers with the Windows Wireless Driver thing, still no good. (Might have something to do with the fact that out of all the drivers I installed from the disc, only one ever says that hardware is present.)

Then, I tried using Gnome PPP to connect.  But, it couldn't open the modem, so it says.

Also, when I open that god-forsaken terminal and type lsusb, it tells me I have a Huawei E620, not a Huawei EC228.  Sometimes when I log into Ubuntu, it'll ask me if I want to configure this imaginary E620.

I really, really do want to get my Ubuntu connected.
I even tried installing VirtualBox, but I remembered my Windows XP disc got destroyed, so I can't install the QuickLink Mobile software that came with the card on it and attempt to connect like that...

I've heard of people successfully connecting with a Huawei EC228, so surely someone here must have an answer. D:
I've already followed some Google results, but all of them involve commands, all of which fail because a directory doesn't exist, or some other thing along those lines.

I would be so grateful if someone could help, even if it just gets me closer. <3

NOTE: I have no internetz on Ubuntu.  When I install something, I have to do it "manually" by finding everything it needs and installing it that way.

---

### Post by TheBlueBeastie on 2008-12-11
Aww, I'm *desperate*. T.T

By the way, I also tried to install Wammu.
It's weird that I got to a point where dependency A said that it needed dependency B, which says it needs dependency A. xD  @.@

---

### Post by LowSky on 2008-12-11
Alltel uses the same technolgy as Verizon (infact Verizon jut purchase Alltel) so try their driver

otherwise its usb based correct? With modem plugged in, open a terminal window and type

```
lsusb
```

It may show the modem as something else so please post the data you get here..

thanks

---

### Post by TheBlueBeastie on 2008-12-11
Sorry for taking so long...

Here's what I got after typing lsusb in the terminal:

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:5112 Dell Computer Corp. Photo AIO Printer 924
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 006: ID 093a:2468 Pixart Imaging, Inc. Cammaestro 2.5DU/X-EYE/Orite SC-120/ICGear TravelCam/Easy Snap Snake Eye WebCam
Bus 002 Device 005: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 002 Device 004: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 002 Device 003: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Bus 002 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0781:5406 SanDisk Corp. Cruzer Micro 1/4GB Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Did I do it right? xD
I hope that's what you were looking for.

---

### Post by TheBlueBeastie on 2008-12-12
I have a new development!

I learned that Gnome PPP has a "Setup" button, that lets me tell it what kind of modem it is and stuff.

Everything was way off... So, I set the settings right.

However, it seems the default place to find the modem was at /dev/modem .  Looking at the log when it tried to connect, it said the directory didn't exist.
There are other places from the drop-down list that tells it where to find the modem.  However, all them say there was input/output error. These places are /dev/ttyS0 through 3.

Maybe that clears something up... or something? :p

---

### Post by JC Cheloven on 2008-12-15
Hi BlueBeastie, your modem should normally be at /dev/ttyUSB0. 

The program gnome-ppp is mainly a frontend, I think that it will be able to do very little for you if things doesn't work properly on the backgroung.

I'd say that the info [in this post]("http://ubuntuforums.org/showthread.php?p=6374775#post6374775")  will be of help for you.

---

### Post by TheBlueBeastie on 2008-12-16
Thanks JC!  Gnome PPP actually recognized the modem! xD

Alas, now I'm faced with new problems.

When I go to the settings, and set the location to /dev/ttyUSB0, it actually does sense the modem.  Strangely, it takes my settings. (USB Modem, 460800) and sets them to Analog Modem, 9600...

Anyway, when I hit "Connect" it says it's connecting, then dialing #777, then it's waiting for a prompt, then it's dialing #777 for a few more minutes, then it's back to the Connect window.

When I hit "Connect" it again, it says it's connecting for a minute, then it says the modem didn't respond.

first i wuz lyk :3  den i wuz lyk :D  den i wuz lyk ):  but den i wuz lyk D:<

If I restart the computer and enter all the commands again, it goes back to dialing.  But then it goes back to saying the modem isn't responding, like stated above.

---

### Post by TheBlueBeastie on 2008-12-16
I decided to take one last, final effort. D:

> It'll show up as /dev/ttyUSB0 or somesuch. Just configure your PPP daemon to open that device with 8/N/1 at 460800. The usbserial driver will automatically load the high-speed driver it needs.

That quote came from another forum where someone asked a question about using Ubuntu with my card.

One user commented that answers like that are the exact reason people get s***brain confused over Linux.

Me? Working with Ubuntu, I know now that /dev/ttyUSB0 refers to a file in that directory, I know what the 460800 is, what the usbserial driver is.  It's been a real learning experience. xD

But, what is 8/N/1? Wikipedia says it's some kind of common configuration thingy.
Will it help to do as she says and open the device with it by configuring the PPP daemon, and if so, how is that done? x3

---

### Post by TheBlueBeastie on 2008-12-18
Okay guys, one last development. Honest!
I'll stop bugging you guys after this one.

I guess I'm just too persistent, but I checked the log after it tried dialing again.  I think I should note, I had it in stupid mode. >>

--> Ignoring malformed input line: ";Do NOT edit this file by hand!"
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATX3
ATX3
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM0L0DT#777
--> Waiting for carrier.
ATM0L0DT#777
CONNECT 3100000
--> Carrier detected.  Starting PPP immediately.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Timed out while dialing.  Trying again.
--> Maximum Attempts Exceeded..Aborting!!
--> Disconnecting at Thu Dec 18 13:49:36 2008

Does this help with anything. It looks like that /usr/sbin/pppd is the cause of current woes. I must be so close. T.T

Should I try checking the permissions, or try to specify a PPPD Path option in wvdial.conf.  However you do that. <.<;
Or is this just completely hopeless? x3

---

### Post by jskiddy19 on 2008-12-19
Did you ever figure this out?  I am having almost the exact same problems.

---

### Post by TheBlueBeastie on 2008-12-21
Actually, I did!  Just now! :D
When my sister's laptop when on the fritz, I tried using ubuntu on it, but got all the same problems. "Check permissions..."
Then it clicked in mah head. PERMISSIONS! O:

I then erased the Ext3 partition and all things using it (like the swap and the extension) and reinstalled Ubuntu.  Then I installed Gnome-PPP.
Then, I did this:

sudo gnome-ppp

Then I typed in my information, hit "Connect" and then I was on the internetz! O:

Quite frankly, I feel a little stupid, it should've one of the first things to try... But whatever. xD

(Now, to state my situation is solved, and send thanks to those that had helped me realize what to do. However that's done. >.> xD )

---

