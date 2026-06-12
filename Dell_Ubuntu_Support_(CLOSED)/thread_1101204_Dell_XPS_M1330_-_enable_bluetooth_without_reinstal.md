---
title: "Dell XPS M1330 - enable bluetooth without reinstalling windows?"
date: 2009-03-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mike.freislich on 2009-03-20
Hi,

I have a Dell M1330. It came pre-installed with Windows Vista Ultimate, and I decided to move to Ubuntu 8.10 Intrepid. All hardware working great except Bluetooth. In reading various posts, it seems that if bluetooth was disabled in Vista before installing Ubuntu, it needs to be reenabled using Vista.

Please tell me this is not the only way. I've spent some long hours customising my Ubuntu install. I truly don't want to have to *blat* it and install Vista again to get my bluetooth working. Is there another way? Even if there's some way to boot vista off a USB drive and reenable it. Is there any plan to make it possible to enable the bluetooth from Ubuntu?

Thanks in advance,
Mike

---

### Post by paddy1978 on 2009-03-20
(Not with my m1330, so can't give detailed instructions...) It might be worth checking in the BIOS. You press Delete or F2 I think on boot to get into that.

The BIOS has options to turn bluetooth/wi-fi on or off - and, I think, control the switch on the right-side of the laptop (i.e. whether this turns off bluetooth or not).

I guess it could be disabled in some otherway - but I'd give this a try!

---

### Post by mike.freislich on 2009-03-24
Thanks for the response. No, unfortunately not that simple. I've tried everything from disabling, enabling in the BIOS, using the switch to turn it on and off. I've read in posts that:
1) Dell's windows vista driver upgrades the firmware of the bluetooth module making it unusable in linux... so there is a dell patch to downgrade the firmware.
2) If the bluetooth module was disabled in windows vista (by using the driver software) before installing ubuntu (linux), then it is not possible to enable it again using the ubuntu driver. This is because the code to do it is obfuscated in the proprietry windows driver.

So... I decided to take the plunge and shrink my ubuntu volume and install windows vista with dual boot. I then downgraded the bluetooth driver, and enabled the bluetooth module... Now when I boot up off the ubuntu live-cd (usb) I can see and use the bluetooth module. Progress! 

However, when I boot into my ubuntu installation on my harddrive, the OS doesn't pick up the bluetooth module. 
* Running lsusb it shows the line "Bus 002 Device 003: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth". This wasn't showing before... good.
* running dellWirelessCtl -i shows the following:
Radio Status for Bluetooth:
	Bluetooth supported
	Bluetooth installed
	Bluetooth enabled
	Status Code: 0

This was showing as "Bluetooth disabled" before... Good!

Why does the Gnome bluetooth software not see the device? If I set the bluetooth preferences in "system->preferences->bluetooth" to only show the icon when a device is present, the icon never shows up. I think I may need to uninstall all traces of bluetooth drivers etc from my ubuntu, and then reinstall them, but I'm not sure how to do this.

Any ideas? (ubuntu 8.10 intrepid)

](*,)

---

### Post by mike.freislich on 2009-03-24
Frikken yes! :D

I just did:

sudo apt-get remove bluez
sudo apt-get install bluez

Bluetooth working! (obviously this was after the vista install etc. as detailed above)

perhaps this will help someone else. 

l8tr

---

### Post by gavinhughes86 on 2009-09-12
Glad your sorted I had the same issue although i am dual booting and was able to use the dell software to turn on the bluetooth module, took me a while to resolve this on google,

---

### Post by gansvv on 2009-10-06
Interesting. I had the same problem after removing Windows XP without enabling my Bluetooth adapter. I was unable to activate the Bluetooth device after installing Ubuntu. But the BIOS tweak worked for me! :)

My machine is a Dell Inspiron 630m (same as Dell M140) that previously ran WinXP. With Ubuntu, after a restart, I opened BIOS setup and in "Wireless Devices", made the device to be activated "by Application", instead of using "fn keys". This was the last category in my BIOS settings. Then, booting into Ubuntu, I was able to detect my cell phone by simply using the BlueZ interface.

Still the blue light on the adapter doesn't turn ON. And, the wireless is also controlled by the app now. But, these are fine since I did not have to install Windows again to turn on the Bluetooth. Perhaps I could turn the fn keys control back on now.

---

### Post by JabberWalkie on 2010-04-27
Well, I have been thinking about this, as I am stuck in the same situation. I would prefer not to install windows on my computer, so I think I have come up with a solution. Going to try this soon, but until then here is my idea: 

Apparently there are several programs that can create a LiveCD/USB from an existing windows partition [http://en.wikipedia.org/wiki/List_of_live_CDs#Microsoft_Windows-based](http://en.wikipedia.org/wiki/List_of_live_CDs#Microsoft_Windows-based)

So, I would think that making a LiveCD/USB from a computer with windowsXP installed, booting up the laptop in question, then flashing the firmware should work. This all of course depends on if the the LiveCD's are able to make a decent windows environment. I'll test this out when I am able, if anyone has the chance, please post your success/failure here :).

Cheers,

-Jab

---

### Post by rykel on 2010-08-19
I also had this problem... without Windows, I cannot turn on my disabled Bluetooth.

This should NOT be the case, as Ubuntu should be able to exist WITHOUT Windows!

Indeed, another unrelated problem that Ubuntu should be able to solve without resorting to Windows is that of an improperly unplugged NTFS hard drive.

---

### Post by heldmar on 2010-08-19
Well, in case anyone is still interested in this post, I have found that Ubuntu 10.04 (Lucid Lynx) works perfectly with my headset (AmbiCom).

I didn't have to install anything, it just worked out of the box.

I'm using of course a Dell XPS M1330 (if not, I won't be posting on this one).

Regards,

Helder

---

### Post by mateomiguel on 2010-09-04
I think I have this problem too.  I'm running a Dell XPS M1330 and don't seem to have Bluetooth working. I just bought a new android phone so this has become an issue.  Here's the output of my command to see what's going on:

```
sudo dellWirelessCtl --i
Libsmbios version : 2.2.13
smbios-wireless-ctl version : 2.2.13
Wireless Info:
	Hardware switch supported
	Hardware switch is Off
	WiFi Locator supported
	Wireless Keyboard not supported
	NVRAM Size: 256 bytes
	NVRAM format version: 1

Radio Status for WLAN:
	WLAN enabled at boot
	WLAN supported
	WLAN disabled
	WLAN installed
	WLAN controlled by wireless switch at boot
	WLAN runtime switch control currently enabled
	Status Code: 1

Radio Status for Bluetooth:
	Bluetooth enabled at boot
	Bluetooth supported
	**Bluetooth disabled**
	Bluetooth installed
	Bluetooth controlled by wireless switch at boot
	Bluetooth runtime switch control currently enabled
	Status Code: 1

Radio Status for WWAN:
	WWAN enabled at boot
	WWAN supported
	WWAN disabled
	WWAN not installed
	WWAN controlled by wireless switch at boot
	WWAN runtime switch control currently enabled
	Status Code: 2

Wireless Switch Configuration
	WLAN switch control: on
	Bluetooth switch control: on
	WWAN switch control: on
	switch config: not locked
	WiFi locator: enabled
	WiFi Locator config: not locked

```

Does that mean I have to load up a Windows environment and apply a patch?  I tried using a virtual machine but there were "no compatible devices found".  I've been using this system for most of a year I can't just reformat back to windows and do this.

---

### Post by rykel on 2010-09-05
Hi, since Ubuntu CANNOT turn on a Bluetooth device if it was initially turned off in Windows, has anybody tried turning it on in Windows under VMWare or Virtualbox?

---

### Post by mateomiguel on 2010-09-06
I just tried it now, and i can't even get the virtual machine to even acknowledge that the Bluetooth exists.

---

### Post by rykel on 2010-09-06
> **mateomiguel said:**
> I just tried it now, and i can't even get the virtual machine to even acknowledge that the Bluetooth exists.

This is indeed sad... what is the use of having a virtual machine then... it seems like we still NEED Windows after all!

I will try it again too myself when time permits.

---

### Post by mateomiguel on 2010-09-08
this is quite frustrating.  I don't have the time to try to install windows on my machine, since it usually takes several hours.  Also, is it even possible to install windows after installing linux?

---

### Post by heldmar on 2010-09-08
> **mateomiguel said:**
> I think I have this problem too.  I'm running a Dell XPS M1330 and don't seem to have Bluetooth working. I just bought a new android phone so this has become an issue.  Here's the output of my command to see what's going on:

```
sudo dellWirelessCtl --i
Libsmbios version : 2.2.13
smbios-wireless-ctl version : 2.2.13
Wireless Info:
	Hardware switch supported
	Hardware switch is Off
	WiFi Locator supported
	Wireless Keyboard not supported
	NVRAM Size: 256 bytes
	NVRAM format version: 1

Radio Status for WLAN:
	WLAN enabled at boot
	WLAN supported
	WLAN disabled
	WLAN installed
	WLAN controlled by wireless switch at boot
	WLAN runtime switch control currently enabled
	Status Code: 1

Radio Status for Bluetooth:
	Bluetooth enabled at boot
	Bluetooth supported
	**Bluetooth disabled**
	Bluetooth installed
	Bluetooth controlled by wireless switch at boot
	Bluetooth runtime switch control currently enabled
	Status Code: 1

Radio Status for WWAN:
	WWAN enabled at boot
	WWAN supported
	WWAN disabled
	WWAN not installed
	WWAN controlled by wireless switch at boot
	WWAN runtime switch control currently enabled
	Status Code: 2

Wireless Switch Configuration
	WLAN switch control: on
	Bluetooth switch control: on
	WWAN switch control: on
	switch config: not locked
	WiFi locator: enabled
	WiFi Locator config: not locked

```

Does that mean I have to load up a Windows environment and apply a patch?  I tried using a virtual machine but there were "no compatible devices found".  I've been using this system for most of a year I can't just reformat back to windows and do this.

I would strongly suggest to use Lucid Lynx and it works perfectly for me. I am even able to use a Bluetooth Headset without any problems and it detects it out of the box, I had to do nothing in order for my machine to see it.

Also, it (Lucid Lynx) has support until 2013, which means it's a long term solution.

---

### Post by mateomiguel on 2010-09-09
I'm using Lucid Lynx now, and have been since it came out.  But I don't got any Bluetooth.

---

### Post by heldmar on 2010-09-10
> **mateomiguel said:**
> I'm using Lucid Lynx now, and have been since it came out.  But I don't got any Bluetooth.

That's weird, have you been updating your software constantly? As I said before, when I installed this distro in my laptop 2 months ago, it instantly recognized bluetooth without any issues.

---

### Post by mateomiguel on 2010-09-12
Yes, I update once a week like clockwork.

According to the OP, the issue is that if you had Bluetooth turned off when you had Windows Vista running, you couldn't turn it back on under Linux.  I assume that's my issue.

---

### Post by dhinuksha on 2010-10-23
even im stuck with the same issue? Mine is Inspiron 1464 with Dell wireless 365 Module. atleast Broadcom could've issue a patch or sumthing. hate installing windows again. and move backups here and there.. :(

---

### Post by chunky bacon! on 2011-01-31
Just out of pure desperation, did you ever get this working?

10.04 on Vostro V130.  No Windows install to fall back on....

---

### Post by heldmar on 2011-01-31
Mine is working like a charm!

In fact, I'm waiting to see if it's going to work in few weeks when new Ubuntu comes out.

---

### Post by chunky bacon! on 2011-01-31
Thanks heldmar, but yours apparently worked out of the box.  Was wondering how it was going for us majority who have had it not work.

I've spent nearly 2 days on this, and I'm about to just give up.

My biggest beef isn't with Ubuntu, I don't think.  It is with Dell only releasing their drivers as windows executables.

---

### Post by rykel on 2011-02-02
Has anyone filed a Launchpad bug report to inform the Ubuntu devs that the Dell XPS 1330 bluetooth will not turn on if it was initially turned off under Windows?

They might be able to advise us.

---

### Post by woop on 2011-02-22
ugh this is just depressing. I dont think it will ever be solved tbh. My camera works under 10.10. albeit looking like its through frosted glass sadly. Worked perfectly in all previous versions of ubuntu

---

### Post by schmandr on 2011-06-17
Hi folks!

For your reference, this is how it worked on my Dell XPS M1330:
I have recently completely reinstalled windows 7 and kubuntu 11.04 dual booting on my XPS M1330. At first bluetooth wasn't available under both OSes (so Windows 7 didn't recognize automatically the bluetooth module neither). So I downloaded a Windows 7 driver from the dell support page. Because for XPS M1330 there's only a Windows Vista driver available, I specified the Alienware M15x Laptop as my computer model and Windows 7 x64 as my operating system (this was recommended in several forum posts). After installation the bluetooth device is now listed as Dell Truemobile 355 Bluetooth + EDR in the so called Device Manager.
After a reboot into Kubuntu, bluetooth is now available and working as well. No more action was needed here.

I was lucky enough I had installed Windows previously anyway. But I do hope there is a linux only solution for those of you without Windows.

---

### Post by mattruffoni on 2011-06-25
I'ven't a dell xps but on my dell vostro 3350 i've solved this problem with this guide [http://www.edwardcrosby.com/2011/06/17/bluetooth-fix-in-linux-mint-11ubuntu-11-04/](http://www.edwardcrosby.com/2011/06/17/bluetooth-fix-in-linux-mint-11ubuntu-11-04/)
:p

---

### Post by mouhammad88 on 2011-10-09
After a long wasting time in complicated tuto and tips , i found an easy magic solution :D look at this : [http://www.edwardcrosby.com/2011/06/17/bluetooth-fix-in-linux-mint-11ubuntu-11-04/](http://www.edwardcrosby.com/2011/06/17/bluetooth-fix-in-linux-mint-11ubuntu-11-04/)

---

