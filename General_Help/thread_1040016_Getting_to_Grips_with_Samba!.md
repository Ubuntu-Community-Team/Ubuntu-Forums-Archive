---
title: "Getting to Grips with Samba!"
date: 2009-01-15
forum: General Help
---

### Post by ally_uk on 2009-01-15
Hi People I am pretty new to Linux, I have at home two machines, the first being a Windows XP computer. 

The second is a small shuttle PC running Ubuntu. I am on a quest to get to grips with Samba, so far I don't seem to be having any luck whatsoever and there are parts of Samba in which I am failing to understand the basic concepts.

I have Samba installed and the service is running fine I am able to start and restart the service.

( What I am trying to achieve)

I want to learn the basics of Samba, so essentially  to start out with I want to be able to create a folder on the Linux machine called " Files" and I then want to be able to view this view the Windows XP machine.

Can somebody give me a clear example or guide that is straight forward and easy to follow. I bought a book on Samba 3 which hurt my brain lol no clear examples were shown and I had no working Samba config by the end of it.

( Things I am struggling to understand)

I understand that the computers need to be on the same workgroup, 

Do I need to edit the Lmhosts file to add the windows client in?

Users that can access the samba shares...........

If I am logged on the windows machine and I want to view the samba share do I need to have logon credentials on the ubuntu machine? this part confuses the hell out of me lol are the users defined in the smb.config if so how?

Many Thanks for your help

I will follow response instructions and keep you guys updated as to how my Samba adventures are going lol

---

### Post by matey3 on 2009-01-15
I am new too but we have a Samba at work, I know that when you create folders and save files on your network drive in Windows they actually get created on samba /users/username/ folder.

 So I think Samba acts as a Windows Server except its linux.(more secure/flexible)
you can get into the files and folders either way (either thru win or linux) . I mean if you have the right passwords, the regular users only see their own mapped drives on Windows side and may be able to see the samba server in the network neighborhood, but its there and you can have shared folders on it plus printers or whatever.

Oh as far as configurations go, I believe you have to do them on the Samba side, bcs once I tried to change/create something and it would not go thru in Windows, so I think there is a difference between the rights of Administrators in Win and the root (su ) in SMB! You have to do things as root in order to change or configure things like network, user rights etc.
I hope someone with more knowledge explains this better .

---

### Post by HermanAB on 2009-01-15
here you go:[http://aeronetworks.ca/samba-debug-howto.html](http://aeronetworks.ca/samba-debug-howto.html)

cheers,

Herman

---

### Post by ally_uk on 2009-01-16
Are there any decent Noobish guides to Samba? I have read a few books and I have to say I am disapointed they all assume you are some hardcore Linux Sysadmin. There are no clear explanations of how you go from A to B and to get a simple configuration up and running.

A excellent book for a potential writer would be how to Share files with Windows and Linux using Samba for Noobs.

I would buy it!.

I had a go at configuring Samba again last night when I am logged on the Windows Box and I go to view Workgroup computers it says I do not have permissions.

---

### Post by polki@mac.com on 2009-01-16
If I remember correctly you have to have a user on the samba/Linux machine, and that user has to be in smbpasswd.

> sudo smbpasswd -a yourusername

Press ENTER for the old password

---

