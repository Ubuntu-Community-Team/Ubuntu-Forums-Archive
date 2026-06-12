---
title: "Need help transferring files with SCP while SSH'ed into my machine"
date: 2009-03-17
forum: General Help
---

### Post by Nano_ext3 on 2009-03-17
Here is the chat log:


```
(11:26:03 PM) JoshuaRL: Nano_ext3: what you got.  ive only played with it a little bit, but i can try.
(11:26:11 PM) Nano_ext3: when I try to do so:
(11:26:12 PM) Nano_ext3: scp winamp_presets.gz mikeyd@75.75.140.181: /home/mikeyd/Desktop/
(11:26:21 PM) Nano_ext3: My password on my remote machine will not work
(11:26:42 PM) JoshuaRL: youre already ssh'd in>
(11:26:44 PM) JoshuaRL: ?
(11:26:46 PM) Nano_ext3: yes
(11:27:45 PM) JoshuaRL: then im not sure.  i never used scp.  but i never had to enter the pswd except at the beginning.
(11:28:04 PM) Nano_ext3: what did you use?
(11:28:23 PM) JoshuaRL: well, i was using portable putty
(11:28:46 PM) Nano_ext3: HAHA
(11:28:54 PM) Nano_ext3: worked flawlessly with gFTP
(11:28:54 PM) JoshuaRL: but i also ssh'd into my desktop with another desktop on my network
(11:29:03 PM) Nano_ext3: I was jw from terminal
(11:29:05 PM) JoshuaRL: just using cli ssh
(11:31:26 PM) Nano_ext3: problem is I dont use the default port to ssh in
(11:31:45 PM) Nano_ext3: this works sorta
(11:31:45 PM) JoshuaRL: that shouldnt matter, i dont think
(11:31:46 PM) Nano_ext3: scp winamp_presets.gz mikeyd@mikeyd-desktop: /home/mikeyd/Desktop/
(11:31:53 PM) Nano_ext3: but get denial on port 22
(11:32:03 PM) Nano_ext3: ssh: connect to host mikeyd-desktop port 22: Connection refused
(11:33:05 PM) JoshuaRL: weird its getting a connection error.  if you're already ssh'd in, then why would it do that?
(11:33:16 PM) Nano_ext3: idk?
(11:33:26 PM) JoshuaRL: wait.  are you trying to connect when you're already connected?
(11:33:38 PM) JoshuaRL: that would mean the port would be blocked, i think.
(11:33:43 PM) Nano_ext3: no just trying to scp the file
(11:33:50 PM) Nano_ext3: im already ssh'ed into my desktop
(11:34:46 PM) JoshuaRL: im sure bodhi will be able to help.  im really not an ssh expert.
(11:35:16 PM) Nano_ext3: maybe I will register a domain with no-ip, might help on the translation end
```

Not sure what is going on, if you need clarification, please reply , I am on the forums everyday.

Thanks for any help,

-Nano

---

### Post by Ynothna on 2009-03-26
Hey Nano,

Did you have any luck?

I've been playing with SCP lately. To change the port you're connecting with you need to put it in the command.

scp -P <port#> random.file [email]name@domain.name[/email]:/path/to/copy/to

Hope that helps :)

Ynothna

---

### Post by Nano_ext3 on 2009-03-26
Yea it works, although I prefer to use SFTP :)

---

