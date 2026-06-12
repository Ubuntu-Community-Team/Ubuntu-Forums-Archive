---
title: "Edgy gnome bluetooth phone help please"
date: 2006-11-10
forum: Desktop Environments
---

### Post by Peepsalot on 2006-11-10
I tried all night last night to get bluetooth connectivity to my phone, but it's just not working.  It appears all the bluetooth apps have changed significantly in the recent past, so that any tutorial I have found ends up being obsolete.

I'm stuck at the part where I try to connect and there is no "pin_helper" or "passkey_agent" set up correctly on my computer.  The phone prompts me for a PIN, but it fails every time.  The computer never asks for a matching pin.

---

### Post by Peepsalot on 2006-11-10
Well i finally got it working.  Most of the tutorials say to put this line in your hcid.conf
```
pin_helper /usr/bin/bluez-utils;
```
The problem is though, the version of bluez-utils in the edgy repos doesn't support this anymore though.


So the only solution I have found for this is to run the command ```
passkey-agent --default /usr/bin/bluez-pin
```
I think passkey-agent is part of the gnome-bluetooth package, but I'm not sure since I was just installing a bunch random bluetooth related crap and praying.

The info that led me to this solution is here:
[http://forum.club.mandriva.com/viewtopic.php?p=268897&sid=8ee3dc8f444bfd9d71f6f7f690db1f32](http://forum.club.mandriva.com/viewtopic.php?p=268897&sid=8ee3dc8f444bfd9d71f6f7f690db1f32)
and here:
[http://qa.mandriva.com/twiki/bin/view/Main/MandrivaLinux2007Errata#Issues_with_Bluetooth_support](http://qa.mandriva.com/twiki/bin/view/Main/MandrivaLinux2007Errata#Issues_with_Bluetooth_support)

---

### Post by Jad on 2006-11-13
I have same problem but yet couldn't figure out how to get it working

---

