---
title: "ssh problem"
date: 2004-12-02
forum: Desktop Environments
---

### Post by mahern on 2004-12-02
when I try to ssh into my ubuntu box, i am getting 

    Local: Bad packet length 1349676916.

---

### Post by p!=f on 2004-12-02
[QUOTE=mahern]when I try to ssh into my ubuntu box, i am getting 

    Local: Bad packet length 1349676916.[/QUOTE]
Check your /etc/ssh/sshd_config (daemon side) for:
```

[~] > cat /etc/ssh/sshd_config | grep Protocol
Protocol 2

```
and the client part (the machine you connect from):
```

[~] > cat /etc/ssh/ssh_config | grep Protocol
#   Protocol 2,1

```
You have two choices:
1) Recommended - set up the client so it uses protocol version 2
2) Enable protocol version 1 on the server side

---

### Post by melonman on 2008-03-01
FYI, although it's not the best choice, if you DO want to enable ssh1 (I do because I have an old windows box I want to commandline CVS from) it goes something like:

**Create an rsa1 identity for the server.**
It already probably has an rsa2 and a dsa identity - in /etc/ssh/ but will have skipped the old way.

*I don't know the proper way to do this* if there is one, so I just ran
```
sudo ssh-keygen -t rsa1

```
and placed the resulting 'identity' and 'identity.pub' files into /etc/ssh/ssh_host_identity and /etc/ssh/ssh_host_identity.pub.

Then,** enable protocol 1**, as above, and also refer to your new identity files.

```
/etc/ssh/sshd_config
```
```

Protocol 2,1
# Host Key for protocol rsa1
HostKey /etc/ssh/ssh_host_identity

# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key

```

Almost done. **restart the ssh daemon**
```
sudo /etc/inid.d/ssh restart
```

Now you may be able to ssh in from other places using the older authentication. There's probably some things to be aware of, like the encryption will only take 3months to crack instead of the 35 years of heavier security levels ... I dunno.

see other tutorials on where to go from here to share your local public key as a remote authorized_key and thus enable password-less logons.

---

### Post by Oliver Sedlacek on 2008-03-07
Please ignore, problem solved. Cygwin does ssh2, but didn't work the first time I tried it!


~~~~~~~~~~~~~~~

I'm also getting "Bad packet length 1349676916", and it's now obvious to me that my Ubuntu (server) is using protocol 2 and my Windoze box (client) is using protocol 1. The recommended fix is to upgrade my client to one that uses protocol 2. Can anyone suggest a win32 ssh2 client?

---

