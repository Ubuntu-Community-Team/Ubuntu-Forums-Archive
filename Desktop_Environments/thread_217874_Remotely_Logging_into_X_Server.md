---
title: "Remotely Logging into X Server"
date: 2006-07-17
forum: Desktop Environments
---

### Post by J0s3ph on 2006-07-17
Hello

I'd like to configure my Ubuntu systems to allow remote X sessions. How would I do this and how would I then connect?

I'm well hardened to RDP, terminal services and various VNC ports on Windows, but I'd like to use some sort of X client to connect to the remote X server.

---

### Post by simonn on 2006-07-18
The easiest and most secure way I have found of doing this is to via ssh.

To set this up, on the server, edit /etc/ssh/sshd_config and set:

```

X11Fowarding yes

```

Restart ssh:

```

$ sudo /etc/init.d/ssh restart

```

To start up a remote X session X needs to be running on the client. Log into the server using:

```

$ ssh -Y [user@][server]

```

You can then run GUI applications.

If you want to run a gnome session remotely instart of the above, run:

```

$ ssh -Y [user@][server] gnome-session

```

Note: I have only tried this with an OSX client to a linux server, but it should be the same.

---

### Post by J0s3ph on 2006-07-18
Thanks simonn. The only thing I had to do different was install openssh-server.

---

### Post by theconley on 2006-07-21
Hmm...this didn't work for me.

Instead of giving me an error, the shell just hangs like the program is running but I don't see anything.

I can get this working from AIX to AIX machine (I say that just so I don't look like a newb).

Suggestions?

~Conley

---

### Post by mbirkis on 2006-11-06
Will this method work with aiglx/beryl on the server?

---

### Post by grimdestripador on 2007-07-31
```

X11Fowarding yes

```

Should be spelled
```

X11Forwarding yes

```


Just a minor error

---

### Post by akba0012 on 2007-11-10
quick question, how do i figure out what my server is called?... i know what user i am

---

