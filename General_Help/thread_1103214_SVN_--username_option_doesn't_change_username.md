---
title: "SVN: --username option doesn't change username"
date: 2009-03-22
forum: General Help
---

### Post by InkyDinky on 2009-03-22
I have an svn repository on my lan at 192.168.0.3 and I listen on port 511 for ssh.
When I try to connect via another computer on the lan to the svn repository it seems that my --username option is ignored.
Here is what I'm getting.

nicky@nicky-desktop:~/Documents/puthesis-svn$ svn --username nicolae checkout svn+sshtunnel://192.168.0.3/home/nicolae/svn/puthesis
nicky@192.168.0.3's password: 
Permission denied, please try again.
nicky@192.168.0.3's password: 

sshtunnel is defined thusly:
### Section for configuring tunnel agents.
[tunnels]
sshtunnel=/usr/bin/ssh -p 511
### Configure svn protocol tunnel 

Is there some other option from the ssh command that isn't changing my username? 
I think I might need to change the username for the ssh as well.  How do I do that?  man ssh shows that I'd need to specify the address when specifying a different address for ssh.  How would I do this generically in the tunnel command?

Thanks 
Nick

---

### Post by lloyd_b on 2009-03-22
Try this one:```
svn --username nicolae checkout svn+sshtunnel://nicolae@192.168.0.3/home/nicolae/svn/puthesis
```This *should* provide the username "nicolae" to the ssh tunnel, rather than the default current user ("nicky").

Lloyd B.

---

### Post by InkyDinky on 2009-03-22
Woohooo!  That did it.  It works for me now.  
Thanks a ton.

---

