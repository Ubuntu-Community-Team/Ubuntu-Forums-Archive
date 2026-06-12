---
title: "Permissions on HD- how to change?"
date: 2006-07-08
forum: Desktop Environments
---

### Post by master_b on 2006-07-08
I am using Kubuntu Dapper on 2 PCS on my home LAN and have set up Shares on these two pcs.

I can copy files OK from PC1 ( media server) to PC2 ( client) without problems via fish:// and Konqueror. 

I can copy files from PC2 (Client) to PC1 (media server) /home/bill without problems.

My problem is that PC1 also has 2 additional hard drives from which I can copy data, but cannot copy data to.

I have determined that this is due to all directories/files on these drives being owner/group 502, whereas the drives themselves are owner/group "bill", the same as PC1 /home/bill and PC2 /home/bill.

I have tried to change permissions on all directories/files to user/group "bill" using /System Settings/Sharing/File Sharing and using Midnight Commander ( both as root of course) without success.

These 2 drives were previously in the same PC when I was running Kanotix ( prior to the current Ubuntu based beta) and Shares worked then, though obviously users/groups were different.

Advice please on changing group/user permissions.

Thanks

Bill

---

### Post by master_b on 2006-07-09
Anybody?

---

