---
title: "Networking on Dell Mini 12"
date: 2009-05-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by DentonE on 2009-05-15
I have a new Dell Mini 12 with factory installed Ubuntu 8.04..1   I have had to re-install the OS twice in three days due to an inability to correctly set up my wireless security after several updates.  In the original setup, you can specify the TKIP option, but after the updates, this isn't available.  I have only been able to get back on the net after re-installing the OS.  Can anyone explain how to get this working so I can allow it to run the updates?  I am very new to Linux and not much of a computer genius to begin with.  Any help would be appreciated.

---

### Post by coffeeaddict22 on 2009-05-16
Hi,
Welcome to Ubuntu!
A bit more info would help.
Are you staying with 8.04 and getting the upgrades for that, or are you choosing the "Upgrade Distribution" option?
The exact problem is that your card is working but you can't access a specific encrypted network?  And are you trying to get WEP or WPA encryptation working?  (I'm also assuming you're running Ubuntu and not Kubuntu/Xubuntu etc)
Open a terminal(it's easier to cut and paste from), and type in:```
lshw -C network
nm-tool
```
and post the results back.  They're two separate commands; for more detail, you can type "man lshw" and "man nm-tool" into the terminal.  The man pages are your friend...

---

### Post by DentonE on 2009-05-18
First question, yes, I am just running updates, still on 8.04.1
Second question, I don't think the card is receiving anything.  On my other laptop I can see several networks in the neighborhood which broadcast their ID, but on this Dell I can only see one, which is the one I set up, and there is no  connection.  The router is set up to use WPA personal with TKIP encryption.  When I ran the updates, it upgraded the network manager applet from 0.6.something to 0.7.0 and the set up screen isn't the same, it won't allow me to select TKIP, I guess it auto detects.  It looks to me like to new network manager applet is just not allowing the network card to operate, as I can't see the other networks in the area.  I assume it should just display them when I left-click on the NM icon the same as the old version did.  This is Ubuntu, Kubuntu or Xubuntu.
The lshw command gets nothing.  The nm-tool gets the following:
  	 	 	 	 	 	  denton@denton:~$ nm-tool  
 

 NetworkManager Tool  
 

 State: disconnected  
 

 - Device: eth0 ----------------------------------------------------------------  
   Type:              Wired  
   Driver:            r8169  
   State:             unavailable  
   Default:           no  
   HW Address:        00:21:70:F5:AE:C0  
 

   Capabilities:  
     Supported:       yes  
     Carrier Detect:  yes  
 

   Wired Settings  
 

 

 - Device: eth1 ----------------------------------------------------------------  
   Type:              802.11 WiFi  
   Driver:            wl  
   State:             disconnected  
   Default:           no  
   HW Address:        00:23:08:6D:75:E7  
 

   Capabilities:  
     Supported:       yes  
 

   Wireless Settings  
     WEP Encryption:  yes  
     WPA Encryption:  yes  
     WPA2 Encryption: yes  
 

   Wireless Access Points  
     NUNYA:           Infra, 00:1E:58:24:8D:C9, Freq 2437 MHz, Rate 0 Mb/s, Strength 100 WPA  
 

 

 denton@denton:~$  
 denton@denton:~$ 



Thanks for your help
Denton

---

### Post by coffeeaddict22 on 2009-05-19
OK.  First up, sorry, I forgot you won't have lshw (you'll be running the netbook remix).  It's a small program that lists your hardware, so is really good for troubleshooting.  Go into System/administration/Synaptic Package manager, search for lshw, and install it.  If nothing else, it's interesting to see what's on there...
Easiest way of finding out what you're running is to try ```
uname -a
```-it's what the kernel reports the version that's running is to any program that asks.

Second, it'd be well worth your while to upgrade to 8.10 at least.  Wireless networking has come ahead in leaps and bounds over the last 12 months.  I know in 8.04 my wireless used ndiswrapper as the native Linux drivers didn't work.  I'm now running the same driver you've got (wl is one of the Broadcom linux drivers).  

The next option is to uninstall and then reinstall network manager.  Open a terminal and enter
```
sudo modprobe -r NetworkManager
``` then
```
modprobe NetworkManager
```

---

### Post by tyroeternal on 2009-05-19
I did some searching around sounds like a problem with network manager .7 based on the forum threads I found for suse and fedora that all said the same thing you are saying.

Upgrading past the 8.04 dell version has issues with the Mini 12's video drivers.  At the moment 8.10 video is not working well if at all after a kernel upgrade that went through.  I am running Jaunty using some basic 2d drivers that were just recently released on the ubuntu-mobile ppa.  I would recommend either not applying the updates (which is a pain) or installing jaunty.

Later today I can check my Mini 12 running Jaunty to see if tkip is an option (I think it is, but I'll have to make sure).  If things work right I could show you how to install jaunty and add the needed video drivers (it is easy).

---

### Post by tyroeternal on 2009-05-20
Sorry it took a bit long to post again.  I did not see anything about specifying tkip, so I would assume that it still attempts to figure the answer out for itself.  It may be working better with newer versions of network manager, but all I use is WPA2.

In reading around I came across another post that talks about the same problem of using WPA with tkip.  Around page five they seem to come up with a working solution where they use gconf-editor to specify that network-manager attempt to use only tkip.
[http://ubuntuforums.org/showthread.php?t=970236](http://ubuntuforums.org/showthread.php?t=970236)

I hope that this works for you!

---

### Post by DentonE on 2009-05-21
Thanks for the info all.  Tyro, I had found the same thread you mentioned and tried to use the gconf-editor, but I never had any success.  I may try to use your advice and step up to Jaunty if you have already done it successfully on a Mini12, I was trying to avoid that because I heard there were many issues with it, but it sounds like specifying TKIP may still be an issue there as well.  For now I am back to the original load and just avoiding updates.  I am now away from my network and will be for the next month or so, so I can't test any new ideas until I get back to the US.  Coffe, when I get back home I will try what you suggested about removing and re-installing the network manager and post the results.  Thanks again for the help!

---

