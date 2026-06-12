---
title: "How do I map an FTP connection to a folder for &quot;regular&quot; use?"
date: 2006-02-11
forum: Desktop Environments
---

### Post by aaronshaf on 2006-02-11
How do I map an FTP connection to a folder for "regular" use?

---

### Post by moephan on 2006-02-11
I think what you might be looking for is having a folder on your desktop that points to an ftp share. This is easy to do in Ubuntu:

1. Go Places->Connect to Server
2. In the Connect to Server Dialog, set "Service type" to either "Public FTP" or "FTP with login" depending on the ftp server you are connecting to.
3. Fill in the dialog with the server name, your login, etc...
4. Click "Connect" 
5. After connecting, this will leave a folder on your desktop that connects to the ftp server, and also ads it as an entry in your "places" menu.

HTH

Chees, Rick

---

### Post by aaronshaf on 2006-02-11
I've done that, but unfortunately it doesn't seem that Eclipse can see it in the file dialogue?

---

### Post by KyleFox on 2006-06-08
I'm having the same problem...

I've mounted my website's FTP location, but I'm unable to use it like a normal directory in tools like Bluefish.

---

