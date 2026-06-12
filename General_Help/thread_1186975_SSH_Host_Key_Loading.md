---
title: "SSH Host Key Loading"
date: 2009-06-14
forum: General Help
---

### Post by nexxus92 on 2009-06-14
When i started my ssh server with /etc/init.d/ssh start i get this back from the terminal:
Could not load host key: /etc/ssh/ssh_host_rsa_key
Could not load host key: /etc/ssh/ssh_host_dsa_key
                                                                         [ OK ]
Is this bad? If so, how do I fix this problem and why did this just happen all of the sudden?

I tried this command as root:  ssh-keygen -t rsa1 -f /etc/ssh/ssh_host_key -N ''
And now when i run /etc/init.d/ssh start as root it seems to work fine. Can someone explain this lol

---

### Post by Brandon Williams on 2009-06-14
In my install, I have ssh_host_dsa_key, ssh_host_rsa_key, and ssh_host_rsa1_key in /etc/ssh. All three are required if you want to support all three possible key types. If you only have an rsa1 key, then you will only be able to support SSHv1. Note that they key files (both the public and private halves) are expected to have 0600 permissions.

If it were me, I would do the following:
```
$ sudo aptitude purge openssh-server
$ sudo rm -Rf /etc/ssh
$ sudo aptitude install openssh-server
```

This should get you back to a fully-functional default installation. If you have a heavily customized sshd configuration, you might not want to do this, though, since it will be a pain to get your config back to where it was. If that's the case, start by checking the ownership and permissions of the existing keys and work from there.

---

### Post by ducksun43 on 2009-06-14
you either damaged/changed the key files itself or changed the path where they could be found. Anyways, there is no need to purge anything; just create a new keypair
[http://sunoano.name/ws/public_xhtml/ssh.html#creating_the_keypair](http://sunoano.name/ws/public_xhtml/ssh.html#creating_the_keypair)

---

