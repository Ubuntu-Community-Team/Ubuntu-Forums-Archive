---
title: "Open remote files in Quanta"
date: 2006-08-30
forum: Desktop Environments
---

### Post by tminuszero on 2006-08-30
Hi - I'm new to Gnome and Ubuntu (and these forums), but not linux. I just switched my desktop from a straight debian install that I've had for four years. I love Ubuntu so far, but I'm having a problem that's probably easily solved.

In Quanta, I'm trying to open a file on a remote server. I *used* to do this by typing in the location ssh://user@foo.bar.com/path/to/file . However if I try that now, Quanta returns the error "Malformed URL."  I've tried sftp, ssh and fish, and I get the same error.

I did go to Places, Connect To Server, and set it up. I can open the files in Bluefish through this location, but for the life of me I can't figure out how to connect to that Place in Quanta.

I'm sure the fix is easy, or I've just overlooked something obvious in the manual, but I just can't find it. Thanks in advance for the help!

---

### Post by dyoung66 on 2006-08-31
Doesn't look like you're getting an answer so I'll give it a shot....

I'm making a semi-educated guess here, but if you're using quanta in gnome you might not have some of the kde protocols that quanta uses. I know quanta uses some kio slaves to run these protocols.

This is from the Quanta manual:
"Available protocols include SSH, FTP, NFS, SMB, WebDAV, and others. The protocol list is powered by KDE's powerful KIOSlave architecture. This framework allows every KDE application to easily access remote information as if it is local to the machine."

So my guess would be to look at installing kio slaves and running them in gnome. I'm not sure how to do this though, I'm a KDE user myself.(Im a big quanta fan.)
Maybe someone else can expand....?

---

### Post by skymt on 2006-08-31
The kio slaves you want are in the package kdebase-kio-plugins.

---

### Post by tminuszero on 2006-09-05
Thank you guys so much for your help. I *thought* I had my account here set to email me when replies were made, but obviously I hadn't. So I was coming on to share my solution - to install kdebase and kdebase-kio-plugins! :) 

Thanks for your quick replies!

---

