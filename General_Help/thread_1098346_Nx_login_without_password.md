---
title: "Nx login without password"
date: 2009-03-16
forum: General Help
---

### Post by schickb on 2009-03-16
I have No Machine's nxserver/node/client installed on my Ubuntu machine. All works perfectly when I login using nxclient on a Windows box, until I set my /etc/ssh/sshd_config to have

PasswordAuthentication no

With that set to 'no' I am no longer able to login using nxclient. Login in with a plain ssh client works fine, however. I don't actually see any way to give the nxclient a user's private key rather than a password. Is this even possible? Or am I forced to allow ssh PasswordAuthentication if I want to use Nx?

---

### Post by schickb on 2009-03-16
Just found my answer in the Nx docs. Not too happy about it:

> 4. NX Server Authentication

NX is configured by default to allow access for any system user, as long as the user provides valid credentials for the SSH login. Please note that SSH authentication without password is not supported.

---

