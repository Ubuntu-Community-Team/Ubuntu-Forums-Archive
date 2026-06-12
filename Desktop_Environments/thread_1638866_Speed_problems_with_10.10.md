---
title: "Speed problems with 10.10"
date: 2010-12-06
forum: Desktop Environments
---

### Post by ingeva on 2010-12-06
I switched to 10.10 to see if it would be better than 9.10 or 10.04
Well, it was in some ways, but here's what I have trouble with:

FireFox and Thunderbird are incredibly slow. It seems like a DNS
problem, because once connection is established, it's OK - until
next time. Transfer time is normal, it's finding a site that takes
time. If I enter the IP of a site into the hosts file, access time is
normal.
I also use the Epiphany browser. All OK there. I haven't bothered
trying others (Opera, Chrome) but I suspect this to be a Mozilla
problem.

Thunderbird does not use the same storage area as the previous
version, and not the same format. I couldn't find any way to migrate
so I could keep my existing data.

OpenOffice 3.2 also needs a small eternity to start, and this is the
case EVERY time I open a document.

The speed problems MAY have a connection, I don't know.

I used Maverick 10.10 server version, with most other software
installed from a batch file.

---

### Post by ingeva on 2010-12-06
I purged my home directory and re-installed from scratch.
The first time I use FireFox it spends a long time finding sites,
but next time the speed is normal.
I guess my DNS server didn't work properly in 10.10 previously.
Running from 9.10 was no problem.

Thunderbird is now also very fast.

OpenOffice 3.2 is still extremely slow. It starts fast, though,
but spends a lot of time reading/converting documents.
However, I'll take that up in another thread after I've
investigated some more.

---

### Post by fatharraxman on 2010-12-06
I also observed that firefox is slower than google ch, I support your notion this is a firefox problem , but I would like to ask you was it faster in 10.04?

---

### Post by ingeva on 2010-12-07
> **fatharraxman said:**
> I also observed that firefox is slower than google ch, I support your notion this is a firefox problem , but I would like to ask you was it faster in 10.04?
I can't answer that because I couldn't use 10.04 at all. Mouse and keyboard are on wireless and 10.04 didn't support them.
What I CAN say is that it's faster on 9.10, which I also have on the computer.
With 10.10, FireFox is very much slower than Epiphany, which I also use, but that's for
one task that runs more or less continuously using the same server all the time. If I open it for other use it's significantly faster than FireFox. To me it looks like FireFox is clearing the DNS cache, but I'm not sure. If I didn't have so much on my hands I'd try to install Squid. Did that many years ago and it helped a lot when the net was slower, but it didn't seem to much sense now, except for this. However, first I'll see if it might help to increase the local cache size. I had set it very small to avoid problems with page updating.

---

