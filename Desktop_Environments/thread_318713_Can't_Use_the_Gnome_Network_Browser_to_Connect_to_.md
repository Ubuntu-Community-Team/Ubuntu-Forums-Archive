---
title: "Can't Use the Gnome Network Browser to Connect to SMB Shares"
date: 2006-12-14
forum: Desktop Environments
---

### Post by RAdams on 2006-12-14
Before I installed the optional Samba software, I could use the "Network Servers" item under "Places" and see an item called "Windows Network". When I clicked on that, it used to take me to a list of available windows machines with shared folders. I couldn't connect to these machines, because I didn't have samba installed. Now I do, but when I open "Windows Network", I can no longer see the computers, just an empty windows with "smb://" in the address bar. What's the deal?

I know I can connect to the machines using fstab or even the "mount" command, but I want to connect using the above method, without having to manually type in the computer information. It's a dynamic set of clients, and I'll be translating some of the methods to people who can't (i.e., won't) handle non-point-and-click methods.

---

### Post by RAdams on 2006-12-18
Update: I installed LinNeighborhood, which was also unable to locate the other computers in the Network. Is it possible it can no longer find the other computers? The settings on both ends are still the same, and the network connection is fine... :\

---

### Post by v.ipe.r on 2007-01-25
I have the same problem you do! Cant see nothing in the "Network Servers" item under "Places".

Any suggestions any one?

---

### Post by chipmonk010 on 2007-01-25
guys:

goto system > administration > networking >general tab 

and set domain: to your windows workgroup

that should solve your problem


EDIT: also goto system > administration > shared folders >general properties tab 

set the correct workgroup here also

---

