---
title: "viewing remote printer queue"
date: 2008-01-31
forum: Desktop Environments
---

### Post by mathenge on 2008-01-31
I have access to remote printers via a print server. Is there a way to see the jobs that are currently in the queue?

---

### Post by Fraktyl on 2008-01-31
If the printers are set up on your system, just use the lpq command from a terminal.

If they're not, you can still use lpq, but you'll have to tell it which host to use.  Check the man pages for lpq.

---

### Post by mathenge on 2008-01-31
It's a HP Print server. I believe it behaves like a Windows print server since all Windows PCs can see it and view jobs using Windows print manager.

Typing:

lpq -h 192.168.0.50 -a -l

should display all printer status, but it doesn't In fact, I'm getting a "lpq: Unable to connect to server" error message.

Any additional ideas?

---

### Post by Fraktyl on 2008-01-31
Try adding the port.  I think HP jet direct cards use 9100.  So use the following:

```

lpq -h 192.168.0.50:9100 -a -l

```

If it's not a jetdirect card.  You'll probably have to figure out which port it's using.  nmap is a good program to see open ports on an ip address.

---

