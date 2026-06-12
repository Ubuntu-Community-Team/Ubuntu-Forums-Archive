---
title: "ssh rsa pub key question"
date: 2006-07-01
forum: Desktop Environments
---

### Post by tefflox on 2006-07-01
I followed the directions to enable "passwordless login" for ssh, but after setting it up, it asks for my passphrase, which i enter as i would my password.  Are the password and passphrase entirely different, that is, only from my machine it asks for the passPhrase, right? So should I make my regular password eXtr3mely difficult?  

Now I know why stats.bls.gov reports higher earnings for sysadmins than programmers :-)

---

### Post by thasheep on 2006-07-01
I'm not sure who's directions you followed for passwordless login but as far as using ssh is concerned...
The passphrase is used to decrypt your dsa/rsa key when making a connection. If you created your key without one, you shouldn't be asked for it.
The password is just your regular password that you'd use to login at gdm or a virtual terminal.
To be secure, I'd recommend only allowing public key authorisation (dsa/rsa). Important things in /etc/ssh/sshd_config are:
```
Protocol 2
PermitRootLogin no
RSAAuthentication yes
PubkeyAuthentication yes
PasswordAuthentication no

```RSAAuthentication refers to using RSA keys, PubkeyAuthentication refers to DSA keys. You only need to enable one of these but can do both. PasswordAuthentication is your normal password.

---

### Post by Dubbayoo on 2006-07-01
[QUOTE=thasheep]I'm not sure who's directions you followed for passwordless login but as far as using ssh is concerned...
The passphrase is used to decrypt your dsa/rsa key when making a connection. If you created your key without one, you shouldn't be asked for it.
The password is just your regular password that you'd use to login at gdm or a virtual terminal.
[/QUOTE]

Just to clarify your passphrase password has nothing to do with your login password. They can be the same or different. The passphrase is just an extra level of protection. It is optional. I use it on computers facing the internet only.

---

### Post by thasheep on 2006-07-02
Ahh I see. Sorry, I thought you wanted to set up an ssh server on your computer so I was looking at the problem from the other way around. The idea of using public/private keys is that you keep your private key and don't give it to anyone. The public key goes on any server (in ~/.ssh/authorized_keys is it's a *nix server) to which you want to use the key to login. When you try to log in, the ssh client (you) and ssh server use these keys and some maths to identify that your are authorized without having to send your private key.

You create an rsa public/private key pair by doing 'ssh-keygen -t rsa'. If you don't enter a passphrase (just hit enter) then once set up, you will be able to log in without entering any password/passphrase. The default location for your keys is ~/.ssh/id_rsa.pub (public) and ~/.ssh/id_rsa (private).

The public key, id_rsa.pub, needs to be copied/appended (more than one public key can be there) to ~/.ssh/authorized_keys on the server. You shouldn't need to change the permissions of any files. By default, your private key (only on your computer) can only be read by you. All other files are not secret and stopping other uses from reading (eg chmod 600) them could cause problems because sshd, the server programme, needs to be able to read authorized_keys. Perhaps this is why you're being asked for a password when you log in because sshd can't read authorized_keys.

Now, about whether you will only be able to log in like this from your computer... If you trust the root user of other (client) computers, you can create a new key from them and then append it to authorized_keys on the server. Alternatively, you could keep a copy of your private key, id_rsa, somewhere on a removable disk and to log in do, 'ssh -i /media/mydisk/somewhere/id_rsa [email]username@server.com[/email]'

---

