---
title: "Evolution Wont Send Email!"
date: 2005-10-17
forum: Desktop Environments
---

### Post by Mosey on 2005-10-17
Hey,

I just setup an account with the Evolution Mail Client. Whenever I attempt to send an email using said client I recieve this error message:
[I]
"Error while performing operation.

RCPT TO <johnck@lycos.com> failed: Transaction failed"[/I]


I searched the "help" files, but found nothing pertaining to my specific situation.

I also recieve another new error message when looking for updates in the software updates program:

W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

Any ideas how to fix this?

Thanks in advance for any help.

---

### Post by Zotova on 2005-10-17
Are you trying to send your mail via smtp or via the sendmail function?

I tried sending an email via sendmail earlier today and got an error. I then found out sendmail for some reason doesn't seem to be installed by default. Opening up synaptic and installing sendmail fixed the problem.

---

### Post by Mosey on 2005-10-17
I tweaked around a bit and eventually got it working. The server I was attempting to access required authentication.

Thanks though.

---

### Post by davidvolmut on 2005-12-15
I am having the same issue. I get Error while performing operation. The email server I have does not require authentication. I have shut the program down and reopened it. I have tried to send test messages. They never go out, they just stay in my Outbox. I keep getting this error. Anyway to look and see why it is failing?
:(

---

### Post by dcstar on 2005-12-15
[QUOTE=davidvolmut]I am having the same issue. I get Error while performing operation. The email server I have does not require authentication. I have shut the program down and reopened it. I have tried to send test messages. They never go out, they just stay in my Outbox. I keep getting this error. Anyway to look and see why it is failing?
:([/QUOTE]
If the Evolution server software has locked up somehow, shutting down the client won't fix it.

You may have to reboot.

---

