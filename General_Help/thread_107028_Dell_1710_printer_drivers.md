---
title: "Dell 1710 printer drivers"
date: 2005-12-22
forum: General Help
---

### Post by tieflingrogue on 2005-12-22
I just received at dell 1710 laser printer.  I've been using the Printing GUI under System/Administration.  The printer is not listed under dell drivers.  Couldn't find much googling.  Tried the Samsung 1710 gdi driver, but that didn't work at all. Any help would be greatly appreciated.

---

### Post by OKIHost on 2006-01-28
I am in the same position as you, Dell says it has 'Linux' support but there are only Debian and Redhat drivers on the CD.

On the phone with Dell Helpless Support now about 30 minutes into the call, first 15 was explaining I am not running XP :twisted:

---

### Post by OKIHost on 2006-01-28
Nope still no luck, There is a .plugin file also on the CD along with Debian and Redhat drivers but I have no clue how one would even try to use it.

Dells support is even worse than I had remembered, I was just told to call on Monday and speak with sales because 'They might have some drivers we don't' <sigh>

If you have any luck please let me know, I have tried the 1710 drivers because someone said it looks like like it which it does but no luck, I can get a test page to go but junk on all other pages.

---

### Post by OKIHost on 2006-01-28
I did manage to get the Debian drivers installed but when adding the printer in the dell print driver manager it just always fails :(

---

### Post by Dr. E on 2006-03-06
I have found, at least on another distro, that if you choose a generic laser printer driver you can get the Dell 1710 to work.

---

### Post by Alexander Kirillov on 2006-05-10
[QUOTE=Dr. E]I have found, at least on another distro, that if you choose a generic laser printer driver you can get the Dell 1710 to work.[/QUOTE]
In Dapper, selectin "generic PCl 6/XL" printer works, though not all features are avilable.

---

### Post by Alexander Kirillov on 2006-05-10
I found that ESP Print Pro (commercial printing system by the same company that gave us CUPS) has drivers for this printer. After downloading the trial verison of this software, unpacking it, etc I found the ppd file, which I am going to try later. Since the copyright notice syas that distributing this file is fine as long as copyright notice is attached, I am attaching this file here for the benefit of other users.

---

### Post by dvdp37 on 2006-09-18
Thanks this driver worked for me for a Dell 1710n laser printer used mostly for Windows users.
I did a self test page on the printer to get its settings
Printer Type 
. Network Printer : Unix Printer (LPD)
Host: = IP address 
Queue: = Hostname

---

### Post by FoxMan1982 on 2006-09-30
For the Dell 1710 you'll have to use the Generic PCL 6 driver, because for the ppd file your printer needs postscript support. And (unfortunately) the 1710 doesn't have postscript support, the ppd file will work for the Dell 1710n, this printer does support postscript.

By the way, the ppd file can also be extracted from the windows drivers. If you look on the CD in the english section of the Windows XP drivers section, you'll find two file with the extention .PP_. If you run the extract command on these two files you have two ppd files for the Dell 1710n

---

### Post by sk8dork on 2007-01-24
i have a dell 1710n connected to the network here at work. i'm not sure what 'run the extract command' means, but i have the printer installed my win xp notebook so i searched for *.ppd and found the one file that matches the .pp_ from the cd. the file was called DKAAY1P2.PPD. i copied that to my ubuntu box and did the add new printer wizard, CUPS. i picked network printer,cups, entered the IP of the printer (ipp://10.10.1.1), when selecting the printer driver i clicked the install button and navigated to the copied .ppd file, chose the first choice (Laser Printer 1710n PS3) and it works fine. someone said something about the non-network version of this printer doesn't support PS so i don't know if this helps those with that version (1710).

---

### Post by javathehot on 2007-05-25
Dell 1710n (network version with PostScript support) works just fine with the DKAAY1P2.PPD file, configured with CUPS.
Now, in order to get the DKAAY1P2.PPD file you have to expand the DKAAY1P2.PP_ file (that's what 'run the extract command' would mean). So, on a WinXP box, fire the DOS console, go to the DKAAY1P2.PP_ directory and execute this:
```

   expand DKAAY1P2.PP_ DKAAY1P2.PPD

```
Then you should have a message notifying that the file is exploded or something.
Transfer the DKAAY1P2.PPD to your Ubuntu box. Use the Administrator > Printing option or the CUPS web interface at [http://localhost:631/](http://localhost:631/)
That's it.

---

### Post by ramjet_1953 on 2007-05-26
Follow this link, it should help:

[http://www.linuxprinting.org/show_printer.cgi?recnum=Dell-1710](http://www.linuxprinting.org/show_printer.cgi?recnum=Dell-1710)

Regards,
Roger :cool:

---

### Post by Cerny on 2007-06-23
when you install the dell 1710 you have to use an HP driver, the HPIJS driver, the best printer i found was the LaserJet 4 driver. It worked out perfectly when i ran the test.

---

