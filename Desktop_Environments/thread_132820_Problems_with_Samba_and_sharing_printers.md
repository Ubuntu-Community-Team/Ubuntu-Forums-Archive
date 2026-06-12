---
title: "Problems with Samba and sharing printers"
date: 2006-02-19
forum: Desktop Environments
---

### Post by Xzallion on 2006-02-19
Ok, I just talked my parents into letting me install Ubuntu Breezy on our family computer instead of leaving an *extremely* slow Windows XP OS on here. :D   But after I got it installed, I now have to share our family printer that is hooked up to the family computer with two other computers.

I searched with google and searched the forums but didn't turn up much, and what I did try ruined my /etc/samba/smb.conf file, and I may have messed up another thing dealing with CUPS (I think it was cups.conf or something)  I can't back track to the web pages and can't remember what I changed, and didn't back up the smb.conf file before I started messing with it.  I now realize how stupid that was. ](*,) 

So I need to fix samba, and possibly cups, and then I need to share the printer from a Ubuntu breezy computer to a WinXP/Ubuntu Dual boot computer (mine), and a Win XP laptop over our lan.  The printer is a HP Deskjet 672C.  Printing still works from the family computer (The computer the printer is hooked up to).

Any help would be greatly appreciated.

:idea:  (Just a thought, Would uninstalling and re-installing samba and cups replace the  .conf files with default .conf files? That would help me start over again.)

---

### Post by bscbrit on 2006-02-19
If you uninstall using the 'remove all' option in synaptic (or something like that!) it will remove all configuration files.  A new install should set you up again.

---

### Post by Xzallion on 2006-02-19
Thanks, I will try that and post what happens here soon.  ^_^

Just finished it, and it fixed my /etc/samba/smb.conf file.  Thanks!  Now to the second problem, how can I share a printer on ubuntu, with a windows XP laptop and a dualboot win XP/Ubuntu computer?

---

### Post by skirkpatrick on 2006-02-19
The best way is through Cups, not Samba for XP (XP gets better responsiveness from a Cups printer than a Samba, Win98 is the opposite, at least in my house).  Open your cups.conf file and find the line that says "#Port 631" and remove the # at the beginning.  Restart the Cups service (easy way is through System->Administration->Services).  Now if your other machines already have the printer driver loaded, all you have to do is create a new printer on them.  You want to tell the wizard it's an Internet printer and the URL is going to be "http://machine:631/printers/printer_name" where "machine" is either the IP of your Ubuntu box with the printer or the name of the box.  "printer_name" is the name of the printer in Ubuntu.

---

### Post by Xzallion on 2006-02-19
[QUOTE=skirkpatrick]You want to tell the wizard it's an Internet printer and the URL is going to be "http://machine:631/printers/printer_name" where "machine" is either the IP of your Ubuntu box with the printer or the name of the box. "printer_name" is the name of the printer in Ubuntu.[/QUOTE]

Okay, that sounds like it would work perfectly, but wouldn't the ubuntu machine need a static IP for that to work?  Currently all the computers on my LAN are hooked to a Linksys BEFSR41 router and it is working a DHCP thing.  So all the computers IP addresses change.  I can fix this I just want to make sure I should set static IP's for all the computers before I do.  Or if just the machine name works, where would I look to find the machine name, because I think I forgot what I named it when I installed Ubuntu.

---

### Post by skirkpatrick on 2006-02-19
Well, my Ubuntu box has a static IP but all the machines in the house, including XP machines, refer to it as "PapaBear".  I didn't modify their lmhosts file, either.

Go to System->Administration->Networking.  Go to the General tab and look at Hostname.

---

### Post by Xzallion on 2006-02-19
Cool, I will try that here soon, though my weekend is about over so I may not get a chance to implement it till next weekend.  Thanks for all your help!

---

