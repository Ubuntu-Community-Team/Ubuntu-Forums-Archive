---
title: "I need some help making a Shell script."
date: 2009-01-25
forum: General Help
---

### Post by linuxisevolution on 2009-01-25
I created a script that launches xterm and automatically ssh'es into my server and asks for password. I want to create another , but have this one automatically enter my password into ssh and launch gnome-system-monitor, or any program for that matter. Here is what I have. I am new to this:

#!/bin/sh

xterm -e ssh -X root@192.168.1.125 | gnome-system-monitor

exit 0

____________________________

So how do I make it enter my password?? After connecting?

---

### Post by dad311 on 2009-01-25
I believe ssh requires you to enter a password or setup ssh without out a password between two trusted machines.

You might try creating an "expect script".  An expect script will send a series of commands, logins, passwords, etc. to a local or remote machine just as you were typing them in a terminal.  Try doing a  Google for "expect scripts".

---

### Post by linuxisevolution on 2009-01-25
> **dad311 said:**
> I believe ssh requires you to enter a password or setup ssh without out a password between two trusted machines.

You might try creating an "expect script".  An expect script will send a series of commands, logins, passwords, etc. to a local or remote machine just as you were typing them in a terminal.  Try doing a  Google for "expect scripts".

I'm confused. I read the tutorial and I'm still confused. Could you please give an example? Lets say the password was cheese. ( it's not..)

---

### Post by linuxisevolution on 2009-01-25
Is there another way? I can't figure expect out.

---

### Post by timvoet on 2009-01-25
you can try ssh key authentication.  you create a private and public key.  but this will entail setting up your server to accept public key authentication.

once that is setup

use the -i option for ssh

ssh -i <private_key_file> whatever other options.

---

### Post by Hobgoblin on 2009-01-26
Set up your ssh server to use public/private keys, this is an easy edit of the sshd config file (/etc/ssh/sshd_config).  I believe this is set up by default in recent versions of Ubuntu. (just tested by installing ssh server on one of my desktops and it is.

[This guide](http://www.ece.uci.edu/~chou/ssh-key.html) should get you sorted with your keys.

Then ssh user@hostname command

---

