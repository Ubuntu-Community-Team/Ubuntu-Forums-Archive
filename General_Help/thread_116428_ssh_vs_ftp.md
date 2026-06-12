---
title: "ssh vs ftp"
date: 2006-01-12
forum: General Help
---

### Post by matva on 2006-01-12
i hear a lot of talk about ssh, so im guessing a lot of people use it. From my understanding, it is a protocal for transferring files between computers. if this is correct, what are the advantages to ssh vs ftp besides encryption?
what are some good uses for ssh (in other words, what can it do for me)? How do i set up an ssh server in both windows and ubuntu?

---

### Post by nkhansen on 2006-01-12
SSH is not actually a protocol for transfering files. It as actually a way to issue commands to another computer in a secure way (SSH = Secure SHell). It can be used to transfer files via sftp/scp, and to route X-connections through. Besides encryption, you ask. Well, encryption is what ssh is all about. You can also compress a ssh connection.

---

### Post by taurus on 2006-01-12
In real basic terms, if you want to connect to another computer, then use ssh (NOT telnet).  But if you want to transfer files between computers, then gftp is one of many apps for it...

---

### Post by Drain on 2006-01-12
[QUOTE=matva]
what are some good uses for ssh (in other words, what can it do for me)? How do i set up an ssh server in both windows and ubuntu?[/QUOTE]

Let me answer the last question first: [The Unofficial Ubuntu Guide to the rescue!]("http://www.ubuntuguide.org/#sshserver") 

ssh allows you to run commands on the server from a remote computer.  Anything you can do from a command-line on your desktop, you can use ssh to do those same things remotely.  (It can do some GUI programs as well, just don't expect it to be fast).  It can also do encrypted file transfers, but you already knew that.

---

### Post by darth_vector on 2006-01-12
> How do i set up an ssh server in both windows and ubuntu?

sudo apt-get install ssh

will set up an ssh server on your ubuntu box with default settings. dont know how to do it in windows.

---

### Post by matva on 2006-01-12
thanks guys... this gives me a much better understanding. my command line skills are very weak, so i think ill stick to vnc.

---

