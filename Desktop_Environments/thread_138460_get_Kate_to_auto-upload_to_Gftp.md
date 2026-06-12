---
title: "get Kate to auto-upload to Gftp?"
date: 2006-03-01
forum: Desktop Environments
---

### Post by geuis on 2006-03-01
I'm switching over from Windows to Linux. I really liked using WinSCP on Windows to do web development because I when I remotely edited a file and it would open locally in Textpad, when I did a local save cnt-save it would automatically update to the ftp server in the background without making me close the current working document.

Is there a way that I can get the same thing to happen with gftp and Kate? If not, is there another similar solution that would support what Im trying to do?

---

### Post by RAOF on 2006-03-02
If WinSCP is accessing your ftp server over SCP, you should be able to get nautilus (Gnome's filebrowser) to connect to it as a mountable resource.  You could then edit your stuff directly on the server.

It would be the "Connect to Server" action.  I think it's under Computer->Connect to server.  It should be somewhere easy to find.

---

### Post by GeneralZod on 2006-03-02
Kate, being a full-fledged KDE app, should do this automatically anyway due to its kio_slave supportt - it's what I use to edit any webpages I have, directly from the server.  Maybe it's different in GNOME, though, but I'd be surprised.

When in kate, click Open, then as the location do [ftp://whereevermyremotefilesarehosted](ftp://whereevermyremotefilesarehosted) and browse to your file and open it.  Every time you edit it and click Save, and the changes should transparently be copied to your server.

Edit:

Re-reading your post, you might want to use sftp://; I'm not sure.  KDE has support for dozens of kio_slaves inclusion fish:// (file manipulation and transfer over ssh; kind of like scp) and I'm not sure which your setup requires.

---

### Post by geuis on 2006-03-02
RAOF, thanks for the advice. Filebrowser integrates the whole process perfectly. I like Kate, though I wish it would open faster. But thats because this is an 800mhz pc. Thanks! +1 for ubuntu.

---

