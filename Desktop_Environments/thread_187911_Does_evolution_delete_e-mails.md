---
title: "Does evolution delete e-mails?"
date: 2006-06-03
forum: Desktop Environments
---

### Post by yaauu on 2006-06-03
Hi all!

After using evolution for a more than a year, it started going pretty slow. I saw that having folders in Inbox instead of in "En este equipo" in spanish (I guess that "In this PC" or sth like that, the root of all folders) made it slower, so I moved all folders there, and I also created a new folder "old" with all the e-mails from my Inbox except for the ones from the last month, so I could have "fast" access to my Inbox.

The problem is that it does not really delete the e-mails. I mean, the "Inbox" file in my ~/.evolution/mail/local/Inbox has still over 700 MB.

So, I started testing, and found that, if I create a new folder (say 'AAA'), and copy or move an e-mail to that folder (say an e-mail with subject 'Hello!'), it works. 

If I delete that e-mail or I move it somewhere else, in Evolution it doesn't appear again (or it appears wherever I have moved it), so it seems that the e-mail has been deleted.

But, if I check:

$ cat ~/.evolution/mail/local/AAA

The folder still has the e-mail. If I copy an e-mail, I delete it, I copy it again there, I delete it again, and I check, the e-mail is twice, so it's not some kind of feature like "it reserves that space so that following e-mails are copied into that space" or anything like that.

I thought that maybe closing evolution and opening again would "save to disk" or something like that, but even killing the daemons of evolution, the e-mails is still there.

Can anybody else try it to check it? Does anybody know if there is a reason for this?

Thanks in advance

---

### Post by yaauu on 2006-06-03
BTW, I could create an empty folder (ie. Folder1), copy e-mails to Folder1, create another empty folder (Folder2), copy ~/.evolution/mail/local/Folder2{,.cmeta,.ibex.index,.ibex.index.data} to ~/.evolution/mail/local/Inbox{,.cmeta,.ibex.index,.ibex.index.data}, move back the e-mails from Folder1 to Inbox and delete both Folder1 and 2. (Well, while I write this I guess copying Folder1{...} to Inbox would have been enough but...).

I mean, I don't really have a problem like "I need help urgently, this doesn't work", I'm just wondering if there is any way to avoid this behavour from evolution.

Thanks in advance (again)

---

### Post by MichaëlVD on 2006-06-03
You need to "purge" the folders to really delete the e-mails rather than just hide them. In the english version, this is done with Folder/Expunge

---

### Post by yaauu on 2006-06-03
:o thank you! yeah... I should have checked the folder menu...

---

