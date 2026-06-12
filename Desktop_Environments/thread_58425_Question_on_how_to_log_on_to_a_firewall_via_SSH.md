---
title: "Question on how to log on to a firewall via SSH"
date: 2005-08-20
forum: Desktop Environments
---

### Post by Strid on 2005-08-20
Hello,

When I wish to connect my computer to the internet, I have to log on to a firewall. This is done by typing the following command

ssh -T -l username fw1.k-net.dk

Then it prompts for my password. I have to do this on a second firewall, fw2.k-net.dk, aswell - "ssh -T -l username fw2.k-net.dk" and then my password. When this is done, I'm online and it works fine.

My question is, how could I  turn all this into a script that also types in the password for me?
I've been trying to use the ssh-keygen application, but I can't really figure out how it works.
A friend of mine suggested a script like this (doesn't work, though):

ssh -T -l username fw1.k-net.dk << end
password
end


It would be nice, if I could just type the command "sh login" and then it logged on to both firewalls and did all the password typing for me.

---

### Post by az on 2005-08-20
If you can put your authorised keys on the ssh server, you can log in passwordless.  Then you would be able to write a script to connect.

---

### Post by cwaldbieser on 2005-08-20
[QUOTE=Strid]Hello,

When I wish to connect my computer to the internet, I have to log on to a firewall. This is done by typing the following command

ssh -T -l username fw1.k-net.dk

Then it prompts for my password. I have to do this on a second firewall, fw2.k-net.dk, aswell - "ssh -T -l username fw2.k-net.dk" and then my password. When this is done, I'm online and it works fine.

My question is, how could I  turn all this into a script that also types in the password for me?
I've been trying to use the ssh-keygen application, but I can't really figure out how it works.
A friend of mine suggested a script like this (doesn't work, though):

ssh -T -l username fw1.k-net.dk << end
password
end


It would be nice, if I could just type the command "sh login" and then it logged on to both firewalls and did all the password typing for me.[/QUOTE]

Getting the passwordless key generation to work is really your best bet.  The technique your friend recommended doesn't work because programs like "passwd" don't read from standard input-- they often go to the trouble of making sure they are reading from a console device.

---

### Post by Strid on 2005-08-21
Thank you guys, for the replies. Unfortunately, I don't think that I'm allowed to put keys on the server. I have a small program that runs in Windows that can log on for me automatic at boot-up. I'd really like a script or something that could do that in Linux. I guess I should contact the a system administrator and ask him if he's got any ideas that could work for me.

---

### Post by krazikamikaze on 2005-08-22
You should try a perl script with the [Net::SSH::Perl](http://search.cpan.org/~dbrobins/Net-SSH-Perl-1.28/lib/Net/SSH/Perl.pm) module. The module implements a secure shell in perl without using the actual ssh program, and it lets you enter a password. Note: you don't want Net::SSH, which is basically just a perl interface to the ssh program and doesn't let you enter a password.

I haven't read all the documentation so I'm not 100% sure it will work for you, but it should.

---

