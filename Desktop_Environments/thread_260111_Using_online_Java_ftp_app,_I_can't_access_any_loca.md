---
title: "Using online Java ftp app, I can't access any local directory"
date: 2006-09-18
forum: Desktop Environments
---

### Post by mjpatey on 2006-09-18
Hi, group-

The best option for uploading files to my church's website (hosted by our church's main HQ) is to use the church's online Java-based FTP app, called "UnlimitedFTP".  A little background on why: I'm not comfortable with any of the command-line ftp clients in Linux, and none of the GUI-based ones allow for TLS on the actual transfers (as opposed to only during the connecting phase), which the host requires.

So... when I try to upload using this online app in Windows, it works fine.  But in Ubuntu, it never allows me to access my local filesystem.  It displays my local folders (in the root directory), but when I try to select  a file to upload, or try to open a folder, it just tries for about 3 minutes, then times out.

When I told this to a very wonderful tech at my church's HQ, he replied that it looks like I'm trying to access a folder that my login user doesn't have permission to access.  He recommended trying to upload a file from my Home directory (which of course I can't do because I can't get into any folders!)

Is there some way to put myself in "sudo" mode to let me access my files from within this online app?  Since it's running in Java, inside Firefox, I have no idea how to tell it I'm a superuser.

Any idea?

Thanks for any help you may have!

---

### Post by kidders on 2006-09-18
Sounds to me like the java app is b0rked! Any chance you could post the .class file? (I'd be interested in decompiling it, to see if I'm right!)

In the meantime, terminal-based ftp clients are a snap ... don't be afraid to try one :-)

**Edit:** Afaik the only way to run a java applet embedded in a web page as root would be to log into your Gnome/KDE as root (or launch your browser with "sudo"). **_DON'T EVER DO THIS!_** This is quite deliberate, and prevents a website from doing something as the superuser behind your back, which would be unthinkable to a Linux user.

---

### Post by mjpatey on 2006-09-18
Well, I just tried sudoing myself into Firefox, but it had no effect on my problem... still times out trying to access files / folders.  However, it struck me funny when the Terminal responded to my request:

"You should really not run firefox through sudo WITHOUT the -H option.
Anyway, I'll do as if you did use the -H option."

A self-aware terminal!  :-)

So, for someone who likes all things GUI, which terminal-based FTP program would you recommend?  (It has to support TLS on transfers).

Thanks!

-Mark

---

### Post by kidders on 2006-09-20
They're all largely the same, really. Have a look in the package database and try one out :-)

---

### Post by mjpatey on 2006-09-21
Thanks, but they're not the same as I'd like them to be... the organization who hosts our site requires extremely strict security, including TLS on transfers (as opposed to just on the initial connection), and it turns out that most of the programs out there don't cut the mustard.  So far nothing I've found in Linux with a GUI will work.  LFTP may do the trick, but I'm not that handy with really complicated command-line stuff.

So, it turns out I found a newer version of UnlimitedFTP (the online Java-based FTP app my church has on their site) as a demo on UnlimiTech's site.  It works like a charm!

Thanks for all the suggestions.  Actually, pretty soon, we'll have a new hosting company, and all this won't matter, but for now it does!  Thanks, everybody.

---

