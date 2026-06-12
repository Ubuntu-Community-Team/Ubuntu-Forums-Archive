---
title: "Dapper remote access via command prompt"
date: 2007-06-16
forum: Desktop Environments
---

### Post by theQmaster on 2007-06-16
Hi, 

I want to connect using VNC to either kde or gnome - both installed on this remote box that I can access with putty. The thing is it has no keyboard and nor a monitor attached to it so it's a must to enable my remote via sudo command.

My default display manager is kde. How do I switch back and forth between them ?
Then how do I enable remote desktoping using a command line ?

Any ideas will be highly appreciated!
Q

---

### Post by thelinuxguy on 2007-06-16
I haven't used putty but I gather that it uses ssh.

This should work with Gnome.
Log into your server with X11 forwarding enabled:
```

ssh -XC serverip

```

For logging in with a different username, use the -l switch.

Once you are in, you should be able to turn on remote desktop with
```

vino-preferences

```

---

### Post by theQmaster on 2007-06-19
That didn;t work. I've moved my 40 pounds monitor and it manage to do it all - it seems that you need to have a monitor to do the the migration. And enabling the remote access via the putty is not possible.
:popcorn:

> **thelinuxguy said:**
> I haven't used putty but I gather that it uses ssh.

This should work with Gnome.
Log into your server with X11 forwarding enabled:
```

ssh -XC serverip

```

For logging in with a different username, use the -l switch.

Once you are in, you should be able to turn on remote desktop with
```

vino-preferences

```

---

