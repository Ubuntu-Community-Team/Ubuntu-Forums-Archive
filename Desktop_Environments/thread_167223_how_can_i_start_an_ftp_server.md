---
title: "how can i start an ftp server"
date: 2006-04-28
forum: Desktop Environments
---

### Post by rocarm on 2006-04-28
I've lost the address for the ubuntu guide, i was just curious as how to install an ftp server.. what are some of the key things i should look at? I want 2 users, but want 1 to be locked to a specific directory, can someone suggest a program that will accomodate my needs?

Thanks

---

### Post by Kethinov on 2006-04-28
The simplest way to do it is to not use a FTP server, but a SSH server and do all your FTP through SFTP. Any competent FTP client supports this protocol in full.

The first thing you'll need to do is **sudo apt-get install openssh-server** from the terminal. Then you'll be able to SFTP to that computer using any user account currently available on the Linux machine. You might make a new user called "fileserver" or something if you're looking to do special things with FTP.

Alternatively, you can set up a traditional FTP server by following [this guide](http://ubuntuforums.org/showthread.php?t=79588) among others. But in my opinion, it's more trouble than it's worth. And SFTP over SSH is more secure anyway.

---

### Post by rocarm on 2006-04-28
thankyou! Worked a charm!

---

