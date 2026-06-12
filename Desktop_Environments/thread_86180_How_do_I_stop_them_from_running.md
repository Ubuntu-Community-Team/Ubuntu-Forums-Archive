---
title: "How do I stop them from running?"
date: 2005-11-04
forum: Desktop Environments
---

### Post by VR6Pete on 2005-11-04
I want to stop the following services from running on my box... 

Also, what are the services that i've highlighed with a ** ?

PORT      STATE SERVICE
89/tcp    open  su-mit-tg**
110/tcp   open  pop3
143/tcp   open  imap
199/tcp   open  smux **
631/tcp   open  ipp **
5900/tcp  open  vnc
32770/tcp open  sometimes-rpc3 **

Thanks,

Pete

---

### Post by Xian on 2005-11-04
Install the sysv-rc-conf package to manage runlevel services.

---

### Post by mwillems on 2005-11-04
[QUOTE=Xian]Install the sysv-rc-conf package to manage runlevel services.[/QUOTE]

Wow, I wondered about that too.

So OK, I have installed it - now how do I run it? I can't find it in any menu. I am presumably not looking right.

---

### Post by Xian on 2005-11-04
Open it from a terminal. Just issue the command:

$ sudo sysv-rc-conf

---

### Post by mwillems on 2005-11-04
Oops, ok, figured it out. Command line.

But it only has some services... how about services and deamons that I want to add, like sshd?

---

### Post by NewWithoutClue on 2005-11-05
[QUOTE=mwillems]Oops, ok, figured it out. Command line.

But it only has some services... how about services and deamons that I want to add, like sshd?[/QUOTE]

sshd will automagically add itself to start up at boot as a daemon.
If at anytime it hasn't simply do the following...
'sudo /etc/init.d/sshd start'
that will start it..there are other options like reload...stop...restart..and maybe one or two more...that's for you to look into isn't it :)

w00t
Paul.

---

### Post by ratsalad on 2005-11-05
Hmm, actually... I find the standard Debian update-rc.d easier than that sysv-rc-conf package.

example:

$ sudo update-rc.d -f ssh remove

---

