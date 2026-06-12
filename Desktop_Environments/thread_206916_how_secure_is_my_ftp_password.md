---
title: "how secure is my ftp password?"
date: 2006-06-30
forum: Desktop Environments
---

### Post by tefflox on 2006-06-30
I guess this might not be an ubuntu-related question, but I was warned that if I use ftp, there will be attempts on the password.  I just set up a domain, [listenlight.net]("http://listenlight.net/"), not locally but on a remote, full-service host.  Should I be concerned about my ftp and ssh passwords?  For instance, if I know of some people in particular who might target me?  thx..

---

### Post by invalid on 2006-06-30
[QUOTE=tefflox]I guess this might not be an ubuntu-related question, but I was warned that if I use ftp, there will be attempts on the password.  I just set up a domain, [listenlight.net]("http://listenlight.net/"), not locally but on a remote, full-service host.  Should I be concerned about my ftp and ssh passwords?  For instance, if I know of some people in particular who might target me?  thx..[/QUOTE]
As a general rule, any machine that has services available to remote users, should have secure passwords. This is especially true for ftp and ssh services.

People use bots to scan addresses for services, and automatically try to gain access usually with a dictionary or brute force attack. FTP accounts are great for storing warez and illegal software, SSH is great for launching remote attacks on other machines.

I would definetly advise on a secure password, utilizing alphanumeric characters as well as special symbols.

---

### Post by tefflox on 2006-06-30
is there any kind of timeout (or can I set this timeout) on the password SEND (or what-have-you) so an automated attack would be useless?

I mean if the attack is really automated and brute force with no request timeout, how would it even matter to have a tricky password?

---

### Post by taurus on 2006-06-30
You can set an expiration on the password to force the users to change their passwords.  Also, you can set some restriction on how many characters a password needed to be and it should also include some special characters or numbers.  Other than that, there is nothing else you can do as long as you have ftp and ssh servers running on your machine.  To feel a little safer, you can also install firewall like firestarter...

---

### Post by echo $USER on 2006-06-30
The best thing to do is transfer your files using ssh; the password is encrypted unlike ftp.

---

### Post by tefflox on 2006-06-30
in case there is some confusion, i do not host on my machine, i'm only using ftp/ssh to connect to a web hosting service.  is it still the same?

---

### Post by tefflox on 2006-06-30
[quote=tefflox]in case there is some confusion, i do not host on my machine, i'm only using ftp/ssh to connect to a web hosting service.  is it still the same?[/quote]

so if someone wants to attack me, they know my ip and can (somehow, plz tell me how!) filter my transmissions, they can just cherry-pick my ftp password?

---

### Post by thk on 2006-06-30
Post your password and I'll tell you... :D 

Seriously, use sftp if possible. If you are forced to use ftp, simply use a unique password for that server. In the worst case (very unlikely) someone will gain access to your account on the web server. At least they wont get access to all your other accounts.

---

### Post by tturrisi on 2006-07-01
So it appears that you want to know how secure it is when you access an ftp server (outside your lan), such as a web host?

The answer is that FTP is NOT secure.  FTP clients send the username and password in plain text, just like POP email does.  Therefore, if someone was sniffing the wire or wireless connection then they could see your usernames & passwords using a network monitor like Ethereal.

Some web hosts support ssh or sftp.  Most however do not support it.  My experience has been that cheap hosting accounts do not allow sftp or ssh, whereas a hosting account with a dedicated server of your own will support secure transfers.

I maintain several web sites and use ftp for all but one of them.  The ones I use ftp on have no documents online that are private or confidential.  Realize, that a criminal who sniffs for ftp data is usually targeting sites that have some type of ecommerce or software downloads.  They won't be targeting folks who are uploading to personal web space or small personal sites.

So, if using POP or FTP, use a strong password such as one that contains at least 8 characters (10 is better) and use caps, lower case, numbers and special characters in it.  example:
**Wfg3&*H**

A strong ftp & pop password is primarily a security layer for ONLY the server, not the user.  Because as I said earlier, these names are sent in plain text and a sniffer can see them plain as day.  A strong pass DOES deter someone from guessing your passwrd though.  A 10 character mixed character password will take a little over a year to crack using the fastest comp w/ cracking tools running 24/7.

---

