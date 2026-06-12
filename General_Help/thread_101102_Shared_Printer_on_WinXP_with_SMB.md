---
title: "Shared Printer on WinXP with SMB"
date: 2005-12-09
forum: General Help
---

### Post by thepisu on 2005-12-09
Hello, I've installed Ubuntu 5.10 on my office LAN. I have a HP laserjet printer on another computer with Windows XP Home, and it is shared correctly with other Windows XP computer. 
On Ubuntu, I cannot print; I can find and install the printer, but when I try to print, nothing happens, logging this error: NT_STATUS_ACCESS_DENIED. 
I tried to access with smbclient on that PC, I can correctly read file shared directories, and I see the printer shared. I tried using different user names (admin of that PC, Guest, nothing...) but I cannot print.

Any ideas?
Thanks!
Stefano

---

### Post by lakerssuperman on 2006-01-28
I had the same error.  I played around with the printer permissions in windows and now it will put the document in the windows queue from my ubuntu machine.  But it sticks at 64kb in the queue and stays there.  I had printing working between my ubuntu and windows machines till the windows machine died and i had to redo it.  now printing to it is a pain.  On a side note, hooking the print up to the ubuntu box will let the windows machine print to it, i just cant use that setup in my house, rrrr.

---

### Post by drakeoutlaw on 2006-02-08
Same problem as above. Will enabling Unix print services in XP help?
--
S.S.

---

