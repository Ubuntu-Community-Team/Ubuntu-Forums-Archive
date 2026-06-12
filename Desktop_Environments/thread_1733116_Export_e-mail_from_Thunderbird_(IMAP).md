---
title: "Export e-mail from Thunderbird (IMAP)"
date: 2011-04-18
forum: Desktop Environments
---

### Post by vatzec on 2011-04-18
I'm trying to export all of my e-mail from an IMAP account. As far as I know, Thunderbird doesn't provide any explicit export tools, but it does have a "Save As" option, thanks to which I can select all of the messages in a folder, select "Save As", and save them at one location on a disk. That's awesome, but in reality... for some reason Thunderbird doesn't save some of the messages. And it happens quite often -- at first I thought it mostly happens to e-mail with attachments, but it also happens to messages that are text-only. In addition to that, often future attempts to save the same message also fail -- nothing happens (in other words, if a message hasn't been saved when trying to save a bunch of messages, you can try to save just this one message, which might work (I think), but if an attempt to save that single message has failed, so will any consecutive attempts to save just this one message).

So, here's the question: Do you know how to export e-mail from an IMAP account in Thunderbird? Or do you know why the above happens and do you know a solution to this problem?

Thanks!

---

### Post by vista_convert on 2011-04-18
If you have not deleted the messages on the IMAP account, then you don't need to export them. Just give your new client the log-in particulars and let it download them. 

As to the problem you describe, that could be a problem with Thunderbird's indexes. Try right-clicking and compacting the folder. 

HTH

---

### Post by vatzec on 2011-04-18
> **vista_convert said:**
> If you have not deleted the messages on the IMAP account, then you don't need to export them. Just give your new client the log-in particulars and let it download them.

The point is rather to export the e-mails to have them as files on a local disk, instead of on the IMAP server. I don't want to use that server anymore.


> **vista_convert said:**
> As to the problem you describe, that could be a problem with Thunderbird's indexes. Try right-clicking and compacting the folder.

I have just tried it, and it didn't help. :-(


It seems the filenames are the problem. By default, Thunderbird saves the messages with subjects in the filenames (AFAIR). If I input simple names for the files (which I can only do if I save the files one by one, so it isn't a solution; it'd have to be automated somehow), such as "1.eml", "2.eml" and so on, it works! Do you have any idea how to rename saved files on-the-fly? Is there any extension that does that?

---

### Post by vatzec on 2011-04-20
I've found a program called "OfflineIMAP" to be a good solution. :-) Thanks!

---

