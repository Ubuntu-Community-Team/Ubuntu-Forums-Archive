---
title: "I searched the forums already, I promise...IBEX"
date: 2008-12-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by deadbeef on 2008-12-15
Dell Vostro 1500 and a fresh install of Intrepid Ibex
Broadcom Corporation BCM4311 WLAN Rev 1--confirmed
Broadcom Corporation BCM4401-BO Ethernet NIC
BOTH are disabled and I don't know why.

I have tried at least 5-6 different methods to fix this problem and believe me, I feel badly for resorting to starting a new thread.  So...I can't get the OS to work with the WLAN card, or the wired LAN connection for that matter.  "Hardware Drivers" shows "wl" as activated and currently in use.  It's a proprietary driver if that makes a difference.  I'm seriously about to break something here.  I've set the SSID and all pertinent options to where they should be.  The router is working fine.  Three hours on this single problem is absolutely killing me.  I logged on to the ubuntu irc channel and a fine gent there showed me that my repository is missing ndiswrapper.  For the love of your God,  please don't assume that I know anything about anything.  If anyone has any advice, please deliver the explanation as though you were talking to your lovely grandmother, or maybe a three year old.  Seriously.  I'm so lost that I'm about to, well you don't want to know what I'm about to do.  I have a working XP box (!!) with a working wireless connection, but the laptop needs help as soon as someone here can administer a VERY short spoonfeeding.

---

### Post by shae on 2008-12-15
My first question is what the wired or wireless connection working when you booted the live cd to install?

---

### Post by saru411 on 2008-12-15
Under System>Administration>Hardware Drivers there should be a Broadcom B43 driver to activate. Once that driver is loaded the system may have to be restarted, but Ubuntu will let you know that it needs restarting by telling you to restart(the recycling type symbol in the upper right near the date). I'm unsure of what 5 ways you tried fixing this and I also have run into previous fixes holding me back from salvation. If there is nothing worth backing up on your HD you could always get a fresh install done and then update everything, restart, then activate the graphics driver(if any but vostros tend to come with Nvidia cards so I'm gonna guess it has one), restart, then activate the wifi(and restart if prompted). I run a Vostro 1500 and haven't had any issues with the wifi not working once the drivers were loaded.

P.S. Make sure the little wifi catcher button on the left side of the computer is on( the >> arrows are the on side and the 0 is the off side of the switch, and pushing the button past the >> arrows resets the connection if it needs a refreshing)

hope some of that helps

---

### Post by deadbeef on 2008-12-15
Yes, both connections were functional before the install.  
I've been thinking about downloading another .iso and trying again, it's not as if that's a difficult thing to do.  So I might try that right now.

It's interesting that nobody addressed the wierd "wl" driver in the hardware drivers prog.  Oh well.  I'm off to try again.  Thanks and I WILL post again re: this debacle. 
...

---

### Post by falcon61102 on 2008-12-15
Did you install straight from the LiveCD Ubuntu enviornment or did you restart and select Install from the CD boot Menu?

If you installed straight from the LiveCD enviornment, that could be where you're system started using the "wl" driver.  Any changes you make while using Ubuntu off the LiveCD before installing will stay in effect once Ubuntu is installed.  Ubuntu may have used the "wl" driver much in the same way that it uses the vesa driver for graphics, as a very basic but functional driver until the correct one can get installed.

If you haven't already started the re-install process, I would suggest starting it straight from the boot menu.  Or you could attempt to remove the wl driver from your current installation and see if Ubuntu recognizes your Broadcomm chips.

---

### Post by deadbeef on 2008-12-16
I installed from USB and it appeared to go pretty straightforward.  I don't recall any choices for anything other than a "full" install.  I installed over XP and never ran the Live version and/or made any changes.  

And I've been checking the log.  The radio switch functions and the OS sees it.  The OS also recognizes the WLAN card and starts the process of connecting to my SSID, but there is a suspicious bunch of error messages.

I'll try to paraphrase;
NetworkManager: Found radio killswitch /org/freedesktop/Hal/devices/dell_wlan_switch
"            ": eth0:driver is 'NULL9infor.linux.driver)'.
"            ": Found new Ethernet device 'eth0'.
"            ": (eth0): exported as /org/freedesktop/Hal/devices/net_00_19_b9_85_b8_f1
"            ": wlan0: driver is 'NULL(info.linux.driver)'.
**I'll skip some lines here
laptop firmware_helper[5499]: main: error loading '/lib/firmware/b43.ucode5.fw' for device 'devices/pci0000blahblahblah.../firmware/ssb0:0' with driver '(unknown)'
NetworkManager: <WARN> nm_device_hw_bring_up(): (wlan0): device not up after timeout!
"            ": (wlan0): deactivating device (reason:2)

I feel like this is going to be an extremely east fix for someone out there.  Anyone?

---

### Post by deadbeef on 2008-12-18
Nobody?  

Is this simply an issue that needs a re-install to fix?  I think it might be simpler than that.  Can someone interpret this so that it makes sense to me?

---

### Post by notwen on 2008-12-18
First let's see if the install is even recognizing your Ethernet or wireless cards.  

Run 'lspci' in a terminal and post the output here.

---

### Post by deadbeef on 2008-12-23
Yep.  The OS recognizes the cards, WLAN and NIC, and I'm still pretty sure that mine is a driver issue or something like that.  I used UNetbootin and a fresh download to install from usb during boot.  ALL the same issues with this new install.  I can't post the entire output of lspci, but if you know what you're looking for I can search and report back.  I'm thinking about installing an earlier version of Ubuntu now.  Maybe if I go back a release or two, I can get it to work well enough to update.  I'm at the end of my rope here.

---

### Post by deadbeef on 2008-12-25
Back again...   Sorry folks, but this place is my only hope.  

I re-installed using the same method and am now running the OS from the USB drive (Live Mode?). Now I get two entries in the hardware driver manager window.  One for the Broadcom B43 wireless driver (fwcutter, which obviously isn't working) and one for "wl" (Absolutely no information).  If I choose to activate the Broadcom driver, there is a progress window like something is happening, but nothing happens.  No error message, no activation, nothing.  I can de-activate the "wl" driver, but that doesn't seem to do anything either.  

Using Synaptic is different in the "Live Mode" also.  When I previously searched the library for ndiswrapper nothing appeared.  Now I can find ndisgtk, but no ndiswrapper.  

What The Hell is wrong with this computer/install/situation?

---

