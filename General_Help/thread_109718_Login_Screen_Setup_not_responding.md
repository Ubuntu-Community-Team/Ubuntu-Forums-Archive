---
title: "Login Screen Setup not responding"
date: 2005-12-29
forum: General Help
---

### Post by lurch2012 on 2005-12-29
I installed Ubuntu, then later decided to try Kubuntu-desktop. Most people would agree that it is relatively harmless to have both desktop environments, because you can simply choose the one you want. My problem is that ever since I installed the kubuntu-desktop (through synaptic), my splash and login screens are all kubuntu. I want to install some custom stuff from gnome art, but can't get the Login Screen Setup to respond. It asks for the password, and I enter it correctly...the window just thinks for a moment and disappears. So far I have re-installed gdm...uninstalled kubuntu-desktop...re-installed ubuntu-desktop...the only thing I haven't done is uninstall KDM, which I'm very hesitant to do...any ideas?

---

### Post by rjwood on 2005-12-29
from the logon screen-are you choosing a session?

Have you tried to reboot?

---

### Post by lurch2012 on 2005-12-29
[QUOTE=rjwood]from the logon screen-are you choosing a session?

Have you tried to reboot?[/QUOTE]

Yes and Yes (several times)

---

### Post by rjwood on 2005-12-29
I have read that there are problems with kde in synaptic. When I installed my kde I use v3.5. Instructions found here:
[http://www.kubuntu.org/]("http://www.kubuntu.org/")

BTW----love the username "lurch'

---

### Post by lurch2012 on 2005-12-29
[QUOTE=rjwood]I have read that there are problems with kde in synaptic. When I installed my kde I use v3.5. Instructions found here:
[http://www.kubuntu.org/]("http://www.kubuntu.org/")

BTW----love the username "lurch'[/QUOTE]

Thanks...I'll try that for now...The worst part is it is just the stupid login screen...It's just annoying and now I have something I have to figure out or I won't be able to sleep...

---

### Post by rjwood on 2005-12-29
[quote=lurch2012]Thanks...I'll try that for now...The worst part is it is just the stupid login screen...It's just annoying and now I have something I have to figure out or I won't be able to sleep...[/quote] 
I know what you mean.. Been there-done that!
Look at my eyes---can't you tell??

---

### Post by lurch2012 on 2005-12-29
Well, I fixed it...I had prepared myself for a clean install by backing up everything...I was browsing through another thread and it said to choose kdm as the default display manager by doing 

sudo dpkg-reconfigure kdm

Well, since it was obvious to me that mine was already set as kdm, I did

sudo dpkg-reconfigure gdm

I got a window that let me switch my default desktop manager...changed to GDM, rebooted and BAM!...it worked...Just for the record I don't think it matters if you put gdm or kdm in the terminal as it will give you the option when the window loads...I want to thank rj for helping me out on this...I hope it helps someone else...

---

### Post by Strike&gt;&gt; on 2006-01-02
It sure did man. i was having the same problem, and i was going nuts. thanx to this thread i was able to solve my problem. so thank you all.

---

### Post by FlaSheridn on 2006-09-26
> **lurch2012 said:**
> 
sudo dpkg-reconfigure kdm


Thanks from me, too; I was having this problem, plus an odder one:  The KDE environment failed to launch after a reboot (Kubuntu is my default), though the Kubuntu boot screen showed up, but eventually dropped me into a bare terminal.  (This started happening after I'd run out of memory due to a GCC bug.)  Oddly enough, using the above to switch the default window manager to gdm from kdm (not vice versa) allowed me to launch Kubuntu as usual.

---

