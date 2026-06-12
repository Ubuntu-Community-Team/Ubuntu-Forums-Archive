---
title: "Save/Load Thunderbird e-mails?"
date: 2005-08-28
forum: Desktop Environments
---

### Post by veraction on 2005-08-28
Ok, so I had a bunch of emails in my "Local Folders" which I wanted to backup before I reformatted my drives. I copied every thunderbird folder I could find:

[list]
[*]/home/username/.mozilla-thunderbird
[*]/home/username/.thunderbird
[*]/usr/share/mozilla-thunderbird
[/list] 

Then after fresh install of Ubuntu, I installed thunderbird via apt-get then put these folders from their backup location to where they were originally.

It seemed to load my settings for connecting to my email server fine, however the archived messages are no longer showing up under "Local Folders." Any advice?

---

### Post by scoon on 2005-08-28
Hey there, 


From here:  [http://www.mozilla.org/support/thunderbird/faq#q2.10](http://www.mozilla.org/support/thunderbird/faq#q2.10) 

```

How do I export e-mail messages to another mail program or computer?

    Thunderbird's mail files are in the standard plain text "mbox" format, which almost all mail programs can use or import. Many proprietary mail programs have a function to import from Eudora, which also uses the "mbox" format; this function should read your Mozilla mail files properly.

    Your mail files are inside your profile (see the Profile Folder), in the Mail and (if you use IMAP) ImapMail folders. Each mail folder (Inbox, Sent, etc.) is stored as two files — one with no extension (e.g. INBOX), which is the mail file itself (in "mbox" format), and one with an .msf extension (e.g. INBOX.msf), which is the index (Mail Summary File) to the mail file. Tell the other program to import mail from the file with no extension.

    If you want to transfer a mail file to another Mozilla profile or another installation of Mozilla, simply put the mail file into the other installation's Mail folder.


```


regards, 

scoon

---

### Post by veraction on 2005-08-29
I'll try that. Though I thought that the "Mail Folder" was included in one of those 3 folders I copied over.

In middle of moving so can't try now

---

### Post by veraction on 2005-08-29
Ok, I fixed it.

In my ~/.mozilla-thunderbird directory, there were two folders:[list]
[*]Archived.sbd
[*]archived.sbd
[/list] 

And a file called "archived."

Previously when I opened thunderbird, it showed a folder named "archived" with no contents. 

I fixed it by deleting archived.sbd folder then renamed "archived" to "Archived"

Don't know why it happened, but it's fixed

---

