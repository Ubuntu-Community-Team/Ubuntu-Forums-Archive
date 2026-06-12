---
title: "GVFS + Samba: Upload to share on another Linux machine fails, Share unavailabe"
date: 2009-04-04
forum: General Help
---

### Post by JAlexoid on 2009-04-04
Hi,

    I am having a problem with SMB share. Whenever I try to upload a file to an SMB share it gets stuck. The share becomes unavailable. Not responsive to unmount requests. Logout/Login does, visually, unmount the share, but I cannot remount it. 
    The same happens when the physical connection to the server is lost.
    Downloads work perfectly well. Only uploads do this kind of magic.
    To make the share mountable again, I have to restart my client machine.
    Sometimes, I get a message from either the DBus or something other, stating that the connection has timed out.

     Client is on Jaunty. (Absolutely same problem happens with Intrepid on the client)
     Server is on Hardy. Samba 3.0.28a.

     Who do I bug with this issue? Any ideas?

     And where in hell is the log for these king of operations? Samba server has the log, but does the client?!?!?!?!

---

### Post by cariboo on 2009-04-04
I would suggset trying a different network card on your server. If that doesn't make any difference try the adaptor in your desktop computer.

I had a similar problem on my sever, and a new network adaptor soved the problem.

Jim

---

### Post by JAlexoid on 2009-04-04
The network card is perfectly Ok.
Windows machine also can upload files to that Samaba share, but not the Linux one. This is 100% software issue.

So my question still stands: Who do I bug with this issue? (As in, what project might be responcible for that area? Gnome? Samba? Nautilus?)

---

