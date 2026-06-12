---
title: "lftp vs. sftp vs. ftp?"
date: 2008-12-09
forum: General Help
---

### Post by moore.bryan on 2008-12-09
although i know what all three are, why is one better/worse than another? i've read a handful of articles which say sftp is "more secure" and lftp is "faster" than ftp, but does anyone have any better insight?

and to throw another wrench in the machine, how does ssh fit into all this?

really? no one has any insight?

---

### Post by johnraff on 2009-01-29
Hi Bryan - I expect you've googled your way out of this by now, but I found your post on a similar quest.

Confusion arises because the names of *protocols* and the names of *applications* can be the same.
ftp, sftp, ftps, http, fish ... are protocols
but
ftp, sftp, lftp, psftp, ... are commands which can call up applications.

I'm trying to improve my ftp upload script and have been playing with a few apps over the last few days, but lftp seems to have the most complete set of options and is the one the most people seem to recommend. ncftp is another, I also tried wput, ftp-upload, sftp, psftp, ncftpput, but I think lftp is the one.

ftp vs sftp protocols: sftp uses ssh to send data securely.
ssh: you'd better look this one up.

Good luck!

---

### Post by jms1989 on 2009-01-29
Ok, ssh stands for secure shell.

[quote=wikipedia]
Secure Shell or SSH is a network protocol that allows data to be exchanged using a secure channel between two networked devices. Used primarily on Linux and Unix based systems to access shell accounts, SSH was designed as a replacement for TELNET and other insecure remote shells, which send information, notably passwords, in plaintext, leaving them open for interception. The encryption used by SSH provides confidentiality and integrity of data over an insecure network, such as the Internet.[/quote]

---

### Post by moore.bryan on 2009-02-01
yeah, i found-out most of this stuff through my own research. i've also noticed sftp is _much_ slower for me, with ftp coming next in the speed category, and lftp as the fastest. i tested things out on a wireless g connection on a cable modem using 1gb of files to transfer; sftp took 3 hours-12 minutes, ftp took 57 minutes, and lftp took 16 minutes.

---

### Post by johnraff on 2009-02-02
Still not sure if you're comparing protocols or apps.
"sftp" and "ftp" will call up some default software probably already in your system, but there are many others which can handle the ftp and sftp protocols. Meanwhile, the lftp app can do sftp, ftp and many other protocols...

Anyway, whether you use a secure protocol or not is just down to if you care about the security of your password and data. :)

---

