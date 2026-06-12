---
title: "Printing to Windows share... HELP!:("
date: 2006-06-07
forum: Desktop Environments
---

### Post by Aulden on 2006-06-07
Hi all, 

Here is the story... I'm on Ubuntu at work (YAY!) but I need one thing (so far) for everything to be working. I need to print to a Xerox Phaser 3117 (same driver as 3115 as I understand) which is located on a Windows 2K machine... it's connected by USB. WHAT TO DO?

I've tried everything I could find. I've tried through System - Administration - Printing (I get an icon and all but doesn't print... says it does...)
I've tried setting up through browser on 127.0.0.1:631 ... no success...
What to do? The one thing that doesn't seem to work is when I put a password and username into the printer settings it doesn't save them... So I figure maybe it doesn't print becuase it's getting blocked from the Win2K box.

By the way... I'm inputting that the printer is as 'smb:\\(comp)\(printername)'
can I add username and password to that line somehow or what to do???

Any suggestions would be SUPER!

Thanks, 

Aulden!

---

### Post by Flyn on 2006-06-07
Make sure the printer is shared on the Windows box and that no firewall is blocking Ubuntu from communicating with it.
I assume Samba is set up properly?

---

### Post by Aulden on 2006-06-07
Thanks!

The printer is shared and currently about 3-4 other people using it (through windows).

I can access all the computers on the network and their shared folders... and when I setup the printer it finds the computer and the xerox printer no worries... 

I still am troubled that it doesn't save the username and password (which is blank). Cause if it doesn't save it then I guess the printers computer wouldn't let me logon to the printer to use it...

Any more suggestions would make my week!!!:)

Thanks

---

### Post by drtvasudevan on 2006-06-15
me too same printer but no network.
problem in setting up
will be watching this thread hopefully!
tv

---

### Post by Aulden on 2006-06-16
I've been looking into it a bit more. 

I've got it working a little... but only on occasions. 

What I do is before i print I open a terminal and logon to the network printer. 
That is:

smbclient -up //computername/printername --username=(name) --password=(password)

That logs me on to the printer so when I go to print I wont get knocked back on login (as the name and password doesn't save in printer settings)

This usally works but last few times hasn't been consistant. Maybe I'm writting the command above wrong sometime.

But please... anyone who can help it would be greatly aprreciated!

Thanks, 

Aulden

---

### Post by mrvw0169 on 2006-06-16
I don't know if this will help you, but I had the same problem... Here's what I did:

At the terminal: sudo foomatic-cleanupdrivers

Then proceed as usual (remove the non-working printer beforehand):
System>Admin>Printing>Add New
Samba Printer with host IP (or name), printer name, your username/pw for the Windows domain
Select driver...

I've tried every other way and it really did not work until I did the cleanup-drivers line...

---

