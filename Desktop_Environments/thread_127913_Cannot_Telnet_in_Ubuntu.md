---
title: "Cannot Telnet in Ubuntu"
date: 2006-02-10
forum: Desktop Environments
---

### Post by akdkumar on 2006-02-10
Hi

I Use Linux ubuntu 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686 GNU/Linux.

When I telnet to myself I get the message "telnet: Unable to connect to remote host: Connection refused"
What could be wrong?
Is there some command I have to give to start telnet services?

---

### Post by heimo on 2006-02-10
Instead of telnet (which is pretty much insecure), use ssh.
[https://wiki.ubuntu.com/SSHHowto](https://wiki.ubuntu.com/SSHHowto)

---

### Post by akdkumar on 2006-02-10
Hi

I tried it. Now I get message

ssh: connect to host ubuntu port 22: Connection refused

---

### Post by heimo on 2006-02-10
Did you install ssh-server? Do you have firewall blocking this port?

---

### Post by akdkumar on 2006-02-10
[QUOTE=heimo]Did you install ssh-server? Do you have firewall blocking this port?[/QUOTE]

I did not install ssh-server. I have no firewall.

---

### Post by heimo on 2006-02-10
Well. You need ssh-server running on the computer you want to connect to (see the link above for instructions.)

---

### Post by dcstar on 2006-02-10
[QUOTE=akdkumar]Hi

I Use Linux ubuntu 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686 GNU/Linux.

When I telnet to myself I get the message "telnet: Unable to connect to remote host: Connection refused"
What could be wrong?
Is there some command I have to give to start telnet services?[/QUOTE]
Install telnetd

---

### Post by heimo on 2006-02-11
[quote=dcstar]Install telnetd[/quote]

Depending on what he's really trying to accomplish... But most of us should keep away from using telnet over any kind of networks*. Telnet client is still usable for debugging some problems, but telnet servers should be replaced by secure ones, like ssh. (This should have happened ~10years ago.) :)

*) And if someone doesn't know: Regular telnet sends all the data in plain text (that's unencrypted, insecure) - including authentication (passwords). That's a Bad Idea.

---

### Post by akdkumar on 2006-02-11
[QUOTE=dcstar]Install telnetd[/QUOTE]
Hi

How do I install telnetd?...

---

### Post by heimo on 2006-02-11
[quote=akdkumar]Hi

How do I install telnetd?...[/quote]

:cry: Please, don't. And if you still wish to do that:
```
sudo apt-get install telnetd-ssl
```

But it'd be much wiser to just install ssh-server
```
sudo apt-get install ssh-server
```
And istead of using telnet to connect to that machine, use ssh.

---

### Post by alamba on 2006-02-11
Dinesh I would earge you to use ssh instead of telnet. The functionality and way of working is the same. However it encrypts your password before sending it accross a channel. 
Go to System>Admin>Synaptic
Right click on ssh-server and click on install.

Then use a ssh client such as Putty to ssh into the machine.

A

---

### Post by cwaldbieser on 2006-02-11
[QUOTE=alamba]Dinesh I would earge you to use ssh instead of telnet. The functionality and way of working is the same. However it encrypts your password before sending it accross a channel. 
Go to System>Admin>Synaptic
Right click on ssh-server and click on install.

Then use a ssh client such as Putty to ssh into the machine.

A[/QUOTE]
The point is probably minor, but ssh encrypts the whole channel rather than just the password.  Different types of authentication mechanisms are supported as well, and if you used kerberos, for example, the password would not be sent over the channel at all.

You are right that ssh is a lot better to be using than telnet in most cases, though.  ssh also some other nice side benefits besides security:

+ You get a 2 nice file transfer mechanisms (scp and sftp) in addition to the remote shell for installing just the single ssh server.
+ You can forward arbitrary ports.

---

### Post by alamba on 2006-02-11
Agreed cwald. I've been asking all of my clients to move to scp instead of running ftp servers for ages now. End of the day...better peace of mind.

A

---

### Post by akdkumar on 2006-02-17
Hi

I installed ssh server. Now I can ssh the server from itself. But I still cannot ssh it from my desktop PC/Unix System, which is what I wanted. 

ssh does not exist in Windows XP or  (HP)Unix.However, telnet exists.

I tried installing telnetd-ssl. I get the error message 

E: Couldn't find package telnetd-ssl

---

### Post by heimo on 2006-02-17
> ssh does not exist in Windows XP or  (HP)Unix.However, telnet exists.


Here's ssh client for Windows
[http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)
[http://www.openssh.com/windows.html](http://www.openssh.com/windows.html)

And I know for sure that you can get ssh client for HP-UX too.

---

### Post by akdkumar on 2006-02-18
Hi

I downloaded and installed PUtty and now ssh is working fine.

Thank you all for the replies.

:D

---

