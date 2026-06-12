---
title: "Virtual Box usb problems initialising"
date: 2008-05-01
forum: Desktop Environments
---

### Post by BXA121 on 2008-05-01
installed vitual box.
all went well, however, if i select settings i get this error..


"Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.


Result Code: 
0x80004005
Component: 
Host
Interface: 
IHost {81729c26-1aec-46f5-b7c0-cc7364738fdb}
Callee: 
IMachine {31f7169f-14da-4c55-8cb6-a3665186e35e}"

i dont know what it means. 
but i dont have any USB settings that i can change. 
any ideas?

---

### Post by IrishGandalf on 2008-05-01
i've the exact same problem, can someone plz find a solution to this?

---

### Post by the_maassk on 2008-05-02
Follow this:

[http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html](http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html)

It worked for me. Let me know if you have any problems. Remember to reboot after following the guide. It does need a reboot.

---

### Post by IrishGandalf on 2008-05-16
i tried the link above and ur right the usb options did appear under the settings menu after a restart. My only problem is now the virtual machine (in my case windows xp pro) refuses to detect any connected devices including my built in webcam as this is classed as a usb device.

---

### Post by turezky on 2008-05-16
IrishGandalf, there's no big deal with webcam :) You can't use it in any way inside the virtualbox. But I do agree with the connected USB devices like flashdrives and portable mp3 players. There's an ongoing bug with this USB-proxy-device stuff, and it is related to the virtualbox itself.
Hope, now that Sun has bought them, they will finally have time to remove this flaws..

---

