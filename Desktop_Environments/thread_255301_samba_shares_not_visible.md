---
title: "samba shares not visible"
date: 2006-09-11
forum: Desktop Environments
---

### Post by Lary Grant on 2006-09-11
I have 2 Dapper machines connected to the same router, using dynamic IP.  On the 1st machine, I'm sharing a directory.  On the 2nd machine, if I use Places -> Connect To, I can connect to the share on the 1st machine by IP address and share name.  Copying in both directions works fine.  So this shows that Samba is basically working.  However, I can't get it to connect in the "normal" way, where I can navigate through "Windows network" to the machine name and then to the share.  If I get on the 2nd machine and click on Network -> Windows network, I *can* see the name of the 2nd machine, but when I click on it, I don't see any shares.  I really would like to get Samba totally working, because once I do, I'll put my old Windows machine back on the network and use Samba to transfer all my files from the Windows machine to my Ubuntu machine, then I can finally retire the old Windows machine.

---

### Post by kidders on 2006-09-11
Hi there,

How much do you know about samba? As in, have you checked the following:

[LIST]
[*]Are you waiting long enough for your windows network to refresh itself before going looking for shares?
[*]Are all your PCs on the same workgroup/domain?
[*]Are the results of your election processes sensible?
[*]Are you explicitly hiding shares in your smb.conf?
[/LIST]

Does any of this make any sense?

---

### Post by Lary Grant on 2006-09-11
I don't know much about Samba.  I have not edited any config files... I set up everything from the Gnome/Metacity interface.  The workgroup for both machines is the default (MSHOME).  I should clarify that I don't currently have any Windows machines on the network... just 2 Dapper machines.  I'm sure I've waited long enough... I set up the share weeks ago.  I don't know what an election process is.  As for hiding shares, I haven't edited the smb.conf, so I don't think I've hidden anything.

---

### Post by kidders on 2006-09-11
Hmmm... let's start with the simple things...

Your problem *might* be that your shares are not "browsable". It's possible for instance that you need to authenticate with the server before it lets you see a full list of shares. One way to check would be to set up a dummy one -- but turn off all the access control. Make it completely public, and see if it shows up. Using this kind of authentication-dependent sharing is quite useful sometimes ... say for instance you were sharing users' homes over samba... the shares you'd display would depend on who was asking.

Windows networks can be a bit fiddly, so you have to be a bit patient sometimes. (I'm sure you know as well as I do that it takes Microsoft a few goes to get things right!)

Incidentally, I assume you're remembering to restart samba when you make changes to shares. (Just in case!)

---

### Post by Lary Grant on 2006-09-11
If I do Edit -> Share Folder in Nautilus on the folder I'm sharing, it already comes up with "Allow browsing folder" checked and "Read only" unchecked.  Under "Share with" it has "SMB" selected.

If I click "General Windows Settings", the "Domain / Workgroup" setting is "MSHOME" and under "WINS server" it says "Do not use WINS Server".

---

### Post by Lary Grant on 2006-09-11
Would it help to post my smb.conf file?

---

### Post by Eggbanjo on 2006-09-11
the 2 apps i found most useful for this were, smb4k and komba2. these helped me locate my shares and mounted them to.

---

### Post by kidders on 2006-09-11
> **Lary Grant said:**
> Would it help to post my smb.conf file?

Yep :-) Just on the off-chance there's something dead obvious wrong with it.

---

### Post by piroshki on 2006-09-11
If you are setting up samba just to retire the Windows machine and you are reasonably confident installing hardware, then it may be easier to plug the windows machines hard disk into the Linux box and read the files straight off it. 

If you then need to share files between the Dapper boxes, NFS could be an easier option to set up.

Just a thought... :)

---

### Post by Lary Grant on 2006-09-12
I thought of the hard disk option, but the problem is that I already have 2 hard drives, a CD, and a DVD in the Ubuntu box.  I would have to take out something else, and if it's a hard drive I take out, then I wouldn't have that available for copying the files.

---

