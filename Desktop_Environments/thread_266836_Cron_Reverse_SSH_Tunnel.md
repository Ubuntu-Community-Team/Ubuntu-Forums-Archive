---
title: "Cron: Reverse SSH Tunnel"
date: 2006-09-27
forum: Desktop Environments
---

### Post by Prospero2006 on 2006-09-27
Ok all, 

My work computer is behind a firewall. I can reach home from work, but not work from home because of this firewall. 

```

ssh -R 8022:localhost:22 username@my.home.ip.address

```

This sets up an ssh tunnel when run from the command line nicely.
However, I want this command to execute either when the machine starts up 
or once every hour through cron. If you try adding this command to a cron script, you'll see that the ssh connection exits immediately. 

Anyone run reverse tunnels out there?

Thanks,
Pros

---

### Post by henriquemaia on 2006-09-27
I'm just intrigued, but don't you have to type your password everytime you connect? Isn't that what kills it when cron runs it?

---

### Post by Prospero2006 on 2006-09-28
Nope. I set up rsa authentication using the ssh-keygen 
program. No password required for ssh login from a standard shell.

Cron won't run that sucker right.  

I can't run it using nohup

I can't run it using the  & operator either. (This makes sense because once you stop a job it technically 'stops' running. I think.)

If I could run ssh with nohup, that would probably do the trick also.


Thanks, 
Pros

---

### Post by Miademora on 2006-09-28
I use [autossh]("http://www.harding.motd.ca/autossh/") in combination with screen for this task.

---

