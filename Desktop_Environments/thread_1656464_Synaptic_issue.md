---
title: "Synaptic issue"
date: 2010-12-30
forum: Desktop Environments
---

### Post by mikeody on 2010-12-30
When I access Synaptic I get the message :

"E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

So I open a terminal and run 'sudo dpkg --configure -a' as requested.

I then get the following in a panel with blue surround :

[I]Package configuration

Configuring grub-pc
The GRUB boot loader was previously installed to a disk that is no
longer present, or whose normally unique identifier has changed for some  reason. It is important to make sure that the installed GRUB stays in   &#9474; 
sync with other components such as grub.cfg or with newer Linux images  &#9474; 
it will have to load, and so you should check again to make sure that   &#9474; 
GRUB is installed to the appropriate boot devices. 
If you're unsure which drive is designated as boot drive by your BIOS,    
it is often a good idea to install GRUB to all of them.
Note: It is possible to install GRUB to partition boot records as well,   and some appropriate partitions are offered here.  However, this forces   GRUB to use the blocklist mechanism, which makes it less reliable, and    therefore is not recommended.                                                                             <Ok>    [/I]  
The Ok is in red but I cannot click it, and cannot get rid of the panel without closing the terminal. If I try to access Synaptic again I am told it is "Unable to get an exclusive lock"

I have updated GRUB but the problem still exists.

All this may stem from the fact that I tried out another Ubuntu OS on the PC by swapping the HD for another empty one. The original hard drive is now back. It all boots OK but I am left with this Synaptic issue.

Can anyone help please ?
Thanks.                             &#9474; 
 &#9474;

---

### Post by mcduck on 2010-12-31
Run the "sudo dpkg --configure -a" command, and once in the confirmation screen use the Tab key to highlight the OK button and press Enter.

---

### Post by Krytarik on 2011-01-01
Detailed instructions, also try the "debconf"-option: [http://ubuntuforums.org/showthread.php?p=10285505](http://ubuntuforums.org/showthread.php?p=10285505)

---

### Post by mikeody on 2011-01-02
Thanks guys,
Followed the first suggested option which worked OK.
Thanks again.

---

