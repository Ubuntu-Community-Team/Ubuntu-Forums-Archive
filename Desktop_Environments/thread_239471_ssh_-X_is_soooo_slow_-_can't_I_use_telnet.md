---
title: "ssh -X is soooo slow - can't I use telnet?"
date: 2006-08-19
forum: Desktop Environments
---

### Post by xp_newbie on 2006-08-19
Before I switched to Ubuntu as my desktop OS, I used to use Exceed on Windows, **telnet** to another linux box - and display on my local client varios X based applications that help me do my work (one of them is Emacs).

I tried to do the same on my Ubuntu client, but instead of smoothly displaying Emacs on my screen, it outputs the message:

> emacs: Cannot connect to X server 192.168.0.3:0.
Check the DISPLAY environment variable or use `-d'.
Also use the `xhost' program to verify that it is set to permit
connections from your machine.

Well... both the DISPLAY env var and xhost are set proprely, but that doesn't help.

So I started researching the problem and discovered that if I use **ssh -X** instead of telnet, things work without me even needing to set $DISPLAY or xhost. That's great, but it is **too slow** to my taste. :( 

I understand the need for SSH over the Internet (security), but all I want to do is use Emacs on the remote server on my home LAN.

I then discovered the following article: [Displaying Remote X-Windows Applications]("http://www.vyvy.org/blogs/index.php/2005/06/23/displaying_remote_x_windows_applications").

Which instructs to modify /etc/X11/gdm/gdm.conf to:

> [security]
DisallowTCP=false


to allow X via telneting.

The problem however is that I am afraid that if I do that, I am actually exposing my Ubuntu client to security risk from the Intenet. (is this true?)

Is it possible to allow X by telnet (over TCP) on the LAN only, leaving the default security measures set by the Ubuntu installer in place (so that X over TCP is not allowed from the Internet)?

If so, how do I accomplish that?

Thanks!
Alex

---

### Post by stdragon on 2006-08-20
Probably the easiest way is to use a firewall to block X traffic to/from the internet. Iptables should work fine.

On the other hand, why is the forwarding slow over ssh? You can disable encryption if that is an issue.

---

### Post by xp_newbie on 2006-08-21
> **stdragon said:**
> Probably the easiest way is to use a firewall to block X traffic to/from the internet. Iptables should work fine.

Thanks. So I guess this cannot be accomplished locally in /etc/X11/gdm/gdm.conf?

> **stdragon said:**
> On the other hand, why is the forwarding slow over ssh? You can disable encryption if that is an issue.

I think SSH is slower than telnet because of the encryption. But if I disable encryption doesn't it defeat the purpose of SSH? If not, how do I disable encryption?

---

### Post by stdragon on 2006-08-21
If you're using ssh only on your lan then encryption isn't very important, plus you still get X forwarding. However, I just tried it and found that that Ubuntu's sshd does not allow it! You would have to recompile sshd with the "--with-none" option to allow no encryption.

I guess your best bet is using a firewall. Replace "eth0" with whatever your internet interface is (maybe ppp0).

iptables -A INPUT -p tcp -i eth0 --dport 6000:6009 -j DROP
iptables -A INPUT -p tcp -i eth0 --dport 7100 -j DROP

To save them so that they're permanent, you can type:

/etc/init.d/iptables save

Hope this helps!

---

