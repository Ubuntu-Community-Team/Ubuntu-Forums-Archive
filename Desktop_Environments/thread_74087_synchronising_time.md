---
title: "synchronising time"
date: 2005-10-10
forum: Desktop Environments
---

### Post by websavages on 2005-10-10
Hello,

Is it possible to configure the ntp client on my computer to connect to any ntp server it can find rather than a specific one. The reason why I ask is that the corporate firewall i'm behind won't let me talk to ntp.ubuntulinux.org

So i was thinking is it possible for the client to ask the network if there are any ntp servers and then synchronise with them?

Cheers ws

---

### Post by HermanAB on 2005-10-10
Use the pool at ntp.org:
pool.ntp.org

That will provide a randomly assigned time server, to spread the load on the system.

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

### Post by mlomker on 2005-10-10
> So i was thinking is it possible for the client to ask the network if there are any ntp servers and then synchronise with them?


It won't automatically find one, but you could choose a different one by editing the /etc/default/ntpdate file.

---

### Post by websavages on 2005-10-10
that won't solve the problem, the firewall i'm behind prevents access to any external ntp servers. 

Cheers ws

---

### Post by Zwack on 2005-10-10
If you have an internal ntp server then modify /etc/default/ntpdate so that the line
NTPSERVERS="ntp.ubuntulinux.org"
is changed to your internal server.

If you don't have an internal ntp server then there is nothing you can reasonably do.

I hope that this helps,
   Z.

---

### Post by mlomker on 2005-10-11
[QUOTE=websavages]that won't solve the problem, the firewall i'm behind prevents access to any external ntp servers. 
[/QUOTE]

Then hit Ctrl-C and skip past that part of the bootup.  You can permanently remove ntpdate from your startup like this:

```

sudo update-rc.d -f ntpdate remove

```

---

