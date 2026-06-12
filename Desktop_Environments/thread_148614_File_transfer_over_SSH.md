---
title: "File transfer over SSH?"
date: 2006-03-22
forum: Desktop Environments
---

### Post by pbaehr on 2006-03-22
I've got my Ubuntu computer set up so that I can connect to it via SSH using PuTTY and cygwin/x from my Windows laptop at work.

Awesome. I'm still impressed with everything I can do.

Now, I'd like to be able to move files from my Ubuntu computer to my laptop. Is there a command that will let me do this through my SSH connection or do I have to establish a second FTP connection? I can certainly set that up, too, but I'd like to keep things as simple as possible.

---

### Post by heimo on 2006-03-22
If you want to connect from Windows laptop to your Ubuntu box, you could use [WinSCP]("http://winscp.net/eng/index.php"), it uses ssh and has a nice easy to use interface. On your Ubuntu box, you can use scp on command line or nautilus (the file browser) to do the same.

---

### Post by pbaehr on 2006-03-22
Wow, just downloaded it. Works perfectly and does exactly what I wanted. Thanks for the quick response. You're my hero for the day. :D

---

