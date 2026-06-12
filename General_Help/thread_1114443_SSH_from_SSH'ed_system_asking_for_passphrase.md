---
title: "SSH from SSH'ed system asking for passphrase"
date: 2009-04-02
forum: General Help
---

### Post by dmouck on 2009-04-02
Hi folks,

This might be more of a linux in general question than Ubuntu, but I figured that this would be a great place to start.

Okay, so I've followed the documentation on several sites that show how to ssh to a remote system without requiring a password (e.g. ssh from B to C). I have set it up and tested it, and it's working flawlessly.

But here's the weird part: When I ssh into B from another computer and THEN try to SSH into C (e.g. from A, ssh into B and then ssh into C), this is when it asks me to enter passphrase for key $HOME/.ssh/id_dsa .

So to summarize: when I'm B and ssh into C, it works without requiring a password. But when I am on A and SSH into B and THEN ssh into C, it asks for the key. By the way, it doesn't matter what system A is. Basically, unless I'm local on B, it asks for a password.

Any thoughts? Thanks!

---

### Post by kevstar31 on 2009-04-03
Try using an ssh tunnel
ssh -L 21:*hostnameB*:22 -l *user* -N *hostnameB*
then
ssh *user*@*hostnameC*:21

---

### Post by dmouck on 2009-04-03
I tried the command (as sudo) and it just sat there, never got to the point where I could start the next ssh session.

---

### Post by CyberMando on 2009-04-03
You have your agent setup so it asked you for your key on A and then let you into B because of the agent. Nothing is loading an agent on B to allow you to connect to C so it asks you for the passphrase. At that point if you hit enter without typing anything it will ask you for your password.

You can enable agent forwarding in sshd_config or you can use keychain.

---

