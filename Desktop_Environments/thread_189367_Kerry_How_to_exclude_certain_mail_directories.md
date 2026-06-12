---
title: "Kerry: How to exclude certain mail directories"
date: 2006-06-05
forum: Desktop Environments
---

### Post by drx on 2006-06-05
Hi, i am very very happy to see kerry, the beagle frontend, working in KDE. (I tried kat before which was only crashing.)

But how can i prevent it from indexing all my SPAM mail? I have some locally synched IMAP folders in KMail where all the SPAM messages go. They are shown in kerry to rest inside the directory "dimap", but inside there i cannot find any real mail messages.

So where are they?

---

### Post by manubreizh on 2006-06-05
hi,
i'm not sure i've understood your problem, but i can try to help : in kerry you can secify what folder is to ignore in indexing ; when you browse with the window appearing, you canno't find your spam folder (that was my case) , so i've manually specified it : i've used konqueror (with "show the hidden files" option to browse in /home/(username)/.kde/share/apps/kmail/mail/, i've found my folder of spam (which is named "junk") and added /home/(username)/.kde/share/apps/kmail/mail/junk in kerry options (privacy).
i hope i've been explicit, but it's not sure...
hope that help

---

### Post by drx on 2006-06-06
Hi manubreizh, you understood my problem exactly. But i think you are using POP3 accounts?

I did also look inside /home/(username)/.kde/share/apps/kmail/mail/ and /home/(username)/.kde/share/apps/kmail/dimap/ with visible hidden files, but i could not find any folders with messages. I am using "cachedimap" accounts, so the messages are on my harddisk. But where?? There are folders with suspicious names, like

/home/(username)/.kde/share/apps/kmail/dimap/.1209568003.directory/Spam

But there is nothing inside them, only index-files (*.ids) with not more than some kilobytes in size. And i have like 600 megabytes of Spam messages. :)

---

