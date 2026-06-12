---
title: "Boot error"
date: 2006-10-01
forum: Desktop Environments
---

### Post by RudolfMDLT on 2006-10-01
Hi,

I have been having troubles the past day or two booting up Ubuntu. When booting, at the orange Ubuntu splash screen the headings of what is booting apear like normal woth the [OK] apearing next to them, until Ubuntu reaches BASIC NETWORKING. From here a black and white screen appears and says the following:

[PHP]cannot remove /etc/mail/sendmail.cf :read only file system
Updating Autehntication
/usr/share/sendmail/update_auth : line 98 : cannot create temp file for here

Creating  /etc/mail/relay
Optional file

You should Issue "/etc/init.d/sendmail reload"[/PHP]

When KDE loads it brings up an error dialog, but it only brings up this dialog when I have booted with my bluetooth adapter plugged in. When unplugging the adapter, and restarting, i don't get the error but I still get the boot error described above.

When I tried reloading the sendmail I recieved an error:

rudolf@rudolf:~$ /etc/init.d/sendmail reload
Reloading Mail Transport Agent configuration: sendmailtouch: cannot touch `/var/run/sendmail/stampdir/reload': Permission denied
rudolf@rudolf:~$


I have set all the file permisions in the /etc/mail folder so that anyone can read them and still this error.

Can someone please help me!

Thank you

Rudolf

---

### Post by brum76 on 2006-10-02
For one, you should run the reload as root, not as a normal user. That's why you're getting the "Permission denied" error.

---

### Post by RudolfMDLT on 2006-10-02
Thank you - But how do you or any one else for that matter know either how to fix the main error, or work around it? It would be great if I could get a flauless boot up!

---

### Post by RudolfMDLT on 2006-10-02
Thanks, I can now restart the service one KDE has loaded. Do you know what the service does?

---

### Post by zoutmax on 2007-06-21
Hi i got the same error at boot anyone has an idea i getting lost ...

[http://ubuntuforums.org/showthread.php?p=2885147#post2885147](http://ubuntuforums.org/showthread.php?p=2885147#post2885147)


Thanks

---

