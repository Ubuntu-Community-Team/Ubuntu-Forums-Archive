---
title: "Print jobs not always being sent to networked printer"
date: 2009-03-31
forum: General Help
---

### Post by BlueNoteMKVI on 2009-03-31
On my network, I have a Windows machine with a printer attached.  That printer is shared to the network via Samba.  On that same network I have a variety of other boxes, some running Windows, some running various flavors of Linux (mostly Kubuntu).  All of them can print to the networked printer without problems EXCEPT my laptop.

On my laptop, I can always print from Thunderbird.  Printing from FireFox is difficult.  I have found that I can follow this procedure and it works every time:
-open printer configuration GUI
-remove printer
-re-install printer using all of the same settings
-switch to Firefox and print
When I do this, the first print job works fine.  If I try to print again, no go.  All of the print dialogs come up, the progress window comes up and appears to finish.  Nothing comes out of the printer.  If I go back to the printer config and remove then reinstall the printer, I can print again (but only one print job).  There seems to be no relationship between the size of the job and whether or not it prints.

Other programs are spotty.  Kate works sometimes, sometimes not.  I can't find a pattern there.  OpenOffice is the same way.  Restarting cups has no effect.  Rebooting has no effect.

When FireFox prints the one successful print job, I see this line in /var/log/messages:


```
Mar 31 11:40:19 miles kernel: [93096.229038] type=1503 audit(1238517619.936:26): operation="inode_permission" requested_mask="::rw" denied_mask="::rw" fsuid=7 name="/dev/tty" pid=10298 profile="/usr/sbin/cupsd"

```

I see the same log output when I print from Thunderbird - works every time.

I've compared the setup to my desktop which is also running Kubuntu.  As far as I can tell everything is the same.  The desktop works fine, every time.

In case it's relevant, the printer is a Xerox Phaser 8400B.  I'm using the driver that came with Kubuntu.  My laptop is running the latest Kubuntu, everything up to date.  The desktop box is also the latest version but is a few updates behind.  The machine attached to the printer is running Windows XP with all of the latest updates from Microsoft.

Any ideas of what's causing this or how to troubleshoot?

---

### Post by DeMus on 2009-03-31
When a print job has failed to print, is it possible to:

[LIST=1]
[*]communicate with other computers in your network? If so, Samba is still running fine, if not, it could be Samba related.
[*]print from another computer? If so, it must be in the laptop, if not, it could also be the Windows side of the network.
[*]print to pdf on the laptop? If so, printing itself is okay, if not it could be cups related.
[/LIST]
I'm sure you have tried all these things already, but I wrote them just to be sure.

---

### Post by halitech on 2009-04-09
and not to say Kubuntu doesn't have a good driver but maybe download the proper driver from Xerox as well

[http://www.support.xerox.com/go/results.asp?Xtype=download&prodID=8400&Xlang=en_ZA&Xcntry=ZAF](http://www.support.xerox.com/go/results.asp?Xtype=download&prodID=8400&Xlang=en_ZA&Xcntry=ZAF)

Just download the file, extract it and use the proper PPD file for the 8400b when you reinstall.

---

