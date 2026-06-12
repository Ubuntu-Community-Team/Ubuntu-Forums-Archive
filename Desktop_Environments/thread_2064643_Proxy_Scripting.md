---
title: "Proxy Scripting"
date: 2012-09-29
forum: Desktop Environments
---

### Post by DanHorniblow on 2012-09-29
Hi

I often connect to an external server via ssh and setup a socks proxy on my machine and configure application to go through it.

I know very little about scripting but I assume it would be possible to do this with a script and save the script to the desktop.

The command I use is:

ssh -D 9999 [email]username@sshserver.com[/email] -p ssh_port_on_server

Thanks Dan

---

### Post by hictio on 2012-09-30
You can, for instance, place that line onto your ~/.bashrc file as an alias, like this:
```

alias proxy_conect='ssh -D 9999 username@sshserver.com -p ssh_port_on_server'

```

Therefore, you open a Terminal, and type:
```

proxy_connect ENTER

```

And It'll will execute the connection string.
Another option might be to add an entry onto your .ssh/config file... With the parameters to connect to the SSH server.

---

### Post by DanHorniblow on 2012-10-03
Thanks!! That has worked perfectly! :)

---

