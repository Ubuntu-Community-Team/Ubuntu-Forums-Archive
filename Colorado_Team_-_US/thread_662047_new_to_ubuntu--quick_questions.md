---
title: "new to ubuntu--quick questions"
date: 2008-01-08
forum: Colorado Team - US
---

### Post by phrea84 on 2008-01-08
hi

i am new to this and am wanting to know a few things:

1.  can i make ubuntu server a proxy server?
2.  can i make ubuntu server a place where scanned files go on our all-in-one machines?

i look forward to learning as i go.

thanks!

jeff

---

### Post by BrandanLloyd on 2008-01-08
Hey Jeff,

Welcome to Ubuntu and to the CoLoCo forum.  There don't seem to be as many people in the group that check the forum as those that check the subscribe to the mailing list [1].  You may be able to find more help there or in irc on freenode [2].

As for your questions I'm sure that you can use Ubuntu as a web proxy server. You will probably want to look into SQUID[1].

I'm not 100% sure about using it as a repository for your scanned documents.  It may depend on your scanners.  If you only need to make is accessible as a windows file server than you want to look into configuring the server with SAMBA[2].

References
1. [https://lists.ubuntu.com/mailman/listinfo/Ubuntu-us-co](https://lists.ubuntu.com/mailman/listinfo/Ubuntu-us-co)
2. irc://irc.freenode.net/#ubuntu-us-co
3. [https://help.ubuntu.com/community/SquidGuard](https://help.ubuntu.com/community/SquidGuard)
4. [https://help.ubuntu.com/community/ComprehensiveSambaGuide](https://help.ubuntu.com/community/ComprehensiveSambaGuide)

---

### Post by Pangz on 2008-01-25
I also having problems or difficulty on install squid at ubuntu 7.1 desktop just to try.
I download the squid-2.6 manuall and install, just when I ./configure command error occur
Also I have try to get in terminal by sudo apt-get install squid, error occur by package error.
hope to help me with my concern.
Im totally new on linux (ubuntu)

---

