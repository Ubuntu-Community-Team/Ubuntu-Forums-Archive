---
title: "What do I do to get ubuntu server up and running?"
date: 2009-01-18
forum: General Help
---

### Post by Dustin2128 on 2009-01-18
Ok, I managed to get ubuntu server running properly in virtualbox (inside my ubuntu desktop installation) I have the gnome interface for user friendliness, and I have it set up as a mail server, and every other optional thing it had when I was installing. I set the second part of the email as my website, so I, and my friends could share an email from our own website e.g. [email]dustin@thebestwebsite.terapad.com[/email]. What do I do to set it all up? I have virtualbox settings at default except for pae, which is required. I need in depth instructions. If anyone would also have instructions on setting up an ftp server, I'm planning on hosting 001 games we made for download. Http server would also be usefull.

---

### Post by mssever on 2009-01-18
> **Dustin2128 said:**
> Ok, I managed to get ubuntu server running properly in virtualbox (inside my ubuntu desktop installation) I have the gnome interface for user friendliness, and I have it set up as a mail server, and every other optional thing it had when I was installing. I set the second part of the email as my website, so I, and my friends could share an email from our own website e.g. [EMAIL="dustin@thebestwebsite.terapad.com"]dustin@thebestwebsite.terapad.com[/EMAIL]. What do I do to set it all up? I have virtualbox settings at default except for pae, which is required. I need in depth instructions. If anyone would also have instructions on setting up an ftp server, I'm planning on hosting 001 games we made for download. Http server would also be usefull.
For a mail server, postfix is a common choice. For HTTP, apache2 is the most popular choice. For FTP, I don't know, since I consider FTP to be a security hole (I use SCP instead, which comes with the openssh-server package).

For each of these servers, Google can find plenty of information on how to use them.

---

### Post by Dustin2128 on 2009-01-18
well, not neccisarily ftp, but some sort of server that allows for file downloads

---

### Post by mssever on 2009-01-18
> **Dustin2128 said:**
> well, not neccisarily ftp, but some sort of server that allows for file downloads
A webserver? Apache.

---

