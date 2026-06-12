---
title: "samba with ubuntu client = user permissions incorrect"
date: 2009-07-28
forum: Desktop Environments
---

### Post by larry007 on 2009-07-28
Hi all,

This is something I haven't yet seen, and can't find a solution to either. I have a samba server running in an mixed environment with a few users for over a year and all is working great!

However, I had to rebuilt my Ubuntu PC last week (I think ext4 on / wasn't a great idea...) and now have the following problem:

On my new Ubuntu install, UserA access his remote SMB share with his own SMB creds which are the same as his local account.  But the file/folder permissions points the owner to be UserB.  On the samba server though, the files belong to the correct owners, and all is fine from a Windows box. The same applies to UserB's files belong to UserC, etc.  

I checked mounting the shares with CIFS and SAMBA, but with the same result.  I also rebooted both boxes.

Thus I am let to believe that somehow UserIDs are somehow screwing around on the new Ubuntu install, however weird that may be, as the very same version of Ubuntu 904 was running just fine last week.

I would gladly provide log/conf files if required, as I would really like to get this resolved asap.

---

### Post by larry007 on 2009-08-06
any takers, or samba experts out there?

I'll appreciate your assistance, even pointers....

---

### Post by brianread on 2009-10-19
this is mentioned in:

[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

but gives no solution other than retaining the earlier packages (and I am not sure what or how this can be done).

I am very keen to get this working also.  I notice your last posting was August, did you find a solution?

<edit later> Actually i had some paths wrong in my fstab entry, and it is now working, so anyone reading this - the answer is defiantly in the excellent help doc linked to above...

---

### Post by Roasted on 2009-10-20
Hmm... Let's see your smb.conf. 

sudo gedit /etc/samba/smb.conf - paste here.

Also, tell me more about your setup.

Where are your shares located? 
What are the permissions on your shares?
What are the ownership of the shares?
What samba users do you have on your system?
What ubuntu users do you have on your system?

I'm not too sure I understand where you're coming from with your issue just yet, however if you provide the following info, perhaps an inconsistency can be found and figured out.

---

