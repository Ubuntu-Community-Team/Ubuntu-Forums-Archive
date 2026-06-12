---
title: "Sharing an NTFS partition with another Ubuntu computer"
date: 2010-05-20
forum: Desktop Environments
---

### Post by Heathicus on 2010-05-20
I'm trying to make the switch from Windows to Ubuntu throughout my whole house (2 desktops and a laptop).  I already have a headless file server that has been running Ubuntu for a couple years (I haven't messed with it since initially setting it up other than to reboot it a couple times).  With 10.04, I feel we're ready to make the switch.

The transition is going well but I have one sharing issue I can't seem to fix.  On my desktop (Ubuntu 10.04), I have a Win7 NTFS partition, a Ubuntu Ext3 partition, and a "Data" NTFS partition to be shared between them.  I set it up this way just as a failsafe just in case I NEEDED Windows and a VM wouldn't cut it.

I have used the Ubuntu GUI to share a folder in my "Data" partition.  I right-clicked the folder, chose "Sharing Options", checked "Share this folder", and gave it a name.  

From my son's desktop (Ubuntu 10.04), by going to Places then Network then my computer name, I can see the share that I set up.  But trying to open that share results in the error message "**Unable to mount location.  Failed to mount Windows share.**"  I created a user account on my computer to match his username/password on his computer.  I went back to the Folder Sharing dialog and checked both "Allow others to create and delete files in this folder" and "Guest access (for people without a user account)" but that didn't change anything.  I right-clicked the folder, chose Properties, and went to the Permissions tab, but I'm unable to actually change anything there.  

Having set up my file server a couple years ago, I'm somewhat familiar with samba and the terminal commands for editing it and such.  But, I want to avoid that if possible.  Although I'm not intimidated by the command line, other members of my family are.  And if this transition is going to be a smooth one, then we should be able to do everything in the GUI just like with Windows.  I don't need the command line to set up a share in Windows.  I shouldn't need a command line to set up a share in Linux - especially when all of the computers involved are running the same version of Linux.

So, what is my next step to give the other Ubuntu computers on my home network access to my shared folder?

---

### Post by pricetech on 2010-05-20
This may not help in your case, but have you run smbpasswd on your desktop ??

---

### Post by 3Miro on 2010-05-20
This can be due to either a problem with Samba settings in general or Samba settings specifically for NTFS.

Try sharing an ext3 folder just for a test.

If it is a general Samba setting, it will be fixable. However, the problem may be due to mismatch on NTFS vs Linux permissions.

---

### Post by Heathicus on 2010-05-22
Thanks for the help, ya'll.  Sorry for taking so long to respond.  You know how life gets sometimes.

> **pricetech said:**
> This may not help in your case, but have you  run smbpasswd on your desktop ??

I didn't run the "smbpasswd" command, but I created a user account for my son in the GUI.

> **3Miro said:**
> This can be due to either a problem with Samba settings in general or Samba settings specifically for NTFS.

Try sharing an ext3 folder just for a test.

If it is a general Samba setting, it will be fixable. However, the problem may be due to mismatch on NTFS vs Linux permissions.

I shared a folder on the ext3 folder as you suggested and my son CAN access it from his computer.  So what do I look at next?  Samba settings?  NTFS permissions?

---

### Post by hoare on 2010-05-29
i am havening the exact same problem.
does someone have an idea?

---

### Post by Bucky Ball on 2010-05-29
Have you created a mount point on the client?

---

