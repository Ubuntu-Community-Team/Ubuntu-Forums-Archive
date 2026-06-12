---
title: "Printing from Wine (get &quot;no default printer defined&quot;)"
date: 2007-08-28
forum: Desktop Environments
---

### Post by mvip on 2007-08-28
Hi,
I recently installed 7.04 64-bit on a brand new machine. Everything works fine, and I can do all I need to do, including printing to my printer. However, I cant print from Wine. 
I installed the latest binary for 64-bit from Wines repository, and it runs fine. The problem is when Im trying to print I get "no default printer defined". 

If I intepreted how WIne is supposed to work properly, it should come with CUPS support out-of-box, without any further configuration required.

Could anyone please help me find the solution to this problem. Its all that hold me back from moving an entire organization over to Linux.

---

### Post by seshomaru samma on 2007-08-28
do you want to print from MS office?

anyway try this :
$ regedit
- in HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Print\Printers\[cups_printer_name]
- find the key "Port"
- change it's value to "|kprinter" for kde and "|gtklp" for gnome or an environment with gtk. 


Note that the first character is pipe | symbol.

---

