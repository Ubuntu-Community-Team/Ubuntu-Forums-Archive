---
title: "ubuntu will not detect my router"
date: 2009-06-22
forum: General Help
---

### Post by MasterZURG on 2009-06-22
I have Ubuntu 7.10 running on my Ps3 and I need to connect the internet to it. Ubuntu will not detect my rounter/internet connetion's existance. It worked on My laptop but that has Vista. The computer controlling the laptop is Vista aswell. I have a linksys router and a Comcast Cable Modem. Please help I'm trying to do somthing and I havnt came this far for nothing!:confused:

---

### Post by bubbhasdance on 2009-06-22
This was a problem for me when I first installed Ubuntu 9.04. My setup is similar to yours (Belkin router and cable modem), so hopefully this'll help some. 

I had to reset my router (should be somewhere on the router itself, usually on the bottom) and re-install the software CD that came with it. Afterwards, all was fine. 

You may try that, or even going onto the router settings page (you'll need to use your home computer, obviously) and seeing if everything is synced with what you have on your PS3. Check SSID's, which security key you're using (if any), see how that works.
[I]
Is the connection you're attempting to make wired or wireless? [/I]
If it is wireless, try connecting it with Ethernet to see if it connects at all.

---

### Post by JeffersonX on 2009-06-22
What is the output from ifconfig and lspci?

---

### Post by MasterZURG on 2009-06-22
Its Wireless. And I have no Idea what eighther of those mean. lol Im a noob. Ty for the help! Feedback in a few.

---

### Post by bubbhasdance on 2009-06-22
Go to your terminal (Applications-->Accessories-->Terminal) and type in 'ifconfig' (without the quotes) and paste the output here. After that type in 'lspci' (w/o quotes) and do the same.

I wonder how well Ubuntu runs on PS3s...

---

### Post by MasterZURG on 2009-06-22
ur first comment didnt and I dont have no Ethernet cable but Ill try the terminal thing :)

btw, Ubuntu runs like a charm on ps3

---

### Post by MasterZURG on 2009-06-22
When I do the terminal thing it says "error fetching interface information: Device not found" after I do ifconfig. but then I do the ispci and a bunch of stuff pops up then starts a new terminal thing. what now?

also sry for double post

---

### Post by bubbhasdance on 2009-06-22
> **MasterZURG said:**
> When I do the terminal thing it says "error fetching interface information: Device not found :(

also sry for double post
I am not all that efficient when it comes to wireless connections, but if it did not find your device (router, I'm guessing), then it's not recognizing it.

Anyone here care to help this guy? :)

---

### Post by MasterZURG on 2009-06-22
> **bubbhasdance said:**
> I am not all that efficient when it comes to wireless connections, but if it did not find your device (router, I'm guessing), then it's not recognizing it.

Anyone here care to help this guy? :)
I edited my post lol read it this time

---

### Post by bubbhasdance on 2009-06-22
Ok, copy and paste what text came up with lspci.

---

### Post by MasterZURG on 2009-06-22
> **bubbhasdance said:**
> Ok, copy and paste what came up with lspci.
...How? Im talking to u on a diffrent machine. lol

---

### Post by MasterZURG on 2009-06-22
Got it
```
    Usage: lspci [<switches>]

-v              Be verbose
-n              Show numeric ID's
-nn             Show both textual and numeric ID's (names & numbers)
-b              Bus-centric view (PCI addresses and IRQ's instead of those seen by the CPU)
-x              Show hex-dump of the standard portion of config space
-xxx            Show hex-dump of the whole config space (dangerous; root only)
-xxxx           Show hex-dump of the 4096-byte extended config space (root only)
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]   Show only devices in selected slots
-d [<vendor>]:[<device>]        Show only selected devices
-t              Show bus tree
-m              Produce machine-readable output
-i <file>       Use specified ID database instead of /usr/share/misc/pci.ids.gz
-D              Always show domain numbers
-M              Enable `bus mapping' mode (dangerous; root only)
-P <dir>        Use specified directory instead of /proc/bus/pci
-F <file>       Read configuration data from given file
-G              Enable PCI access debugging

  
```

---

### Post by jsoellner on 2009-06-22
To me it sounds like the wireless hardware in the PS3 isn't supported by Ubuntu (or it's faulty).

The best way to check is to get hold of a standard RJ45 network patch cable from somewhere and try connecting to the router with that.

You could also try a Linksys gaming adapter, which is a wireless device that plugs into the ethernet port on your PS3.  Normally the PS3 would just see this as a wired connection (though that is with the standard OS and not Ubuntu).

Good luck!

---

