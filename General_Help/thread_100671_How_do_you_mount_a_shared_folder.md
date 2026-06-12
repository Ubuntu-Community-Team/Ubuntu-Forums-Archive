---
title: "How do you mount a shared folder???"
date: 2005-12-08
forum: General Help
---

### Post by adduds on 2005-12-08
First of all I LOVE UBUNTU! Second I'm very new lol go easy on me lol.

I have a shared windows folder called Musick it is located in a folder named Adam Toews

I normally access it through alt+F2 smb://ADDESK

which shows me the folders Adam Toews Musick University (in nautilus)

Musick and University are both located within Adam Toews

and then double clicking it, but i can only play one song at a time???.....i.e. i cannot create a playlist, if i highlight them all it says "This will open X windows do you want to continue" X being the number of songs selected. I'm not entirely sure how to open the shared folder through Totem or Rhythmbox....

So i was wonderin' if their was a way to have it as a folder so i can access it and play all my music "at once"

---

### Post by Joe_CoT on 2005-12-08
[How to mount network folders on boot-up](http://ubuntuguide.org/#automountnetworkfolders)

you might want to check out xmms. much like winamp, it has a very simple playlist editor, and you can just drag files into it.

---

### Post by adduds on 2005-12-08
Hey both my firewalls are down.....and i followed that tutorial to a T! I have the screenshot to prove it lol. This is what happens

[ATTACH]4294[/ATTACH]

Ping Results:

```
adduds@adtop:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=127 time=1.42 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=127 time=1.35 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=127 time=1.38 ms
64 bytes from 192.168.0.1: icmp_seq=4 ttl=127 time=1.36 ms
64 bytes from 192.168.0.1: icmp_seq=5 ttl=127 time=1.52 ms

--- 192.168.0.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4002ms
rtt min/avg/max/mdev = 1.356/1.410/1.524/0.061 ms

```

---

