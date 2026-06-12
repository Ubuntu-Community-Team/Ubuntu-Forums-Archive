---
title: "IPP Serve to OSX = Madness! PLEASE HELP"
date: 2006-07-30
forum: Desktop Environments
---

### Post by gandalf2041 on 2006-07-30
My sanity can take no more...I have a Ubuntu 6.06 box with a HP PSC 2210 multifunction printer attached via USB.  Cups reports the uri as "hp:/usb/PSC_2200_Series?serial=xxxxx"  How do I tell if the printer is setup correctly for IPP and what the correct ipp:// address is?  No matter what I try, my wife's iBook G4 w/Tiger OSX can NOT see the printer, nor can I even force it to the ipp address that I think it should be (ipp://192.168.8.10/PSC-2210).  I've wrestled with this for days by searching the forums and googling. Someone out there must know how to make this work.  Any help would be GREATLY appreciated!

Gandalf2041

---

### Post by llamakc on 2006-07-30
Have you checked the logs in /var/log to see what the error is? Have you futzed with cups.conf any?

---

### Post by gandalf2041 on 2006-07-30
I looked in /var/log/messages but now it occurs to me that I didn't check the actual cups log. Boy, have I ever futzed with the cupsd.conf! LOL :rolleyes: Do you have any idea how I can tell if I have the Ubuntu box setup correctly?

---

### Post by gandalf2041 on 2006-08-01
Finally!!  Aside from changing the Allow directive in  <Location></Location> to accept my local network, the only other change was to the ports.conf file in the /etc/cups/cups.d directory. Once I commented out the "Listen localhost:631" directive, the printer popped right up in the OSX printer utility. I was making it waaaaay harder than it needed to be #-o

---

