---
title: "Public Lab Question"
date: 2011-10-15
forum: Education &amp; Science
---

### Post by royceb on 2011-10-15
Hello all,

I am up and coming new open source/linux advocate primarily as a result of my job.  I have been placed in charge of operating and maintaining 4 public computer labs. 

I am trying to replace our aged software in the labs with newer alternatives.  Our content filtering is an example of this. 

I am in need of a username/login system that keeps track of who logs in, when they login/out, and the work station they are at.

I have yet to find something that does this for me and could use a good push in the right direction.  Our labs all run Windows XP for the student terminals.  Any suggestions?

---

### Post by hsweet on 2011-10-16
Definitely check out LTSP.  It's worked really well for me and my college for 6+years now.  It's available in many flavors, inc [http://www.edubuntu.org/](http://www.edubuntu.org/) and part of the server version installation.

If you are not familiar with it, you need a server, switch and whatever lab computers.  They can be any old thing, but run really well as long as there is sufficient server resources.  Students log in on the now dumb terminals and that info is saved in the server log in /var/log.  Everything is one place so easy to back up
 
We dual-booted for awhile win/linux ( I can explain how if you need that) but now are totally linux ltsp.  There is Dans Guardian filter.  I never needed that.  I was using OpenDns along with some custom IPTABLES scripts to make a whitelist of websites in classes I needed more control.

+ all the great open source software for just about anything for free.

---

