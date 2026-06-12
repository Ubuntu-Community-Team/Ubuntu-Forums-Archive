---
title: "Postfix and all the related stuff is driving me nuts"
date: 2009-05-20
forum: General Help
---

### Post by nevets_anderson on 2009-05-20
Ok

Not so long ago on a distribution that shall not be named it was a fairly easy process to set up postfix and get it talking to other mail servers and other clients. (I did it with about 4 lines of code)

I've been mucking about for a week or so now and am thoroughly confused - and puling my hair out.
 
Due to certificates and for example trying to create them (ie self signed)

Following the instructions in the documentation I get this when typing the recommended command.

openssl x509 -req -days 365 -in server.csr -signkey server.key -out server.crt
server.csr: No such file or directory

Also some of the documentation is marked that it needs updating. So what do you do?

Although people have written some long and detailed information about the install process the best I can do at the moment is run something from my server - all of it via cli this whole issue with mail directorys, certificates etc - In a nutshell I'll admit it I am now utterly confused and very frustrated.

I think that installing postfix has become a nightmare for the average user. This I believe is bad for Ubuntu.

I need a simple fairly secure postfix installation that preferably dosen't need certificates, and can be completed in a few lines.I also need something like dovecot to talk to it and have smtp and pop working out of the box.

Anyone have any idea on how to sort this out?

Regards

Nevets

---

### Post by dcstar on 2009-05-20
> **nevets_anderson said:**
> 
.........
I think that installing postfix has become a nightmare for the average user. This I believe is bad for Ubuntu.

I need a simple fairly secure postfix installation that preferably dosen't need certificates, and can be completed in a few lines.I also need something like dovecot to talk to it and have smtp and pop working out of the box.

Anyone have any idea on how to sort this out?


I installed the postfix package, selected "Internet" as the type of server and it worked immediately.

For convenience, I manually set my ISP's mail server as the mail relay, added in a few alias domain names and it still works.

If you want SSL SMTP connections then you need a certificate, if you do not know how to set this up don't blame the postfix package, it works fine.

---

### Post by nevets_anderson on 2009-05-20
Ok - I'll try and contain the rage and start explain the problems

David I'm glad it worked for you 
- I'm not blaming the postfix package - but I think the documentation and procedures are at fault.

My concerns are

-Not enough explanation of what is possible - and what is needed
-Badly or not at all revised documentation
-Possible that there is 2 much emphasis on massively secure installations 
-Previous version of postfix and Dovecot for example just worked with 4 or 5 lines of configuration.

Anyway now on to what I'm trying to make happen

My current setup

Real-ip-address
     |----------> Router set up to forward ports to server

(note Dns is working fine both inside and outside the network)
These are the open ports on the router all forwared to the server
25/tcp   open  smtp
53/tcp   open  domain
80/tcp   open  http
110/tcp  open  pop3
995/tcp  open  pop3s



         The Server - set up with 192.168.1.0 /24 type address

These ports are open on the machine (the 192.168.1.0 /24 address)

22/tcp   open  ssh
25/tcp   open  smtp
53/tcp   open  domain
80/tcp   open  http
110/tcp  open  pop3

The test mentioned in the server documentation gives this
-----
telnet mail.mydomain.com 25 

ehlo mail.mydomain.com 

-----Which Gives this result

ehlo mail.mydomain.com
250-mail.mydomain.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN

lack of these response are a concern
??

250-AUTH LOGIN PLAIN 
250-AUTH=LOGIN PLAIN 

??

The good news is that from the mailserver it's self I can send and receive mail via teh cli (phew!) But for the life of me I can't get a client to connect from another machine.

- Also I'm confused about selection of mailboxes (these seem to have been changed due to various configuration attempts) I'm finding that 

mutt -f /home/myaccount/Maildir 

seems to be working but if I just type Mail then I seem to get a whole lot of older stuff.

How do I make mutt the default client and set the Maildir ?

Anyway - If anyone can suggest anything, or you need further clarificaton let me know

TIA

Nevets

---

