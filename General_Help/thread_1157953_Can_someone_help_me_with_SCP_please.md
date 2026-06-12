---
title: "Can someone help me with SCP please?"
date: 2009-05-13
forum: General Help
---

### Post by The Switch Blade on 2009-05-13
Okay let us preface this with I have no idea what I am doing.

I'm on ubuntu. I just installed it over the weekend.

I need to connect to a machine with which I have an IP address and root. I need to transfer an 8gb file from that machine to mine.

Can someone walk me through this? I will be eternally grateful.

---

### Post by druhboruch on 2009-05-13
This howto is about backup PC, but it answers your question in detail.

[http://www.howtoforge.com/linux_backuppc_p4](http://www.howtoforge.com/linux_backuppc_p4)

---

### Post by The Switch Blade on 2009-05-13
Is "server1.example.com" the machine to which I connect?

---

### Post by druhboruch on 2009-05-13
Yes it is.
In this example files are being copied both ways.

```

scp ~/.ssh/id_rsa.pub root@192.168.0.100:/var/lib/backuppc/.ssh/client_id_rsa.pub

scp ~/.ssh/BackupPC_id_rsa.pub root@192.168.0.213:/root/.ssh/


```

It is almost like regular copy command...

---

### Post by HereInOz on 2009-05-13
Check out this tutorial.  It is a bit rambling, but after a couple of reads it begins to make sense.

[http://www.linuxtutorialblog.com/post/ssh-and-scp-howto-tips-tricks](http://www.linuxtutorialblog.com/post/ssh-and-scp-howto-tips-tricks)

With scp, make sure you get the colons right.

---

### Post by andrew.46 on 2009-05-13
Hi The Switch Blade,

> **The Switch Blade said:**
> I need to connect to a machine with which I have an IP address and root. I need to transfer an 8gb file from that machine to mine.

The syntax should be:

```
scp your_username@remote_address:my_8gb_file /some/local/directory 
```

Hope this helps!

Andrew

---

