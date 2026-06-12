---
title: "Crazy Mirrored Printing in Samba"
date: 2009-05-31
forum: General Help
---

### Post by Phatfingers on 2009-05-31
I installed Ubuntu 9.0.4 yesterday on a newly formatted drive.  I can print directly to my printer (a Canon MP210) from Linux, and would like to use it as a print server for some Windows laptops on my local LAN.  I installed samba-server, changed smb.conf, and installed the correct driver on my Windows laptop.  The laptop sees the printer when browsing for network printers.  When Windows prints to it, however, the page is an exact mirror of what it should look like.

I followed instructions on [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba) under "Sharing CUPS Printers, Manual Configuration".

Any ideas why I'm getting backwards mirror-writing (and images), and how I can make it print correctly for both local and network printing?

---

### Post by cariboo on 2009-05-31
I've never seen that running samba to share printers, I would suggest it is probably a setting in Windows that is causing the problem.

If you are using cups to share the printer, you don't need samba. I would suggest commenting out the printer section in /etc/samba/smb.conf and see if the problem persists.

Just make sure cups is set to share the printer. See screenshot.

---

### Post by Phatfingers on 2009-06-01
> **cariboo907 said:**
> I've never seen that running samba to share printers, I would suggest it is probably a setting in Windows that is causing the problem.
 
If you are using cups to share the printer, you don't need samba. I would suggest commenting out the printer section in /etc/samba/smb.conf and see if the problem persists.
 
Just make sure cups is set to share the printer. See screenshot.
 
Thanks, Cariboo. I looked through the Canon driver configuration on Windows and found no settings for printing output in mirror mode. I found one in CUPS-- which I understand is handy for things like T-shirt transfers.
 
I disabled Samba printing and enabled cups, as you suggested. There are a littany of problems, such as the driver complaining that it cannot connect and that the print queue needs to be unpaused, but it prints anyhow and produces very normal looking output. I appreciate your guidance-- it's not perfect now, but is at least usable.

---

