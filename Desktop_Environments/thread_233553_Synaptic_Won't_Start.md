---
title: "Synaptic Won't Start"
date: 2006-08-10
forum: Desktop Environments
---

### Post by kungfoofool on 2006-08-10
I'm having some problems with my update manager. In the taskbar, it tells me I have updates. When I click the icon, it briefly shows the "gear" icon for the package manager in the taskbar... then it disappears. If I run Synaptic through the menu, it does the same thing.

If I run apt-get install it says:
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

How can I figure out why Synaptic appears to be on the fritz?

---

### Post by missmoondog on 2006-08-10
i have a computer that does the same thing ocassionally with synaptic, but all the time with k3b. have a thread started somewhere on here about that, that hasn't ever been replied to (as of last check).

will subscribe to this thread just to see what you come up with. :-$

---

### Post by missmoondog on 2006-08-18
my problem was mainly with k3b, but sometimes synaptic too.

have fixed my problem. did a clean install of ubuntu and graveman. burner works correctly now.

wonder what the issue was using kubuntu on this computer? everything pretty much worked right out of the box with kubuntu on my 6 other machines.

---

### Post by WhO_KnOwS on 2006-08-18
[http://www.ubuntuforums.org/showthread.php?t=238668](http://www.ubuntuforums.org/showthread.php?t=238668)

```
sudo ln -s /usr/lib/libvte.so.9 /usr/lib/libvte.so.4
```

---

### Post by kungfoofool on 2006-08-18
I don't think that was the solution to my problem.

I fiddled around with things, and eventually resolved it. I'm pretty sure trick that finally fixed it was repairing damage done to the /etc/hosts file. I noticed when I was happily sudo'ing in terminal that I kept getting the following error...

```
sudo: unable to lookup ubuntu via gethostbyname()

```

That usually happens when my hostname "ubuntu" gets knocked off the line that resolves to 127.0.0.1 in /etc/hosts. I'm not sure WHAT program messes with my hosts file, but it does this occasionally.

So I made sure the following line was in /etc/hosts...

```
127.0.0.1 ubuntu
```

That fixed the sudo error message. I attempted to start up synaptic, and then it asked me for the password as it normally should and everything seemed to start up fine.

- Brian

---

### Post by dweasel79 on 2006-08-18
I had the same issue.  Not sure if this will help but, I resently changed my hostname and in doing so I must have broke something so I changed it back and now all works fine.  Hope this may be of help.

---

