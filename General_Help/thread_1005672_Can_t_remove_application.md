---
title: "Can t remove application"
date: 2008-12-08
forum: General Help
---

### Post by bigrev on 2008-12-08
Hi

When I try to remove an application using the applications manager, a message appears saying 

"Failed to run /usr/sbin/synaptic '--hide-main-window' '--non-interactive' '-o' 'Synaptic::closeZvt=true' '--parent-window-id' '58720259' '--set-selections-file' '/tmp/tmpx-caDG' as user root.

Unable to copy the user's Xauthorization file."

I tried googling it with no sucess. This is worrying me a bit, can someone help me please?


EDIT: It started working again. I followed one of the answers I found in google, it was very simply that the hard drive was full (I had been making some backups to it). I deleted those backups, restarted, and it started working again. I am not sure if that was the reason for it to start working again though.

---

### Post by dragos_iliescu_2005 on 2008-12-08
Did you were logged on as root?

---

### Post by CrusaderAD on 2008-12-08
Did you try this from the command line?

sudo apt-get remove packagename

---

### Post by CrusaderAD on 2008-12-08
Did you try this from the command line?

sudo apt-get remove packagename

---

### Post by bigrev on 2008-12-08
I didn t, because as I said when I edited my post, everything is fine now. I will try that if I get the error again and report back if it gets corrected with it ;) Thanks!

---

