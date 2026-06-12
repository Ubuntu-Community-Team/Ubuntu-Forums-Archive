---
title: "PS110 Print Server"
date: 2006-04-13
forum: Desktop Environments
---

### Post by Whhpssh on 2006-04-13
Hi all,

I posted this in the user support forum but haven't gotten a response that helped me.  Can someone help me out?  I am really impressed with Ubuntu and have been able to find answers for all my questions except this one.

Thanks for any help.

[quote="whhpssh"]Hi all,

Hope someone can help me out here.  I have a Brother MFC-8300 connected to port 1 of a PS110 print server.  I've been trying to setup the printer today but can't seem to get it to communicate.

I've been trying "System", "Administration", "Printing", then adding a printer but, though it accepts my settings, nothing prints when I try to print a test page.

I just installed Ubuntu a couple days ago and I'm a noob with regards to Linux.  I can update packages if needed and I can do any terminal commands needed if someone can point me in the right direction.

Thanks for any help.:D[/quote]

---

### Post by UbuntuJohan on 2006-04-13
Hi,

I'll try to help you. I have a PS110 and have used it from ubuntu and it worked fine. But I rememeber that it wasn't obvious what need to be done to get it going.
When I reboot the PC I'll go into my ubuntu partition an check it.
I post what I did when I have done that.

Cheers
//Johan

---

### Post by UbuntuJohan on 2006-04-13
I thought I might as well do it while I still remembered it.

You add it as a network printer and select 
Unix-printer (LPD)
In the host field you enter the IP of your P110
and in the cue field you enter the port your printer is connected to on the PS110 e.g P1 or P2. 
Then you select the brand and model of your printer.

Then try to printout a test page.

With my pinter a HP Deskjet 930 C I must switch it on myself if I print from Ubuntu or Windows 2000 but from XP the printer swithes on automatically if it's off. But I think that is because they use different drivers.

Since I use a swedish ubuntu I might have gotten the translation of the parameters above slightly wrong but I hope you'll be able to figure it out anyway if not give me a shout.

I hope this helps.

Cheers
//Johan

---

### Post by Whhpssh on 2006-04-17
Thank you, Johan, for your help.  I am able to communicate with the printer now but it's printing a bunch of blank pages instead of the test page.  I assume it's a driver issue.  I'll research further.

I appreciate you taking the time to help me out.  :)

---

### Post by Whhpssh on 2006-04-18
UPDATE:

Johan, thanks again for your advice.  I was able to get the printer working by choosing the laserjet driver instead of the recommended hl7x0.  I now have a working printer.

:D

---

