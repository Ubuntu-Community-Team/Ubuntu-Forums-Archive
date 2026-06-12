---
title: "vino remote desktop localhost=ipv6??"
date: 2007-08-06
forum: Desktop Environments
---

### Post by tall-male on 2007-08-06
On a Feisty Gnome desktop I enabled Remote Desktop.  In order to improve security I enabled local_only in Gconf_Editor (Desktop -> gnome -> Remote_Access -> local_only)
This should make it possible to use remote Destop through localhost only (using a SSH tunnel). Safety first...!
However, vino-server now is listening to localhost only but ***only ipv6***...!

$ ps -ef | grep vino
wdh       5232     1  1 20:08 ?        00:00:00 /usr/lib/vino/vino-server --oaf-activate-iid=OAFIID:GNOME_RemoteDesktopServer --oaf-ior-fd=17

$ lsof -p 5232 -a -i TCP
COMMAND    PID USER   FD   TYPE DEVICE SIZE NODE NAME
vino-serv 5232  wdh   16u  **IPv6 ** 17228       TCP [::1]:5900 (LISTEN)

I can't connect to localhost using ipv4:

nmap -p5900 localhost

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-08-06 20:11 CEST
Interesting ports on localhost (127.0.0.1):
PORT     STATE  SERVICE
5900/tcp closed vnc

How to get vino-server using ipv4 on localhost? 
Disabling local_only makes it work OK, but I don't want to use eth0 for vino-server.

---

### Post by ruibernardo on 2007-08-09
I don't know about that, but if you don't use IPV6 for anything else, maybe you could blacklist the module and this would force vino to use IPV4.

To do this:

```
 sudo nano /etc/modprobe.d/blacklist
```and in the end of the file add:

```
 blacklist ipv6
```Save, exit nano and reboot. 

This should disable the use of IPV6.

If after blacklisting IPV6, your Firefox browser begins to be slower than before, go to the "about:config" page (write it as if it was a webpage) and seach "IPV6" on the filter. You should see

```
network.dns.disableIPv6                     false
```Turn it to [B]true.

[/B] This as been referenced as making Firefox quicker. Hope this works. :)

---

### Post by rumli on 2007-09-04
_On the server_

1. Turn on the local_only configuration flag:
```

gconftool --type boolean --set /desktop/gnome/remote_access/local_only true

```

_On the client_
1. Start an SSH session with port forwarding to [::1] (which is the IPv6 name for localhost):
```

ssh -fN -L 5901:[::1]:5900 server_hostname

```

2. Run vncviewer on local port 5901:
```

vncviewer localhost:1

```

That should work, and you'll have the extra security of limiting VNC access to SSH tunnels.

Until they fix the -via option to use IPv6, we're stuck with having to manually create the SSH tunnel rather than simply doing:
```

vncviewer -via server_hostname server_hostname:0

```

---

