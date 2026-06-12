---
title: "BIND9 and NetworkManager"
date: 2005-10-28
forum: Desktop Environments
---

### Post by CdtDelta on 2005-10-28
Hey all,
I installed the NetworkManager Applet on my new Ubuntu box, and for some reason in my Networking settings for any of my network interfaces it adds a 127.0.0.1 to the DNS servers (and usually it's the only one listed).  So it's not picking up the DNS servers on the network I'm on.  So basically I'm going in and removing the 127.0.0.1 entry and then adding in the ones for my network (again depending on where I'm plugging into).
Now I don't really want/need BIND9 running on my system, can I have it shut down and still use the NetworkManager Applet?  Or is there some other workaround where it doesn't go looking for the nameserver on the localhost?
The main crux of the problem is that I can't get out to the Internet until I remove the 127.0.0.1 entry, which is somewhat annoying.

Thanks ahead of time....

---

### Post by emax on 2005-11-19
[QUOTE=CdtDelta]Hey all,
I installed the NetworkManager Applet on my new Ubuntu box, and for some reason in my Networking settings for any of my network interfaces it adds a 127.0.0.1 to the DNS servers (and usually it's the only one listed).  So it's not picking up the DNS servers on the network I'm on.  So basically I'm going in and removing the 127.0.0.1 entry and then adding in the ones for my network (again depending on where I'm plugging into).
Now I don't really want/need BIND9 running on my system, can I have it shut down and still use the NetworkManager Applet?  Or is there some other workaround where it doesn't go looking for the nameserver on the localhost?
The main crux of the problem is that I can't get out to the Internet until I remove the 127.0.0.1 entry, which is somewhat annoying.

Thanks ahead of time....[/QUOTE]

Hi, I have a very similar problem.

My Network Settings seem to ignore whatever I put in the DNS settings and a cat of /etc/resolv.conf shows it pointing to 127.0.0.1 whatever I set.

bind9 is set to start in /etc/rc[345].d as S15bind9.

When my machine starts a ps -ef | grep bind9 shows the following:

```
bind      7384     1  0 21:24 ?        00:00:00 /usr/sbin/named -f -u bind -c /var/lib/NetworkManager/NetworkManager-named.conf
```

if I do a sudo /etc/init.d/bind9 start, DNS starts working just fine but it would be handy to get this to work without having to intervene on the command-line.

Any tips would be greatly received.  Is it possible to use nm-applet without running bind??  Seems a little overkill if you know some valid nameserver ip's.

---

### Post by shadow07 on 2005-12-27
I believe it does this because of some issues I have seen with updating (or rather not being able to update) resolv.conf.

But, I would like to know where the list of name servers are.  I have looked at named.conf and did not find anything listed there, nor with the included files.

---

