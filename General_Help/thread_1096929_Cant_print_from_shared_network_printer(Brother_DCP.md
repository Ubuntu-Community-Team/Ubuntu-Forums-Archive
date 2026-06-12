---
title: "Cant print from shared network printer(Brother DCP7020)"
date: 2009-03-15
forum: General Help
---

### Post by ztein on 2009-03-15
Hi.
I got a small network of two computers, one running Windows Vista Home(the printer is connected directly to it through usb), and second is Ubuntu powered that Im using right now to type this thread. Both of the computers connected to a Lynksys router WRT54G. I added the printer into Ubuntu using "Windows Printer via SAMBA" and installed the .PPD file for Brother DCP 7020 model of the printer. When I go to "Printer Configuration" I see the icon of the printer with a green check mark next to it.

Now when I try to print it prompts for an authenication, and i type in my username and password, after few seconds it prompts for authenication again but it doesn't print.

I went to "Properties of the Printer" and it says that its status is "Idle - Tree Connect failed (NT_STATUS_ACCESS_DENIED)".

And when I try to authenicate the printer now, and then click Verify I get "Print Share Inaccessible - This print share is not accessible".

How can I fix this problem and print from my Ubuntu PC to the shared printer on Windows Vista PC?

Thanks.

---

### Post by The MacNab on 2009-07-15
I am having the same problem. I am running Ubuntu 8.04 and trying to connect to printer bar, running on Samba server foo. I enter the device URI as smb://foo/bar and put in the appropriate PPD (HP Laserjet 4250dtn) but, when I try to print a test page, get the same error. Any ideas?

---

### Post by rick71 on 2009-09-11
I get the same error trying to print to an HP 9650 shared from an XP machine, using both 8.10 and 9.04.

---

### Post by NutmegCT on 2010-01-07
Interesting - I have exactly the same problem as described in the first post in this topic.

I want to print from my KosmicK laptop to the Canon printer; the printer is connected to my WinXP computer via USB.

I've never printed from this laptop before.  I "Add Printer", find the printer in the Windows/Samba menus, then find the printer and model, etc., then click Verify, enter the Windows machine's username and p/w, but always get "print share inaccessible".  If I plunge on through and click Print Test Page, I see the queue form, and printing gets to about 42%, but nothing comes out of the printer.  So after about 10 minutes I cancel the job.

The Add Printer function seems to perform flawlessly - except for that nasty "print share inaccessible" issue.

Is there any hope?

Thanks.
Tom

---

### Post by daemoncat on 2010-01-16
CAVEAT:
As the printer I'm accessing is on a WinXP machine, I'm not sure how much of this applies to Vista.

I notice that my printer device URI is formatted as > smb://WORKGROUP_NAME/WINDOWS_MACHINE_NAME/PRINTER_NAME

Is the "smbclient" package installed? For some reason, it wasn't on my Xubuntu laptop.

Googling that "ACCESS_DENIED" message led me to this thread:
[http://ubuntuforums.org/showthread.php?t=1169149]("http://ubuntuforums.org/showthread.php?t=1169149")
The author points out that Ubuntu flavours need to have the WORKGROUP_NAME specified.

Another thread suggested using the IP address of the Windows computer in the URI. The WinXP Pro computer my DCP-2070 is connected to doesn't seem to care. 

I'm not sure how reliable the IP address setting would be using DHCP (who doesn't these days? ... except me ;-)), unless you never ever turn off the computer.

Try giving those a shot.
Good luck.

---

### Post by NutmegCT on 2010-01-16
Thanks for the suggestions.  That workgroup/computername/printername is all there in the SAMBA properties.  Still get the same negative result.

You asked if Samba is installed.  I'm new to all this (obviously).  I just assumed that if the printer setup app gives me the SMB option, it had found Samba.

-> How can I tell if Samba is installed or not?

The KK Ubuntu seems very positive to me, except for a few problems.  Can't print to network printer, and some weird suspend/resume issues.

Anyway, thanks for the ideas.
Tom

---

### Post by Morbius1 on 2010-01-16
Give this a shot to fix **NT_STATUS_ACCESS_DENIED** problems with Windows attached printers:

Open **Terminal**
Type **sudo cp /etc/cups/printers.conf /etc/cups/printers.conf.bak**
[COLOR=Blue]*This will make a copy of the original conf file - just in case*[/COLOR]

Type **gksu gedit /etc/cups/printers.conf**

Look for a line that has this form:
> DeviceURI smb://VISTA_PC/HPDeskjetand change it to
> DeviceURI smb://[COLOR=Blue]guest@[/COLOR]VISTA_PC/HPDeskjet[COLOR=Blue]*Just add a guest@ in front of the vista machine name.*[/COLOR]
Save the file, exit gedit and back in the terminal type: [B]sudo service cups restart



[/B]

---

### Post by NutmegCT on 2010-01-16
Thanks Morbius.  After your suggestions, I now get "Cannot connect to CIFS host".

Well ... at least it's a different error message!

Thanks.
Tom

---

### Post by Morbius1 on 2010-01-16
Actually I was answering the original posters question which in retrospect was kind of silly since his post was 10 months ago :D
He had a specific error message which you did not.

---

