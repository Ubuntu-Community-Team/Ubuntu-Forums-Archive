---
title: "How do I set the passphrase for SSH logins?"
date: 2006-10-05
forum: Desktop Environments
---

### Post by kwilliam on 2006-10-05
Hi all,

I'm trying to set up SSH on my two computers (An Ubuntu Server and a Kubuntu desktop). I've run 
```
sudo apt-get install ssh openssh-server
```
on both of them. Unfortunately, logging in is too easily. When I initially try to connect, I get a mesasge:
```

$ ssh william@192.168.x.x

The authenticity of host 192.168.x.x can't be established.
RSA key fingerprint is 8b:47:bunch:of:numbers.
Are you sure you want to continue connecting (yes/no)?
```

I type 'yes' and am asked for william@192.168.x.x's password. I enter my regular admin password (sudo password) and am logged in remotely.

That's cool, but I want my remote logins protected by a passphrase. (Especially because my regular 'sudo' passwords aren't that strong.) How can I change it so that passphrases are required?

---

### Post by mitch.c on 2006-10-05
> **kwilliam said:**
> Hi all,

I'm trying to set up SSH on my two computers (An Ubuntu Server and a Kubuntu desktop). I've run 
```
sudo apt-get install ssh openssh-server
```
on both of them. Unfortunately, logging in is too easily. When I initially try to connect, I get a mesasge:
```

$ ssh william@192.168.x.x

The authenticity of host 192.168.x.x can't be established.
RSA key fingerprint is 8b:47:bunch:of:numbers.
Are you sure you want to continue connecting (yes/no)?
```

I type 'yes' and am asked for william@192.168.x.x's password. I enter my regular admin password (sudo password) and am logged in remotely.

That's cool, but I want my remote logins protected by a passphrase. (Especially because my regular 'sudo' passwords aren't that strong.) How can I change it so that passphrases are required?

You'll need to generate a key-pair. It's not too difficult, here's a good place to start: [https://help.ubuntu.com/community/SSHHowto#head-1ff9e61cfd81e9f741920b6920af8a85f7bddb30](https://help.ubuntu.com/community/SSHHowto#head-1ff9e61cfd81e9f741920b6920af8a85f7bddb30)
and: [https://help.ubuntu.com/community/AdvancedOpenSSH#head-f06532af79917a251e68c7ccf567cb5c399e0aba](https://help.ubuntu.com/community/AdvancedOpenSSH#head-f06532af79917a251e68c7ccf567cb5c399e0aba)

You definitely want public key authentication. After you get it set up, don't forget to change /etc/ssh/sshd_config:
```
# /etc/ssh/sshd_config
PermitRootLogin no
PasswordAuthentication no
```

Let us know if you have more questions.

---

### Post by kwilliam on 2006-10-07
I still haven't gotten key-based authentication working. Here's basically what I've done (names and passwords changed).

```
joe@compA$ ssh-keygen -t rsa

Generating public/private rsa key pair.
Enter file in which to save the key (/home/joe/.ssh/id_rsa): 
Enter passphrase (empty for no passphrase): th3-PaSsW0rD
Enter same passphrase again: th3-PaSsW0rD
Your identification has been saved in /home/joe/.ssh/id_rsa.
Your public key has been saved in /home/joe/.ssh/id_rsa.pub.

joe@compA$ ssh-add

joe@compA$ ssh-copy-id bob@compB
```

I checked, and compB has the correct public key in /home/bob/.ssh/authorized_keys. I've also made the changes to sshd that the AdvancedOpenSSH tutorial you linked to listed. However, I still only got plain text logins after restarting sshd both computers, and when I set "PasswordAuthentication no" on compA, I simply got denied.

On the bright side though, I may be safe using only plain-text authentication. I'm only SSH-ing between my desktop and my HTTP server, both of which are connected to the same router. The router's port-forwarding is set only to forward port 80 to the server, so **is there any way that someone outside my local network could actually even attempt to SSH into one of my machines?** Am I right in thinking that all they could 'speak' to would be the router, which they obviously can't SSH into? (It's a Linksys wireless router.)

---

### Post by mitch.c on 2006-10-08
> **kwilliam said:**
> I still haven't gotten key-based authentication working.

...

I checked, and compB has the correct public key in /home/bob/.ssh/authorized_keys. I've also made the changes to sshd that the AdvancedOpenSSH tutorial you linked to listed. However, I still only got plain text logins after restarting sshd both computers, and when I set "PasswordAuthentication no" on compA, I simply got denied.

As I understand it, you are trying to login to computer A (ssh server), from computer B. If this is the case, the public key belongs in the ~/.ssh/authorized_keys file on computer A. The private key belongs on computer B.

> **kwilliam said:**
> On the bright side though, I may be safe using only plain-text authentication. I'm only SSH-ing between my desktop and my HTTP server, both of which are connected to the same router. The router's port-forwarding is set only to forward port 80 to the server, so **is there any way that someone outside my local network could actually even attempt to SSH into one of my machines?** Am I right in thinking that all they could 'speak' to would be the router, which they obviously can't SSH into? (It's a Linksys wireless router.)

If your router is configured properly, and there are no port forwards other than 80, then you are only vulnerable at 80. I would still take the time to get public key auth working.

---

