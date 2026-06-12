---
title: "Thunderbird: Importing mbox."
date: 2013-03-16
forum: Desktop Environments
---

### Post by XEtedBear on 2013-03-16
In Thunderbird I'm trying to import mbox files that I have exported from Evolution. I use Tools->Import->Mail and am presented with a blank dialog box and the prompt "please select the type of file you would like to import". There is nothing to select and nothing can be entered. The only options are <Back> or <Cancel> which makes it a very quick, but not very effective, import tool.

Has anybody got a more practical way of importing mbox files into Thunderbird?

---

### Post by schragge on 2013-03-16
See [http://kb.mozillazine.org/Importing_and_exporting_your_mail](http://kb.mozillazine.org/Importing_and_exporting_your_mail)
Basically, you need [ImportExportTools](http://www.nic-nac-project.de/~kaosmos/mboximport-en.html) extension.

---

### Post by XEtedBear on 2013-03-16
> **schragge said:**
> See [http://kb.mozillazine.org/Importing_and_exporting_your_mail](http://kb.mozillazine.org/Importing_and_exporting_your_mail)
Basically, you need [ImportExportTools](http://www.nic-nac-project.de/~kaosmos/mboximport-en.html) extension.

Yep, that's what I thought too; it makes no detectable difference.

---

### Post by schragge on 2013-03-16
Have you got the new menu entry *ImportExportTools* on your Tools menu after installing the extension?

---

### Post by XEtedBear on 2013-03-17
> **schragge said:**
> Have you got the new menu entry *ImportExportTools* on your Tools menu after installing the extension?

Yes. However, you make a good point - I hadn't noticed the new option "importexporttools" in the tools menu - I still used the simple "import" option. Having tried the new option I get this inscrutable error message: 

"impossible to import in this folder (imap or newsgroup type)"

Is this telling me I can't import in IMAP mode?

---

### Post by XEtedBear on 2013-03-17
OK, I think this is solved now; see: 
[https://freeshell.de/~kaosmos/mboximport-en.html](https://freeshell.de/~kaosmos/mboximport-en.html)

It's clear that the ImportExportTools does not support import for IMAP Accounts. Perhaps it should be renamed to "can'timportexporttool"

I'll start a new thread asking if there is any way to import mbox files into a TB imap account.

---

### Post by schragge on 2013-03-18
There are some command-line tools that synchronize local MailDir folders with remote IMAP folders like [mbsync](http://manpages.ubuntu.com/manpages.gz/precise/man1/mbsync.1.gz) from the package *isync*, or [offlineimap](http://manpages.ubuntu.com/manpages/precise/en/man1/offlineimap.1.html), but you will need to convert your mbox files to MailDir format first, e.g. with [mb2md](http://manpages.ubuntu.com/manpages/precise/en/man1/mb2md.1.html).

---

### Post by XEtedBear on 2013-03-18
Aha! That's very useful to know; thanks. I'm converting from Evolution, which uses (in its current version) the MailDir format (or so I'm told). It remains to be seen what doesn't work this this process; I note with some misgiving your reference to 'local MaiDir folders': this modifier 'local' has always confused me; anything that I can walk to, without having to stop for lunch somehwre, is 'local' to me  - that's what the word means. So all my folders are local, if not closer. Clearly this is a naive view to take when discussing the labels applied by those who are respected for their coding skills, rather than their etymological skills

---

### Post by schragge on 2013-03-18
Here *local* basically means "physically located on your computer, and not on some remote IMAP server". With some reservations, naturally. E.g. a mail folder on the network share in your LAN is still *local* from the mail system POV. OTOH, any mail folders on the IMAP server are *remote* even if that server is located in the same room as you.

---

