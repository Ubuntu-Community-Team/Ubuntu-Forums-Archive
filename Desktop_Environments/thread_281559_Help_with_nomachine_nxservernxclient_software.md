---
title: "Help with nomachine nxserver/nxclient software"
date: 2006-10-21
forum: Desktop Environments
---

### Post by phlosipher on 2006-10-21
Hi All,

I am having trouble with nxserver/nxclient software from nomachine and could use some advice. The problem is that the fonts inside the nomachine windows appear with funny colors. I didnt have the problem 3 months ago, but something I have done (probably to the server machine) has caused the problems.

I am attaching a screen shot of the problem running nxclient (in this case from an ubuntu 6.06 machine) to log into the ubuntu 5.10 machine (running nxserver). See the wierd colors on all the fonts?

I try to keep both machine up to date, but cannot upgrade the 5.10 machine to 6.06/6.10 at this time because it is my production box
and I cannot afford any downtime on it.

I am running the most recent version of all the required nomachine software  as of oct 21. The client machine works perfectly when I log into the nomachine test machine, so I doubt that it is misconfigured.

I have messed around with anti-aliasing, and with installing versions of
the software that require the Xft libraries and version that do not. I cant
figure out what I have changed in my setup that has introduced this problem

Can anybody suggest a path forward?

Thanks

Phil

---

### Post by Macchi on 2006-11-02
This may not help to find a solution, but I have had similar problems with FreeNX.

Firstly, I have observed problems with the fonts when using older versions of FreeNX clients (nxclients), likewise with the nxclient on the 2X PXE/boot disk. The fonts look ugly.

Since a couple of days ago I have been experiencing two other problems on nxcliets running on Edgy. The first is a very strange font and theme for the nxlogin window, and the second was the inability of the latest client to login on previous versions of the server.

My unqualified guess is that the clients attemp to use fonts and or refer to libraries that are not available or have changed. Limited compatibility among versions of the server and clients for different distributions.
I hope to find a combination that works.

By the way, I have reinstalled my main desktop application server with Dapper 6.06.1 LTS but decided not to run Edgy 6.10 on it. Very moderate conservatism can be a good choice in some situations, thus I will rely on the long term support.

---

### Post by jon21 on 2007-01-31
I am having the exact same problem running nxclient on a Windows XP machine.  NXServer (free forever version) is running on my Ubuntu 6.1 server.

I had suspected that this had something to do with the recent Windows XP SP2 upgrade that does something to improve the font appearance throughout XP.  However if you are getting it on an Ubuntu client then that is not the problem.

I have just today uninstalled, downloaded, and re-installed both client and server sides.

Any help appreciated.

- Jon

---

