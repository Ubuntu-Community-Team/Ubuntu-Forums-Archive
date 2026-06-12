---
title: "Lubuntu 10.10 pcmanfm crashes on right clck"
date: 2010-08-15
forum: Desktop Environments
---

### Post by samigina on 2010-08-15
Hi, I have found a bug, pcmanfm sometimes crashes with any right click, on the desktop or on any pcman window. The kernel.log sows:

pcmanfm[1171]: segfault at 1 ip 00bd859b sp bfc189bc error 4 in libc-2.12.so[abc000+157000]

I have reported the [bug]("https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/617655").

---

### Post by phillw on 2010-08-16
Hi,

the loud scream you heard would have been the creator of pcmanfm :p
The bug is correctly registered and I'm sure he will be looking into it.

Thanks for taking the time to report it.

Regards,

Phill.

---

### Post by cmike on 2010-08-16
I have the same problem.

As Julien Lavergne wrote:
> 
I just realized the problem. This issue appears if you are using the
version of libfm in the Lubuntu PPA on Maverick. It's currently quite
unstable and I advise you to remove it and re-install the libfm in
official Maverick repository until we figure out why it's crashing.

I just removed the version on the PPA, I'll report back when it will be
stable enough to be tested. Sorry for this :(

Regards,
Julien Lavergne



**That work for me!!!**

---

### Post by RTrev on 2010-08-16
What versions do you have installed of libfm0 and libfm-gtk0?

Some of us who had added the Lubuntu PPA a while back have found that dropping back to the current repository version solved the crash problem.  The version numbers that currently work are 0.1.12-1ubuntu1.

If you have the two programs above showing up as local or obsolete, and with a different version number, ping me back and I'll give you a fairly simple fix.  At least it worked for me.

---

### Post by cmike on 2010-08-16
Everything was described in thread 'PCManFM crashes after right click on icon' on lubuntu-desktop mailing list on Launchpad, started with my message [https://lists.launchpad.net/lubuntu-desktop/msg02159.html](https://lists.launchpad.net/lubuntu-desktop/msg02159.html)

I've used PurgePPA.

---

### Post by phillw on 2010-08-17
And for those who go "purge ppa"????!!!!  It is a handy little tool, I wrote up a quick introduction to it at [ppa purge](https://wiki.ubuntu.com/Lubuntu/Developers#ppa-purge) There are some other notes for those testing the Lubuntu 10.10 system at [Lubuntu 10.10 Development](https://wiki.ubuntu.com/Lubuntu/Developers).

Regards,

Phill.

---

