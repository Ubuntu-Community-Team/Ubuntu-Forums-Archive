---
title: "Evolution Question"
date: 2006-01-16
forum: Desktop Environments
---

### Post by knichel on 2006-01-16
I am trying to configure Evolution for my email.  I have the following email accounts I need access to...

1)  POP - my own domain (easy to set up in evolution)
2)  IMAP - my email at work (unix server FreeBSD)  Not so easy

I have the POP set up fine, but when I try to set up the IMAP one, I see all of the files and folders in my home directory on the server.  I am used to checking this email account through a shell account.  Microsoft Outlook handles this account fine.  I would like to set up Evolution to handle it as well.  I know I can set Evolution to treat this as a POP account, but then all of the mail from both accounts will show in my inbox and I do not want that.  I prefer to keep them separate.  On my server at work, I have the following files/folders in my home dir...

.mbox
/mail

I think that all mail is delivered to .mbox and when I run pine, it gets sorted into the /mail folders accordingly.

Any suggestions as to how to configure this account in Evolution would be greatly appreciated.

--
Mike

---

### Post by srt4play on 2006-01-16
Well you could set it up as a POP server like you say, and then just create mail filters to keep them separate?

---

### Post by Hereford on 2006-02-01
> Well you could set it up as a POP server like you say, and then just create mail filters to keep them separate?


This seems to be working for me,  I think my ISP discourages POP but I will go with it as long as it works.  I think another advantage (and perhaps why the ISP discourages it is that I can leave messages on the server until I have gained confidence and experience with *Evolution.*

---

### Post by dcstar on 2006-02-01
[QUOTE=knichel]I am trying to configure Evolution for my email.  I have the following email accounts I need access to...

1)  POP - my own domain (easy to set up in evolution)
2)  IMAP - my email at work (unix server FreeBSD)  Not so easy
......
Any suggestions as to how to configure this account in Evolution would be greatly appreciated.

--
Mike[/QUOTE]
Evolution will set up a separate tree for IMAP accounts (although there are some IMAP display issues in the current version).

IMAP is basically as easy to set up in Evolution as POP.

---

