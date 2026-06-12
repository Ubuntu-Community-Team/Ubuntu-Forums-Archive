---
title: "LTSP: mixing old &amp; new machines"
date: 2012-02-17
forum: Desktop Environments
---

### Post by Yanomamo on 2012-02-17
Hello all,
just registered to this forum because I have a problem with LTSP and found no proper solution (using the most favourite search provider and a handful of buzzwords which kept me busy for the last 3 weeks...).

So here's the setup I'm playing with:
I have two diskless PCs that I want to use in an LTSP environment.
1) HP T5540
2) An old Neoware Thin-Client

On a "server" (just another PC) Lubuntu 11.10 is installed.

Here's the annoying part:
1) When booting the T5540 everything is fine. 
2) When booting the Neoware machine it throws up a message telling me that I should use a kernel that suits the machine's architecture.

Digging into this I found out that an Ubuntu 10.04 LTS works fine with the Neorware thingy (and also with the T5540) booting from a USB-CD drive. On the other hand I don't want to downgrade my "server" to 10.04 just in order to be able to boot both diskless stations.... Adding disks (and thus a locally installed OS) is also no option as I want to be able to centrally administer everything.

All of the above lead to the idea to install LTSP 4 in parallel to LTSP 5 (as described here: [http://sourceforge.net/apps/mediawiki/ltsp/index.php?title=Ltsp5SameServerLTSP42](http://sourceforge.net/apps/mediawiki/ltsp/index.php?title=Ltsp5SameServerLTSP42) )
Unfortunately the sources have gone leaving me unable to do that.

But thinking about this parallell installation: If this would have worked then I would have ended up having different environments that I have to manage individually. Is this correct?

Even I use Linux for several years now, I am not that experienced with Linux to know what CHROOT means and what to do then... (it is mentioned quite often in conjunction with LTSP...) What I would like to have is a simple management tool that simply let me:

[LIST]
[*]add additional architectures with a simple GUI
[*]add kernels and OS that fit even to my old PC
[*]add another diskless machine that has Mythbuntu instead of Lubuntu
[*]easily manage thin and fat clients and the software that should be available to them (without thinking too much)
[/LIST]

Breaking down everything to a simple (?) question:
Is there anything like a graphical user interface to easily administer LTSP?

Thank you in advance,
Yanomamo (Michael)

---

