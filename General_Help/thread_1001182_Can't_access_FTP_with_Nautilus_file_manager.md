---
title: "Can't access FTP with Nautilus file manager"
date: 2008-12-03
forum: General Help
---

### Post by Schammy on 2008-12-03
I'm running the latest version of Ubuntu and am having trouble connecting to my FTP server with Nautilus.  I'm using the proper format in Nautilus to connect to my FTP site...

    [ftp://username@ftp.server.com](ftp://username@ftp.server.com)

...and I get errors telling me it can't connect.  I also can't connect to my public folder on the FTP server.  Finally, I can't connect to other known accessible FTP servers like [ftp://ftp.ubuntu.com/](ftp://ftp.ubuntu.com/).  Additionally, I can access my files on the FTP server with Filezilla but I don't want to have to use a separate client.

Anyone else having this problem?  What trouble shooting steps can I take?

---

### Post by oldos2er on 2008-12-03
I just connected to ftp.ubuntu.com with no problems. Instead of giving Nautilus a URL, check FTP (with login) under Service type, and type your username in the User Name field.

---

### Post by LinuxRocks713 on 2009-01-23
If you're looking to mount it permanently, here's a good solution:

[http://www.compdigitec.com/labs/2008/12/07/mount-a-ftp-share-in-ubuntu-as-a-folder/](http://www.compdigitec.com/labs/2008/12/07/mount-a-ftp-share-in-ubuntu-as-a-folder/)

---

