---
title: "Evolution Error while Storing folder 'Inbox'.  no such table: mem.Inbox"
date: 2010-07-14
forum: Desktop Environments
---

### Post by Stoneface on 2010-07-14
Just tried to run IMAP in the latest version of Evolution on Ubuntu Maverick Meerkat. Then I got this error```
Error while Storing folder 'Inbox'.
no such table: mem.Inbox
``` after the fetching was supposed to be done. No headers downloaded and only this error? Any idea what to do? Will probably file a bug report as well.

---

### Post by Stoneface on 2010-07-14
Followed the instructions @ [http://www.linuxforums.org/forum/redhat-fedora-linux-help/29064-fc3-evolution-smtp-port-number-change.html](http://www.linuxforums.org/forum/redhat-fedora-linux-help/29064-fc3-evolution-smtp-port-number-change.html) and added the proper ports to IMAP (imap.domain.com:143) and SMTP (smtp.domain.com:25025) as used by that particular web hoster, but not a single header downloaded so far even though it does seem to connect. Why Evolution does not use seperate fields to add ports only <God knows... IMAP service seems to be running as well:```
me@ubuntu:/etc$ cat services | grep imap
imap2		143/tcp		imap		# Interim Mail Access P 2 and 4
imap2		143/udp		imap
imap3		220/tcp				# Interactive Mail Access
imap3		220/udp				# Protocol v3
imaps		993/tcp				# IMAP over SSL
imaps		993/udp
``` And it is running with port 143..

---

### Post by Stoneface on 2010-07-14
Never mind the IMAP issue. With the port change all is peachy now :-). Just had to send one more test email to download it. Why I got the earlier mentioned error is not clear yet though.

---

### Post by warkior on 2010-10-19
I'm experiencing the same problem with random folder names since upgrading to Meerkat.  I'm NOT using imap though.  Just regular old POP3 and smtp.

---

