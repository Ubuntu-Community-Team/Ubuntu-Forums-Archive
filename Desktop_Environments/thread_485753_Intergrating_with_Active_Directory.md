---
title: "Intergrating with Active Directory"
date: 2007-06-27
forum: Desktop Environments
---

### Post by Soimafreak on 2007-06-27
Hello,

I'm trying to think of a way that will allow a laptop to be connected to a windows AD 2003 network while at work, authenticate against the AD server as well as having the AD server managing the user account.

I must confess I've not looked much into it in the last year, but a solution for getting the user account into AD was to modify that with a third party application, This isn't such a thrilling idea as it is quite an important system that if I apply anything to it I'd rather it came from Microsoft.

I'm hoping that there's something new that I don't know about for that issue...

Password authentication, In the past I have configured kerberos to authenticate against a windows AD server, so i'm not too worried about that, however it was using a local user account but authenticated the password with the server, because of the aforementioned issue. 

The other issue is all of the windows file sharing, I'm assuming I can configure a samba client to pick up on all of these if needed? If anything the File access over the network i'm assuming is the easiest of these issues, although I have never dealt with samba properly.

As you can see I'm hoping to get everything working on Ubuntu (preferably Xubuntu) I was just hoping that someone more knowledgeable could tell me what to expect and possibly any problems with the laptop authenticating while not connected to the network.

Help and advice appreciated!

---

### Post by rivasdiaz on 2007-06-28
Samba 3.0.x will work if your AD is configured in compatibility mode (supporting pre-AD clients). Full support for AD will be included in upcoming 4.0 version, currently in alpha.

Assuming pre-AD compatibility, you can use smbpasswd to change a password, and smbclient/nautilus/konqueror (nautilus and konqueror both have wrappers to use samba client from gui) to access a shared windows folder.

To share a folder to be accessed by windows users you can always use samba server for any windows version.

---

### Post by Soimafreak on 2007-06-28
Cheers for the info on Samba, I'll probably tackle that one first.

The issue with windows is every time you access a share it checks your local user credentials to see if you're allowed in to that folder. Which i'm not sure how that'll all work, but I should really read into all that and deal with the issues if i have them!

Hopefully with all the interoperability things MS have been doing lately they have or wil release one that legitimately matches AD to manage linux user accounts.

---

