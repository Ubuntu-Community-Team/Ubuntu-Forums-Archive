---
title: "ubuntu for sun enterprise 450 ?"
date: 2008-12-31
forum: General Help
---

### Post by fred_kard on 2008-12-31
Hi all, straight to the point.
I have Enterprise 450, can I install ubuntu server on it ?
Thanks

---

### Post by ilrudie on 2008-12-31
I don't think Ubuntu is distributed for the sparc architecture.  Your best bet would probably be Debian.  It's similar to Ubuntu but with the goal of rock solid stability instead of cutting edge applications.  Get it [here]("http://www.debian.org/CD/http-ftp/#stable").

---

### Post by mips on 2009-01-02
> **ilrudie said:**
> I don't think Ubuntu is distributed for the sparc architecture. 


You think wrong. Ubuntu has been available on SPARC since 8.04 and before that as unofficial if I recall correctly.

Ubuntu 8.10 for Sparc can be found here, [http://cdimage.ubuntu.com/ports/releases/8.10/release/](http://cdimage.ubuntu.com/ports/releases/8.10/release/)

This post says it works on the E450, [http://ubuntuforums.org/showpost.php?p=2153249&postcount=3](http://ubuntuforums.org/showpost.php?p=2153249&postcount=3)


For Ubuntu ports to Apple Macintosh PPC, IBM OpenPower, HP PA-RISC PS3 & SPARC see, [http://cdimage.ubuntu.com/ports/releases/](http://cdimage.ubuntu.com/ports/releases/)

---

### Post by ilrudie on 2009-01-02
Hmmm... I was not aware of these ports at all.  I seem to remember an announcement about Ubuntu dropping support for ppc but it seems I'm wrong about that too.  Maybe it was just Canonical.

EDIT:
About Ports
- -----------

The Porting Team was born about a year ago, and it's made up only by volunteers,
motivated by love for Ubuntu and uncommon hardware.  Hence the criteria for
ports architectures is more about what those individuals decide than any
rational decision making process.
None of these new architectures are officially supported by the Ubuntu team.
If we can get a large enough user base, we may be able to change that.

While the ports share the same amazing set of software as the official Ubuntu
distribution, their feature set is not as complete yet.  In fact, you're much
more likely to see some rough edges as you use the ports.

-[Announcing The Ubuntu Ports Archive]("https://lists.ubuntu.com/archives/ubuntu-announce/2005-October/000040.html")
This is old (2005) so it may have changed.  It looks like the ports may not be as stable as the x86 and x86_64 releases.

---

### Post by mips on 2009-01-02
> **ilrudie said:**
> Hmmm... I was not aware of these ports at all.  I seem to remember an announcement about Ubuntu dropping support for ppc but it seems I'm wrong about that too.  Maybe it was just Canonical.


PPC used to be an official Canonical release. A while back Canonical with a lot of noise annouced support for the Sun Niagra processors and they made it seem official & SUN was onboard as well. Dunno what happened in the interim though.

Anyway, the ports are there for those wanting to try them out.

---

### Post by fred_kard on 2009-01-05
Thank you all for the response,
I'm downloading ubuntu 8.10 for sparc right know.

I,ve try to boot Sun Enterprise 450 UltraSPARC-II 400 MHz with ubuntu 8.04 sparc.

Boot is terminated with this error msg :
"Fast Data Access MMU Miss"

Should i try the 8.10 to correct this problem ?
Or debian ?

Thanks

---

