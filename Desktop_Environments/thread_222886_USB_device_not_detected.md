---
title: "USB device not detected?"
date: 2006-07-25
forum: Desktop Environments
---

### Post by core on 2006-07-25
Hi all.

I've installed kubuntu dapper, and I wanted to get my Nokia phone device detected. I'm preety sure it was detected a few weeks ago, I even remember running Nokia PC Suite on windows under VMware player, and "Nokia N90" appear as a USB device on the top of vmware-player window.

But now it doesn't appear. My phone doesn't even react to the connection, a usb icon should appear on it's screen.

I've tailled /var/log/messages and got something like this:

Jul 25 21:22:45 core kernel: [17602726.080000] usb 1-3: new full speed USB device using ohci_hcd and address 4
Jul 25 21:22:46 core kernel: [17602727.168000] cdc_acm 1-3:1.8: ttyACM0: USB ACM device
Jul 25 21:22:46 core kernel: [17602727.180000] usb 1-3: USB disconnect, address 4
Jul 25 21:22:46 core kernel: [17602727.224000] usbcore: registered new driver cdc_acm
Jul 25 21:22:46 core kernel: [17602727.224000] drivers/usb/class/cdc-acm.c: v0.23:USB Abstract Control Model driver for USB modems and ISDN adapt

Even if i find that file, how can I enable it as a normal USB device like before, so I can use it on vmware?

Thanks in advance guys.

---

### Post by jimbob on 2006-07-25
So far, things look normal.  That is exactly what I get when I connect my USB dial-up modem and it works great.

I don't know anything about the Nokia hardware but isn't that the way it is supposed to connect?

Go to System->Administration->System Log, scroll to the bottom and watch what happens when you plug in the usb.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by core on 2006-07-25
I dunno, but I just can't get a connection, not even my cellphone detects any connectable hardware on the other side. I tried it on a windows system and it worked. Somehow it isn't getting bridged through kubuntu..

Anyways, that "System->Administration->System Log" is a gnome thingy, i use KDE only here, installed kubuntu from scratched and I didn't want to mess things up more. Does that option do something similar to 'tail -f /var/log/messages'?

Still, awating ohter sugesstions from the undergound :p And thanks jimbob.

---

