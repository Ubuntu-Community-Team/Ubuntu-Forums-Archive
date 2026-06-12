---
title: "ssh error message"
date: 2006-02-23
forum: Desktop Environments
---

### Post by GabrielWolff on 2006-02-23
When trying to connect to some remoted computer using ssh it says: 
```
Nautilus cannot display "ssh://pfabrikant@192.XXX.2.101 Please select another viewer and try again.".
```

When trying it in the terminal, at says: 
```

gabriel@ubuntu:~$ ssh pfabrikant@192.XXX.2.101
ssh: connect to host 192.168.2.101 port 22: Connection timed out
gabriel@ubuntu:~$
```

The guy has installed an ssh-server, so it should work, ah?

Why doesn't it?
And what's a viewer?

G

---

### Post by jrib on 2006-02-23
make sure he hasn't blocked port 22 either through his router or iptables

---

### Post by GabrielWolff on 2006-02-23
[QUOTE=_jason]make sure he hasn't blocked port 22 either through his router or iptables[/QUOTE]

OK, let's assume he's a total newbe to computers in general. To confront him with difficult terms (like for example "router") would be rather unproductive. (and neither am I such a pro)

Should I choose a diferent port? Is that possible?

G

---

### Post by LordBug on 2006-02-23
You missed blanking out the "168" part once :)  (Not that it matters, I'll get to that)

You could change the port, but it would require editing a config file or two on the SSH server and plugging port information into your SSH client.

Seeing that you're using a 192.168 address tells me you 2 are both on the same side of your Internet connection... meaning in the same building/house/apartment.  A connection time out tells me his SSH server might not be running, or his firewall is black-holing your connection attempts.  Double check the server status with "sudo /etc/init.d/{ssh server name that I can't remember} status"  You'll want to "ls /etc/init.d" first to find the server name to fix my command.  You should see a message that it's running.  If you don't, replace "status" above with "start".

Now, if you two are NOT in the same building then we have a different problem.  192.168 addresses, like the one you're trying to use, are not routed across the Internet.  192.168 is reserved for private use.  It's why 95% of routers use addresses from it for their internal networks.  Instead, you'll need to connect to the external address his Internet connection has.  You'll have to find something to tell you what this address is (Google can help).  Try that address instead, and see what happens.

---

### Post by GabrielWolff on 2006-02-24
Thanx for your reply. 

We aren't in the same building, so I guess I had to find out his external address, which I promptly did. What came out is: 84.94.15.95 (hope it's safe to post that here. If it's not, please let me know so.)

Now, when opening Nautilus, pressing ctrl+L and entering ```
ssh://his_username@84.94.15.95
```, it says that it ```
"can't display his_username@84.94.15.95. Access was denied"
```

Well, I guessed something like that would happen. But hey, in no manual I found anything about how to permit or deny access.

What should I/he do?

Thanx
G

---

