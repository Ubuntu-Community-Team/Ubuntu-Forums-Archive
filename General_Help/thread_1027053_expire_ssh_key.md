---
title: "expire ssh key"
date: 2008-12-31
forum: General Help
---

### Post by Lary Grant on 2008-12-31
I use ssh to connect to a remote site.  When I first connect a dialog pops up asking for the passphrase, but from then on it connects with no dialog.  That's fine, but I would like it to expire eventually.  As it is, even days later, I don't need to give the password, until I log out or reboot.   How do I set an expiration?

---

### Post by RealPSL on 2008-12-31
The first time you connect you get a question asking you to accept the remote servers private key. You should also have to enter the pass phrase for your private key. The pass phrase for your private key should be requested every time you connect not just the first time. If you did not set a pass phrase for your private key you can use ```
ssh-keygen -P
```

---

### Post by Lary Grant on 2009-01-01
> **RealPSL said:**
> The first time you connect you get a question asking you to accept the remote servers private key. You should also have to enter the pass phrase for your private key. The pass phrase for your private key should be requested every time you connect not just the first time. If you did not set a pass phrase for your private key you can use ```
ssh-keygen -P
```

No, it only asks me once.  It pops up a dialog, even if I run ssh from the shell.  It's clearly caching the key in memory.  I don't mind it doing that, but I just want it to be able to set an expiration time, e.g. 1 hour.

---

### Post by Lary Grant on 2009-01-02
bump

---

### Post by bgerlich on 2009-01-02
The RSA key is not cached, the RSA key fingerprint is stored in ~/.ssh/known_hosts . If you feel like it - you can delete the file, you can delete a single entry using ssh-keygen -R hostname . There is no point in doing that through, the fingerprints stored on local machine is of little security risk to your connection.

---

### Post by bgerlich on 2009-01-02
The RSA key is not cached, the RSA key fingerprint is stored in ~/.ssh/known_hosts . If you feel like it - you can delete the file, you can delete a single entry using ssh-keygen -R hostname . There is no point in doing that through, the fingerprints stored on local machine is of little security risk to your connection.

Oh and removing the entries or the whole file actually decreases security.

---

### Post by RealPSL on 2009-01-04
Can you provide the text of one of your connections so we can see the interaction or a screen shot if you find that easier? I read the man pages for ssh-keygen which creates and manages the keys and there does not seem to be an expiration. 

However, the behavior you are having can be achieved if you are using ssh-agent then expiring the key would be as simple as using the -t option to expire the key at an interval you feel is appropriate.

---

### Post by Lary Grant on 2009-01-04
> **RealPSL said:**
> Can you provide the text of one of your connections so we can see the interaction or a screen shot if you find that easier? I read the man pages for ssh-keygen which creates and manages the keys and there does not seem to be an expiration. 

However, the behavior you are having can be achieved if you are using ssh-agent then expiring the key would be as simple as using the -t option to expire the key at an interval you feel is appropriate.

The dialog says:
Enter password to unlock the private key.  An application wants access to the private key 'id_rsa', but it is locked.

This dialog may be using ssh-agent in the background, but I am not doing any ssh-agent command manually, so there is no way I can give any -t option.  I just want the dialog to come up as it is, but I want the key to expire.

---

### Post by Lary Grant on 2009-01-05
Maybe this dialog comes from Seahorse?  But if I go into Seahorse I don't find any way to control the expiration.

---

### Post by ooobooontooo on 2009-05-29
I have the same problem. I would like to know how to control it...I'm pretty sure this isn't coming from the ssh side, but rather the gnome/seahorse side. Any help?

---

### Post by ooobooontooo on 2009-06-03
bump

---

### Post by ooobooontooo on 2009-06-06
bump

---

### Post by Lary Grant on 2009-06-07
I'm also still suffering with this!!

---

### Post by ooobooontooo on 2009-06-21
any leads on this?

---

### Post by garvint on 2010-09-14
has this been solved yet as I have the same problem, I thought the whole point of the key is so you don't have to enter a password, but you do!

---

