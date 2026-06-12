---
title: "CUPS/Samba Printing over the network. How do I do it?"
date: 2009-05-31
forum: General Help
---

### Post by Roasted on 2009-05-31
Yes - I have searched the forums.
Yes - I have read several tutorials regarding how to set up network printing with Ubuntu.

Yes - I STILL am having issues with it despite what I've done so far. So after several hours of troubleshooting, I'm here to ask blatantly - how the hell do I get this working?

I'm on an Ubuntu 9.04 machine, and I have an XP Professional machine that I want to connect to my Ubuntu printer - Epson Stylus CX4800.

In the printer settings under system - admin - printers - server - settings I checked publish shared printers connected to this system. I also have my printer shared. When I right click the printer - properties - policies all 3 checkboxes are ticked (enabled, accepting jobs, shared). 

Then on the XP machine when I go to start - run - my server - right click printer - hit connect - link to driver and install, it appears. At first it says access denied, unable to connect. When I reboot the xp computer, it says ready. When I test print, it simply sits here. It doesn't do anything. No errors or anything. It. Just. Sits. Here. Doing. Nothing.

I've spent a good chunk of my Sunday afternoon trying to figure this out. So now, I ask.. how do I connect an XP machine to a printer shared by Ubuntu? What am I doing wrong? What do I need to do yet?

---

### Post by mb_webguy on 2009-06-01
Well... is Samba working?  Have you tried sharing a folder on your Ubuntu machine and accessing it from your XP machine?  If you can't access Samba shares, then you won't be able to access a printer through Samba either.  Depending on what changes you may have made intentionally or inadvertently to the Samba configuration, you might need to change the security settings, or the entry for the printer share.

---

### Post by Roasted on 2009-06-01
I have installed "system-config-samba" from the repos, which is a very simple gui to set up shares, access, etc with Samba. I set the printers to be accessible by everyone. This program automatically changes the smb.conf when I make changes in the gui.

And yes, I can access my samba shares fine. I'm just not sure why my XP install is saying access denied when, as far as I can tell, everything is set to allow all users to print.

Side Question Completely Unrelated - If I set a folder to be shared, must samba be installed to make it work? If so, what is the advantage of setting up a samba server as opposed to just sharing folders out? Can you password protect them like you can with samba?

---

### Post by timzak on 2009-07-12
I have found when setting up a samba printer that I must first navigate via samba to the machine with the printer, then open the print folder.  Once I input the machine username and password, then I go into Printing and set up the samba printer.  If you need help beyond this let me know and I'll do my best.

---

### Post by JKyleOKC on 2009-07-13
> **Roasted said:**
> I'm just not sure why my XP install is saying access denied when, as far as I can tell, everything is set to allow all users to print.This may not help you much, but I'm having problems printing from WinXP via samba to a CUPS printer on Xubuntu. I get that same message -- but the test pages print anyway!

However when I try to print a page full of photos (from Microsoft Publisher, as proofs for a newsletter that I edit), the printer lights blink as if it's receiving data, but it never completes and prints. The logs indicate that the job completed properly, however.

I then added another version of the same printer on the CUPS box, using a PostScript PPD instead of the FooMatic one installed initially, and next set up that version on the WinXP system as a new printer. Now it seems to be working properly although it's horribly slow when doing intensive graphics.

I'd still like to know how to do away with that "access denied" status since it's obviously not the case.

---

