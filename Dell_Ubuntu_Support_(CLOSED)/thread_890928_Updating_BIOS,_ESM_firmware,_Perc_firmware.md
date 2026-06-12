---
title: "Updating BIOS, ESM firmware, Perc firmware"
date: 2008-08-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by inphektion on 2008-08-15
First for the BIOS:
All of my 1950 servers show:
```

Libsmbios: 0.13.10
System ID: 0x01B3
Product Name: PowerEdge 1950
BIOS Version: 2.2.6
Vendor: Dell Inc.
Is Dell: 1

```
yet running update_firmware shows:
```

Running system inventory...

Searching storage directory for available BIOS updates...
Checking System BIOS for PowerEdge 1950 - 2.2.6
  Did not find a newer package to install that meets all installation checks.

This system does not appear to have any updates available.
No action necessary.

```
However Bios 2.3.1 is there:

[http://linux.dell.com/repo/software/bios-hdrs/system_bios_ven_0x1028_dev_0x01b3_version_2.3.1](http://linux.dell.com/repo/software/bios-hdrs/system_bios_ven_0x1028_dev_0x01b3_version_2.3.1)

Any idea why it tells me no update?  and how do we update ESM or Perc firmware?
I see OMSA software for redhat and suse type systems but is there no way to do it in ubuntu?

thanks for any help or pointers.

---

### Post by anjilslaire on 2008-08-16
Unless you have a Dell repository added, you probably wouldn't see a manufacturer update for the bios

---

### Post by inphektion on 2008-08-16
I followed this:
[http://direct2dell.com/one2one/archive/2007/12/05/37446.aspx](http://direct2dell.com/one2one/archive/2007/12/05/37446.aspx)
am i missing something?

---

### Post by inphektion on 2008-08-18
anyone have suggestions?

---

### Post by Diggs808 on 2008-08-21
[FONT=Arial][SIZE=2]You can flash the Bios this way:

[/SIZE][/FONT]   	 	 	 	 	 	  
[LIST=1]
[*][FONT=Arial][SIZE=2]Install 	from Synaptic:  libsmsbios-bin[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]In 	Terminal type: sudo getSystemId [/SIZE][/FONT] 	
[*][FONT=Arial][SIZE=2]Make 	a note of your System ID.  It should look similar to (0x01BD)[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]Go 	to [http://linux.dell.com/repo/software/bios-hdrs/](http://linux.dell.com/repo/software/bios-hdrs/) 	and download bios.hdr from the matching folder.  [/SIZE][/FONT] 	
[*][FONT=Arial][SIZE=2]In 	terminal type: sudo modprobe dell_rbu[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]In 	terminal, navigate to the folder that you saved the bios.hdr file 	to.  If you saved the file to your home folder you do not need to 	navigate to the folder.  [/SIZE][/FONT] 	
[*][FONT=Arial][SIZE=2]In 	terminal type:  sudo dellBiosUpdate -u -f ./bios.hdr[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]This 	will install the bios.hdr file [/SIZE][/FONT] 	
[*][FONT=Arial][SIZE=2]Reboot. 	 During the reboot the screen will flash white, flash the bios and 	then continue to boot up.  [/SIZE][/FONT]
[/LIST]
[FONT=Arial][SIZE=2]
[/SIZE][/FONT]

---

### Post by inphektion on 2008-08-21
> **Diggs808 said:**
> [FONT=Arial][SIZE=2]You can flash the Bios this way:

[/SIZE][/FONT]   	 	 	 	 	 	  
[LIST=1]
[*][FONT=Arial][SIZE=2]Install 	from Synaptic:  libsmsbios-bin[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]In 	Terminal type: sudo getSystemId [/SIZE][/FONT] 	
[*][FONT=Arial][SIZE=2]Make 	a note of your System ID.  It should look similar to (0x01BD)[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]Go 	to [http://linux.dell.com/repo/software/bios-hdrs/](http://linux.dell.com/repo/software/bios-hdrs/) 	and download bios.hdr from the matching folder.  [/SIZE][/FONT] 	
[*][FONT=Arial][SIZE=2]In 	terminal type: sudo modprobe dell_rbu[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]In 	terminal, navigate to the folder that you saved the bios.hdr file 	to.  If you saved the file to your home folder you do not need to 	navigate to the folder.  [/SIZE][/FONT] 	
[*][FONT=Arial][SIZE=2]In 	terminal type:  sudo dellBiosUpdate -u -f ./bios.hdr[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]This 	will install the bios.hdr file [/SIZE][/FONT] 	
[*][FONT=Arial][SIZE=2]Reboot. 	 During the reboot the screen will flash white, flash the bios and 	then continue to boot up.  [/SIZE][/FONT]
[/LIST]
[FONT=Arial][SIZE=2]
[/SIZE][/FONT]
Thanks I actually have done that.  I was just wondering why it wouldn't pick it up automatically.  
And then since it isn't, sometimes a new bios might want a certain rev of the ESM firmware or PERC firmware which I currently have no clue how to update from ubuntu/debian.  Not sure if it's even possible.

---

### Post by Diggs808 on 2008-08-21
I think that it may be possible.  You might try this if you haven't already.....

[http://ubuntuforums.org/showthread.php?p=5633381#post5633381](http://ubuntuforums.org/showthread.php?p=5633381#post5633381)

I know that its for a laptop but it may work for your server too....

Silly me...I just read your post.  I tried the most recent auto update as well and it didn't find it either.

---

### Post by inphektion on 2008-08-30
so.... if you install ubuntu server on a dell that means the perc and esm firmware are now in a time capsule...

---

### Post by rossiFan on 2010-02-05
Actually, you need to download P4FW351S-A09.exe from Dell, create the boot floppies and update the BIOS that way.

---

