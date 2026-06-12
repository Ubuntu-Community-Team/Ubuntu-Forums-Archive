---
title: "adding shortcuts to windows folders on the network"
date: 2006-11-16
forum: Desktop Environments
---

### Post by rkakkar on 2006-11-16
I want to add shortcut links on my dapper desktop to certain windows folders on the network (Samba). how can i do so?

they have an address like smb://<hostname>/folder

---

### Post by ratchetr on 2006-12-23
> **rkakkar said:**
> I want to add shortcut links on my dapper desktop to certain windows folders on the network (Samba). how can i do so?

they have an address like smb://<hostname>/folder

Just spent an hour struggling with the same issue. Worth documenting, even if you've already found the solution.

The usual drag and drop tricks for creating shortcuts don't seem to work with SMB folders or files. They just generate an 'error "Unsupported Operation" while creating a link to smb://<hostname>/folder'

This worked for me: (Ubuntu 6.06)
Right click on Desktop
Select Create Launcher
Change Type field to 'Link'
For URL: smb://<hostname>/folder
Fill in the other fields as you see fit.

---

