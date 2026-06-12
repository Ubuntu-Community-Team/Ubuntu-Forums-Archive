---
title: "Help - How have I corrupted Nautilus ?"
date: 2009-04-22
forum: General Help
---

### Post by sk1ds on 2009-04-22
Hi all,
 
first post, and newbie to Ubuntu.
 
I have been running 8.10 for a month or so now and really happy with it.
 
Today, in a terminal window, I by mistake tried running a .PDF document.
This obviously just displayed a whole load of junk on the screen and I thought..ok, so what.
 
Then, when I tried to start the home folder form Places--> Home Folder
I get the "Starting File Browser" appear on the bottom panel for about 8 seconds and then disappear without opening the file browser.
 
If I go to Places-->Computer I get the Computer - File Browser window without any problem, BUT, as soon as I select a directory to browse
to from the File Browser, the same issue occurs, the Computer - File Browser window disappears,
the starting file Browser appears on the bottom panel and then does nothing again.
 
The only message I can find in /var/log is as follows
 
**nautilus[7966]: segfault at 8 ip b7206b7e sp b686bf54 error 6 in libc-2.8.90.so[b7195000+158000]**
 
And this appears in kernel.log, syslog.log and messages.log
 
I am completely up to date with recent updates etc, am running Gnome and compiz fusion.
 
I would really appreciate some help in resolving this, and i'm scared I might have to do a complete re-install.
 
Many thanks
 
Neil

---

### Post by juancarlospaco on 2009-04-22
Maybe you have too much files in your home folder for your RAM, or multimedia files, 
and when you try to open it, nautilus get stuck, generating thumbnails, and stuff...

reinstall nautilus, use bleachbit.

---

### Post by BslBryan on 2009-04-22
Hello. :-)

I'm not really sure that opening a PDF would corrupt nautilus...  That's pretty ludicrous.  Especially considering it is entirely possible to open a pdf from the terminal.  What else can you think of that you've done in the last day?  Also, I hate to ask, but have you attempted to simply reboot?  If this doesn't work, all I can think of is for you to reinstall nautilus, and use bleachbit.:P

---

### Post by sk1ds on 2009-04-22
> **juancarlospaco said:**
> Maybe you have too much files in your home folder for your RAM, or multimedia files, 
and when you try to open it, nautilus get stuck, generating thumbnails, and stuff...
 
reinstall nautilus, use bleachbit.
 
 
Jaun - you beauty !!
 
 
not quite becuase of too many files - but you got me to look in my home folder
and there I found some files with strange names - including a lot of '?' characters in the filename.
 
 
I deleted these and now it is working again :)
 
 
Thanks everyone.
 
 
Neil

---

