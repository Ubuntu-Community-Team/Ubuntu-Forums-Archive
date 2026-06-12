---
title: "Transfering mail from Windows to Linux"
date: 2005-09-30
forum: Desktop Environments
---

### Post by Jerrac on 2005-09-30
I have all my email in Thunderbird on Windows. I would like to transfer that mail to thunderbird on Ubuntu. How do I do that?

---

### Post by professor_chaos on 2005-09-30
The structure is the same for mail in thunderbird between M$ and linux versions. For a while I had been using the same path on a fat32 to store and share mail between the two installations. So, you should be able to just copy the folder (Mail) over to your linux partition and then change the local directory path in
 thunderbird->edit->account settings->server settings     
 to the place you move the mail directory to. You may want to check and change the permissions after to move.

---

### Post by Jerrac on 2005-10-01
Yeah! It worked great! :D

---

### Post by sturmdogg on 2006-07-06
Will this method transfer the attachments as well?

---

### Post by Jerrac on 2006-07-06
Yes, it grabs all your mail data. The biggest problem I had when I used it, was changing all the permissions. Good luck!

---

### Post by reh4c on 2007-12-31
> **professor_chaos said:**
> The structure is the same for mail in thunderbird between M$ and linux versions. For a while I had been using the same path on a fat32 to store and share mail between the two installations. So, you should be able to just copy the folder (Mail) over to your linux partition and then change the local directory path in
 thunderbird->edit->account settings->server settings     
 to the place you move the mail directory to. You may want to check and change the permissions after to move.

This method sounds fairly simple...maybe too easy :)  Will it work the same between two computers instead of just transferring between partitions?  Here's what I really need to accomplish:  transfer Outlook 2000 e-mails on WinME to Thunderbird on Ubuntu Linux.  My strategy is to install Thunderbird on WinME, import e-mails from Outlook, and then transfer this mail folder from WinME to Thunderbird on Ubuntu using a portable hard/flash drive (two separate computers).  Does this sound reasonable?  Thanks!

---

### Post by ugm6hr on 2007-12-31
> **reh4c said:**
> Does this sound reasonable?  Thanks!

Yes.  That's what I did (but on WinXP).

---

