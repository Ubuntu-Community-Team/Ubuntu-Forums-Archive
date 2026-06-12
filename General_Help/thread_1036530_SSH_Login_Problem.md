---
title: "SSH Login Problem"
date: 2009-01-10
forum: General Help
---

### Post by Knuffle on 2009-01-10
I have set up SSH between my two computers and for security reasons I disabled password login because I would like to be able to log in from friend's computers too. The problem is that I always get this error when testing.
ssh mycomputer
Permission denied (publickey).

I have read the documentation and it seems to leave a gap about what to do after disabling password login. Thanks for the help.

---

### Post by whoop on 2009-01-10
I don't know which steps you took and which steps you didn't. But you need to create a public/private key pair on your friends computer and put the public key on your ssh server.

read RSA Key-Based SSH Logins: [https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

It also helps keeping your password login capability enabled until you set up your keys. Otherwise it's hard to get the public key in the .ssh folder of your server.

---

