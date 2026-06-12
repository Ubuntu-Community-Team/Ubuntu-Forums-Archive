---
title: "Nautilus ssh issues"
date: 2005-12-05
forum: Desktop Environments
---

### Post by dtradd on 2005-12-05
Hi everyone!

I use Nautilus (in Ubuntu 5.10) to connect to several ssh servers. I haven't had any problems, but some days ago one the servers was upgraded. They changed some things, among them a hard drive and the network card. They also changed the users' passwords.

I started a session from the terminal, using ssh, to change my password. I had to edit the file ~/.ssh/known_hosts so my system could "recognize" the server. So far, I had no problems, I could log in and change my password.

However, the problem raise when I tried to connect to the server using Nautilus. It refuses and gives me this message:

Can't show:
"sftp://myuser@the.server:22/"

I installed the keyring manager to check the keyring (...) and found no problems. The point is that I can log in without any problems using the shell or gFTP, but I can't log in with Nautilus. I wonder if Nautilus saves the firm of the servers it logs in somewhere, in a different file from ~/.ssh/known_hosts.

Thanks in advance for any help or tip you could give me.


Cheers!!

dtradd

---

### Post by cgjones on 2005-12-05
I ran into a similar problem. In know_hosts, try deleting the entry completely for the server you are trying to connect to.

---

### Post by dtradd on 2005-12-06
Many thanks for the answer. I tried that and it didn't work. I even deleted my known_hosts file and reautentified all the servers, but this one is still not working.
The strange thing is that I can acces it using the terminal or gFTP but I can't log in using Nautilus.
Perhaps it's a Nautilus bug... I really don't know.

---

### Post by .dm on 2006-05-16
Ive got same problem with Dapper Drake, not sure when it started but ssh server mapped via nautilus seems to generate a different fingerprint in known_hosts from ssh command line tool. 

Basically whichever one make the entry first cuts the other one off.

Very annoying bug that made me switch back to XP :(

---

### Post by dtradd on 2006-05-16
It is annoying indeed. Actually, what I've done is switch to KDE and the fish protocol with Konqueror works excellent.

Cheers!

---

### Post by tribaal on 2006-06-16
*Bump*

Anybody have any more info on this? Is it a reported bug? Is there a workaround?

Cheers

- trib'

**EDIT:** Adding the destination host to /etc/hosts seems to solve the problem for me. Maybe the issue is just a name resolution timeout?

---

### Post by phico on 2006-06-30
Same issue for me,  I can connect with ssh command line
but nautilus fails ... ?!?  It is not a dns resolution problem in my case
because I use IPs

Resolved :  I got it by removing .ssh/knownhosts, an entry in .nautilus/metafiles
and logout/login

---

