---
title: "Network printer sharing"
date: 2009-03-29
forum: General Help
---

### Post by larryma on 2009-03-29
I have Ubuntu 8.10 running on a Dell precision M60 laptop within a wireless network. One of the computers on the network is running Windows Vista and has a printer (HP Photosmart 7760) attached by USB. The printer has sharing enabled and another computer on the network, Windows XP, can print to this with no problem.

I now want to print to that printer from my linux box, but am not sure how to do it. I can go to System->Administration->Printing->New->Printer, and I get the printer configuration box. However, I can't find the printer to connect using this method.

When I go to the "Windows printer via Samba" choice, it's asking for some smb:// address that I don't know how to get. When I browse using the SMB browser, it doesn't find anything.

The other question I have is about the driver. I think I need a the Linux driver for this HP, correct?

Thanks in advance for your help.

Larry

---

### Post by cariboo on 2009-03-29
Are all the computers in the same workgroup? Ubuntu defaults to workgroup whereas XP and Vista Home default to MSHOME while XPPro and VIsta Office/Ultimate default to workgroup.

Jim

---

### Post by larryma on 2009-03-29
Thanks!

When I look at the workgroup name, the Vista computer with the printer is on WORKGROUP, and the other XP computer on the network is on MSHOME.

Both of these workgroups show in the ubuntu printer setup wizard, but the name of the printer doesn't. That is, when I click or double click on WORKGROUP, nothing shows up.

I see that the smb syntax is given as [workgroup/]server[:port]/printer, but I don't know what to put in there besides the workgroup, though the printer name may be "hp photosmart 7700 series" as noted in the box.

What should I do next? Thanks again for your help.

Larry

---

### Post by mdp25 on 2009-03-31
I'm having the same problem. I tried the Ubuntu help files but the instructions don't match the printer setup choices that I have.  I assume that the help doc is from an earlier version of Ubuntu (I'm using 8.10).  I'm on the same workgroup and can share files between the computers (Vista and Ubuntu) just fine. Any help will be much appreciated!

---

### Post by larryma on 2009-04-12
I actually just got this to work. Not perfectly straightforward, but maybe I should have caught on before. Anyway, on the 'New Printer' popup under 'Windows Printer via SAMBA', there is a guide for typing into the url box: smb://[workgroup]/server[: port]/printer.

I knew the workgroup, and searching around on other shared computers I found the port (USB001) and guessed the printer name (which seemed to vary depending on where you look). For server, I assumed the name of the computer that the printer hangs off of.

And it worked. Seems I can print now across the network.

Larry

---

### Post by Slim Odds on 2009-04-12
I actually find it a lot easier to share the printer without samba.

The default printer sharing in Ubuntu will use CUPS and IPP. Windows knows how to use IPP, so just skip samba.

You just tell Windows that you want a network printer and the location is:```
http::/<address of the printer server>:631/printers/<Name of you printer>
```You might have to look to see what you printer name is (for example, mine is DESKJET_930C)

---

### Post by jimford on 2009-04-14
This has had me gibbering with rage over the last 2 days!

I've got a LaserJet 1100 printer on an XP machine and want to print to it from a Ubuntu laptop.  

Simple really? NO!

I've tried samba via CUPS, and the XP box insists on authentication, which I've been unable to satisfy in any way.

I seized on the above post re. IPP with wild cries of delight, but my joy was shortlived because I get messages that the printer 'may not be connected'.

<sigh> - I'm now resigned to manually connecting a printer every time I want to print.

Jim

---

### Post by Slim Odds on 2009-04-14
> **jimford said:**
> 
I've got a LaserJet 1100 printer on an XP machine and want to print to it from a Ubuntu laptop.  

...

<sigh> - I'm now resigned to manually connecting a printer every time I want to print.



Sorry, my bad.... I thought that the printer was connected to a linux machine and you were trying to printer from windows.

My advice is to find a crappy old machine and put Ubuntu on it to act as a printer server....

---

### Post by Nwwmac on 2009-04-26
I'm a brand new to Unbuntu guy running 9.4 on an iMac. I have an HP printer connected to a dual band Time Capsule via USB. The iMac and the Time Capsule are connected via Ethernet. 

I found my printer - HP LaserJet 1022 - in the add printer dialogue but get an error about CUPS. 

Can anyone tell me where to look for the network information I need and what connection method is easiest? Networking is not a strong point! :)

---

### Post by Nwwmac on 2009-04-26
I did manage to get it working! 

The syntax for the URI was: 

socket:// [IP of router] :9100

Hope that helps someone else.

---

