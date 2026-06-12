---
title: "Is there a desktop for the server edition?"
date: 2008-05-16
forum: Desktop Environments
---

### Post by grs on 2008-05-16
Is there a desktop/graphic enviroment for working ubuntu server? If not is it possable to program one - this is more than likely completely over my head!! but I'm interested to know all the same.

---

### Post by Holy Cheater on 2008-05-16
Server and Desktop have the same repository, so you are free to install graphic environment onto the server system.
```

sudo apt-get install ubuntu-desktop

```
This command is the fastest way. But this meta-package depends on some other things like audio system.

---

### Post by grs on 2008-05-16
I didn't think the standard desktop was setup to handel server software through a graphic interface.

---

### Post by americanLoki on 2008-05-16
I run a server using the server kernel with the ubuntu-desktop package installed. I run NFS, Samba, SSH, NX, GNUMP3d, and Webmin with no problems (all from the same box). I have been able to run all of this on the standard kernel before with no problems. I am not sure which server apps you may be running (or need to run) but you shouldn't have any problems running your apps with any of the desktop environments.

---

### Post by grs on 2008-05-17
There call be used without the termnial?

---

### Post by yoda2031 on 2008-05-17
I have run a Ubuntu webserver for my personal websites for some time and have never installed from a "Server" CD.  This is because the "server" is actually my desktop PC and I also use it for gaming (well, not any more...), coding, IM, IRC, Firefox and Thunderbird.  I did what you're asking in reverse, made a server out of a desktop PC but it is (as has been said) entirely possible to make a desktop PC out of a server.

If I were you I'd install the ubuntu-desktop package, and do some apt-cache searches for GUI components of your average server processes.  I know for a fact that there are GUI components of:
 - BIND
 - DHCP
 - Apache2 (httpd)

I hope this information is helpful.

One last thing to note - a server "can" be run entirely through a GUI, but I DO NOT recommend it.  I am always dipping in and out of xterms or consoles (I run a couple of game servers on consoles to keep them out of my way more than anything, whilst still allowing interaction in the rare event I need to interact with them).

---

### Post by roe_polak on 2008-05-18
You could also choose a lighter window manager such as Fluxbox or enlightenment. You will still be able to run any gui application, just with a lot less load on the cpu. This do however require some configuration and you won't be able to have any fancy desktop effects, i.e. Compiz Fusion cannot work with Fluxbox.

---

