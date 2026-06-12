---
title: "Gnome connect with SSH and Public Keys"
date: 2008-09-15
forum: Desktop Environments
---

### Post by KDB9000 on 2008-09-15
I am trying to connect to a server that has SSH on it, but I need to use my public keys to access the server. Is there a was to get the Gnome Server connect to use my public keys to connect to the server or do I need to look at another way?

---

### Post by iponeverything on 2008-09-15
you can -
just make sure that public key is in the .ssh/authorized_keys file of your account on the remote server and that your private key is in .ssh/id_rsa.pub (or dsa depending what type of key) on the local machine. and that the perms are correct for files (not permissive)

---

### Post by KDB9000 on 2008-09-16
No luck. I have RSA keys (the public and private one) and I tried both. They were made using the putty key gen tool. I have the key in the right place for the server, I know this because I used my key to login though ssh. I have used winscp to login to the system with the key.

I changed my public, then tried it with the private, is_rsa.pub and it still won't connect. Any other thoughts?

---

### Post by KDB9000 on 2008-09-17
Bump?

---

### Post by KDB9000 on 2008-09-21
Anyone? It should be possible.

---

### Post by KDB9000 on 2008-10-07
Turns out that the putty key gen system doesn't work with OpenSSH. I generated OpenSSH keys and then converted a copy to putty and everything is happy now.

---

