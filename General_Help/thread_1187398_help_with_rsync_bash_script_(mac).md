---
title: "help with rsync bash script (mac)"
date: 2009-06-14
forum: General Help
---

### Post by Mykle87 on 2009-06-14
I am following [this guide]("http://74.125.47.132/search?q=cache:PXzU9VHNxVcJ:www.petefreitag.com/item/549.cfm+backup+over+ssh&cd=1&hl=en&ct=clnk&gl=us&client=firefox-a") to backup my sister's macbook to my ssh ubuntu server. I want to automate this with cron. The script prompts for a password to the ssh server which is expected. I would like to have the script send the password. I know I can use RSA keys for passwordless ssh but I have many users and I do not want to give keys out every time someone needs access to my server. Is there a way to add the password to the script so that it is truly automatic?

---

### Post by alinef on 2009-06-14
You could make a DSA or RSA key only for your backups and the password method will still works. This is the default behavior for most ssh servers.

---

### Post by Mykle87 on 2009-06-14
> **alinef said:**
> You could make a DSA or RSA key only for your backups and the password method will still works. This is the default behavior for most ssh servers.

Could you elaborate? My understanding is once you create a RSA key and disable passwords, you have to use that key pairing for every user of the ssh server.

---

### Post by alinef on 2009-06-14
Here is some options from a sample /etc/ssh/sshd_config

```

RSAAuthentication yes
PubkeyAuthentication yes

PasswordAuthentication yes

```

When you log in into a server with this configuration you get:

```

debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Offering public key: /home/aline/.ssh/id_dsa
debug1: Authentications that can continue: publickey,password

```

/home/aline/.ssh/id_dsa is my key. First it offers my key. If it can't authenticate with it, then it pass to the next method, which is password. 

If I hadn't any key, it would just prompt me for the password. 

Use ssh -v user@server (the -v option) to see what is happening.

---

### Post by Mykle87 on 2009-06-14
Interesting. If I wanted multiple users to use this script, could I just copy the public key or should I make a new set of keys?

---

### Post by alinef on 2009-06-14
> **Mykle87 said:**
> Interesting. If I wanted multiple users to use this script, could I just copy the public key or should I make a new set of keys?

openssh works with both ways, but if you care about security, it may be good if you create each key for each user.

I have an account in a host service shared with 15 people. In order to have some control about who have access, I ask them to generate a dsa key in their macs:

```

ssh-keygen 

```

So they give me their id_dsa.pub. So I send this to the server account like this:

```

scp id_dsa.pub user@remotehost:.
ssh user@remotehost
cat id_dsa.pub >> .ssh/authorized_keys

```

And I do this for each user who wants to have access to this account. If I need to cut access to one of them I just need to edit .ssh/authorized_keys in the remote host and delete the key line of the user that I want to delete.

---

### Post by Mykle87 on 2009-06-14
Ok this sounds simple enough. Do you have to change the file permissions of the .pub file they give you or is it correct as is? Also, how do you know which key is associated to which user in .ssh/authorized_keys? Do you make them add -C "Their Name" to ssh-keygen?

---

### Post by Mykle87 on 2009-06-15
> **alinef said:**
> 
```

scp id_dsa.pub user@remotehost:.
ssh user@remotehost
cat id_dsa.pub >> .ssh/authorized_keys

```

I think I misunderstood. Do the authorized keys live in /home/user/.ssh/authorized_keys?

---

