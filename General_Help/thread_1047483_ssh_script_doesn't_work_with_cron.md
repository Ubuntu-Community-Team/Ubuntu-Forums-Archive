---
title: "ssh script doesn't work with cron"
date: 2009-01-22
forum: General Help
---

### Post by Lars Stokholm on 2009-01-22
I don't get this. I have a script:

```
#!/bin/sh
ssh server mv file.odt file.bak
scp /path/file.odt server:
```

When I run it manually it works fine, but when I run it with my crontab, I get this error from auth.log on the server:

```
sshd[PID]: error: PAM: authentication error for [user] from [hostname]
```

What gives?

---

### Post by sedawk on 2009-01-22
You can add the verbose flag "-v" and then compare the output
of the interactive version with the one from the script.
Check what differs. Using "-vv" is even more verbose and even
"-vvv" might give more output.

Typically, problems related to "cron" are triggered
by the minimalistic enviroment cron uses to execute jobs.

With ssh there are some things to take care about when running
from a script. Try option "-n" or give option "-o BatchMode=yes"
and "-o StrictHostKeyChecking=yes".

```

#!/bin/sh
SSHOPTS="-n -o BatchMode=yes -o StrictHostKeyChecking=yes"
/usr/bin/ssh -v $SSHOPTS mv file.odt file.bak >/var/tmp/debug_ssh.txt 2>&1
/usr/bin/scp $SSHOPTS /path/file.odt server:

```

---

### Post by lykwydchykyn on 2009-01-22
Are you authenticating using a key, or with a password?

---

### Post by Slim Odds on 2009-01-22
> **Lars Stokholm said:**
> When I run it manually it works fine, but when I run it with my crontab, I get this error from auth.log on the server:

What gives?

Typically, this is because the cron job is running as root, whereas when you run it manually, it's running as you.

---

### Post by lykwydchykyn on 2009-01-22
> **Slim Odds said:**
> Typically, this is because the cron job is running as root, whereas when you run it manually, it's running as you.

It will run as the user whose crontab it's being run from.  The original post says he's using his own crontab.

---

### Post by Lars Stokholm on 2009-01-22
> **sedawk said:**
> ```
#!/bin/sh
SSHOPTS="-n -o BatchMode=yes -o StrictHostKeyChecking=yes"
/usr/bin/ssh -v $SSHOPTS mv file.odt file.bak >/var/tmp/debug_ssh.txt 2>&1
/usr/bin/scp $SSHOPTS /path/file.odt server:

``````

debug1: Authentications that can continue: publickey,keyboard-interactive
debug1: Next authentication method: publickey
debug1: Trying private key: /home/lars/.ssh/identity
debug1: Trying private key: /home/lars/.ssh/id_rsa
debug1: Offering public key: /home/lars/.ssh/id_dsa
debug1: Server accepts key: pkalg ssh-dss blen 433
debug1: PEM_read_PrivateKey failed
debug1: read PEM private key done: type <unknown>
debug1: No more authentication methods to try.
Permission denied (publickey,keyboard-interactive).
```

> **lykwydchykyn said:**
> Are you authenticating using a key, or with a password?With a key.

> **Slim Odds said:**
> Typically, this is because the cron job is running as root, whereas when you run it manually, it's running as you.But not when I run 'crontab -e' as me, right?

---

### Post by Slim Odds on 2009-01-22
But not when I run 'crontab -e' as me, right?[/quote]

crontab also runs with a minimal environment. It does not load .profile or other scripts that an interactive shell would.

You normally have to put full paths on executable files etc.

---

### Post by lykwydchykyn on 2009-01-22
Seems like the ssh command in your revised script leaves out the server name; or else I'm missing something.

and yes, running crontab -e as yourself will put it in your crontab, and the jobs will run as your user.

---

### Post by Lars Stokholm on 2009-01-23
> **lykwydchykyn said:**
> Seems like the ssh command in your revised script leaves out the server name; or else I'm missing something.How do you see it's leaving out the name and is there anything I can do about it?

---

### Post by lykwydchykyn on 2009-01-23
This command:
```

/usr/bin/ssh -v $SSHOPTS mv file.odt file.bak >/var/tmp/debug_ssh.txt 2>&1

```
has no server name in it, unless I am mistaken.

---

### Post by Lars Stokholm on 2009-01-23
Oh, yeah. I misunderstood. Well my local version has a server name. :)

---

