---
title: "Having troubles installing pure-ftpd"
date: 2006-01-14
forum: General Help
---

### Post by nick89 on 2006-01-14
I will confess, I'm a major linux noob. Can anyone give me a step by step instuctions to install this ftp server?

---

### Post by nkhansen on 2006-01-14
I don't have much experience with pure-ftpd. But the installation should go like this:

Commandline:

$ sudo nano /etc/apt/sources.list/
 - uncomment the appropriate lines for enabling the universe repository (that would be anything starting with 'deb' and having the word universe in them.

$ sudo aptitude update

$ sudo aptitude install pure-ftpd


Graphical (now this could be a problem since my software is in danish):

<System -> Administration -> Synaptic>

<Settings -> Repositories (or Archives)>

<Add>
Choose universe in the list and press OK.

Now you can search and install pure-ftpd.


Hope this was any help to you. If you are looking for a program, and can't find it, packages.ubuntu.com is a good place to search. It shows you what repository is in.

---

### Post by back2ubuntu on 2006-01-14
Hi,

I have a related problem with FTP under ubuntu.
I try from home to ftp to/from my machines at work. 
Using the Applications -> System Tools -> Network tools, everyhting goes fine, I mean I can ping, route, etc. Connecting via konqueror, ok. However, no tranfer is possible (even of a very small file) neither with knoqueror, nor gFTP, or kbear (these latter two don't even succeed to connect). On the other hand, Telnet works fine!

Is there any body who has a clue how to solve this problem.
cheers.

---

