---
title: "Dell OMSA 6.4 does not detect PERC 4 controller"
date: 2011-03-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rpm161 on 2011-03-03
I recently upgraded a couple Dell PowerEdge 29xx servers to 10.04 LTS x64 and installed the recently-released (Jan 2011) Dell Open Manage Server Administrator (OMSA) 6.4 using the instructions found here: [http://linux.dell.com/repo/community/deb/OMSA_6.4/]("http://linux.dell.com/repo/community/deb/OMSA_6.4/")

and applied a few bug fixes found here:
[http://en.community.dell.com/support-forums/servers/f/177/p/19350169/19815440.aspx]("http://en.community.dell.com/support-forums/servers/f/177/p/19350169/19815440.aspx")

but although the application installs and runs fine, it doesn't detect my PERC 4 controller cards.  I've done some googling and discovered that this isn't a new problem and that it's not limited to Ubuntu ([http://stevejenkins.com/blog/2011/01/no-controllers-found-fix-set-up-dell-omsa-6-4-32-bit-on-rhel-centos-5-5-64-bit/]("http://stevejenkins.com/blog/2011/01/no-controllers-found-fix-set-up-dell-omsa-6-4-32-bit-on-rhel-centos-5-5-64-bit/")). 

I uninstalled the 64-bit OMSA and installed the 32-bit version using the deb packages available on the Dell site linked above, since doing so in Centos seemed to fix the problem, but OMSA still didn't detect my PERC 4 controller cards.

Has anyone else experienced this problem and found a workaround?

---

### Post by cellulararrest on 2011-11-04
Did this ever get resolved? I'm having the same issue.

---

