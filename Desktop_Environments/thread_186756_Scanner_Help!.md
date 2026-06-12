---
title: "Scanner Help!"
date: 2006-06-02
forum: Desktop Environments
---

### Post by garretwp on 2006-06-02
I have an HP ScanJet 3970 and I did a search for drivers and was able to find them using the scanjet 3900 series deb that was mentioned on this forum. My issue is, when I go to run xsane, I get an error saying that permission has been denied in opening the device. Is there something that I am missing here? How do I allow permission to open the device?

Garrett

---

### Post by garretwp on 2006-06-02
No one knows how I can get past this permission denied problem?


Garrett

---

### Post by No Whammies on 2006-06-02
[http://ubuntuforums.org/showthread.php?t=101775&highlight=hp+3500](http://ubuntuforums.org/showthread.php?t=101775&highlight=hp+3500)

Not sure if it's what you're looking for, but it's a thread dealing with this same problem for the 3500 series scanners by HP.  I don't know if this backend will help, but it was the best I could find.

---

### Post by garretwp on 2006-06-03
Thanks for the help. The problem that I am having is that when i go to load up say xsane, i get a message saying that i do not have the permission to load the appropiate resources for the scanner. Not sure how to get around this.

Garrett

---

### Post by garretwp on 2006-06-03
This is the message I am getting: Failed to open device "hp3900:libusb:005:002 Access to this resource has been denied. How do i get around this so all the other users can use the scanner with xsane.

Garrett

---

### Post by garretwp on 2006-06-03
I have a fix for my problem. I had to go into /dev/bus/usb/005 and do a chmod a+w on 002 and all worked out well!

I hope this helps or anyone who might run into a similar issue.

Garrett

---

### Post by jdarias on 2006-12-18
Garret, thanks for the tip.
Sadly for me, i have to do it everytime i boot and try to use the scanner. 
Sometimes is hp3900:libusb:004:004 or hp3900:libusb:004:003
Is there  any way to grant permission to this thing permanently?

---

