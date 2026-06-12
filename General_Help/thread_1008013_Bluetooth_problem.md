---
title: "Bluetooth problem"
date: 2008-12-11
forum: General Help
---

### Post by Vishnu V on 2008-12-11
when i tries to browse files on my Sony Ericsson  K750i the following error msg comes
**Could not display "obex://[00:12:EE:34:5D:F7]/"**
i can send files from my phone to pc if Bluetooth file sharing is active
and i can't send files from pc and when i tried it this error msg displayed **obex push file transfer unsupported**

what can do to solve this problem






thanks

---

### Post by fragos on 2008-12-11
I'll assume you're attempting to right click on a file aand use Send To. For some strage reason that stopped working with 8.10. However you can send send files if you right click on the bluetooth icon in the upper applet bar and select "Send files to device".

---

### Post by Vishnu V on 2008-12-12
i tried that way too then this was the error org.openobex.Error.connection refused
i can send files to nokia 6300 in both ways

---

### Post by stolk on 2009-02-22
hi,

try this:

open a command promt and type: "bluetooth-wizard".

then select your device, it will give you a access code to make a connection between your PC and the phone.

then try to send the files you want the way you already tried (send to), or type "bluetooth-sendto" in the command line and hit enter.

i just worked for me!

---

### Post by fragos on 2009-02-22
> **stolk said:**
> hi,

try this:

open a command promt and type: "bluetooth-wizard".

then select your device, it will give you a access code to make a connection between your PC and the phone.

then try to send the files you want the way you already tried (send to), or type "bluetooth-sendto" in the command line and hit enter.

i just worked for me!

Click the Bluetooth applet icon and selecting Setup New Device... takes you to the same wizard.

---

### Post by stolk on 2009-02-22
I use Xubuntu and i think i've disabled it (the applet icon), because there's no icon at my taskbar.

But thanks for your reply anyway :)

I hope this problem will be fixed in next version of Ubuntu

---

### Post by stolk on 2009-02-22
I use Xubuntu and i think i've disabled it (the applet icon), because there's no icon at my taskbar.

But thanks for your reply anyway

I hope this problem will be fixed in next version of Ubuntu

---

### Post by crunchfighter on 2009-02-28
System/Preferences/Bluetooth - Select "Always visible"

---

### Post by substanceD on 2009-02-28
You might try installing Bitpim to transfer files if Obex isn't working--[this article]("http://ubuntuforums.org/showthread.php?t=885765") was very helpful when I was trying to get Ubuntu to talk to my phone.

---

### Post by Roy Damman on 2010-06-01
Install package openobex-apps. It worked for me with Ubuntu 9.10.

---

### Post by krishnab108 on 2011-06-24
I could send files using Bluetooth to my phone, but I can't browse my mobile via Bluetooth...

I get the error that was posted on the 1st message in this thread...

If I send files, that will be delivered to Inbox and not directly to Memory card...

I was able to browse files on Ubuntu 10.10 and older versions...

---

