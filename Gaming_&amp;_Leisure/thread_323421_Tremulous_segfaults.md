---
title: "Tremulous segfaults"
date: 2006-12-22
forum: Gaming &amp; Leisure
---

### Post by jordanmthomas on 2006-12-22
As a note:  I am not running Ubuntu, but I thought maybe I could get some help regardless of that fact.

When I try to run tremulous (no matter if it is a binary release or if I compile it myself) I get the following error:
```

#Sound memory manager started
#Loading vm file vm/ui.qvm...
#...which has vmMagic VM_MAGIC_VER2
#Loading 1075 jump table targets
[COLOR="Red"]#Received signal 11, exiting...[/COLOR]
#----- CL_Shutdown -----
#Closing SDL audio device...
#SDL audio device shut down.
#RE_Shutdown( 1 )
#----------------------- 

```

Some other places where people have had this problem have suggested updating libsdl and glibc, and I have the most recent (I think) versions of these:
```
glibc:  2.5
libsdl:  1.2.11-r1

```

Yet another suggestion was to install an old client (tremulous.x86), which I did and it gives the same error.

Any ideas on what else I should try to do to get this straightened out?  
I have gone as far as to install Ubuntu on another partition just to play Tremulous, but I really like Gentoo a lot more.

The whole output in case it might be of any use.
[http://pastebin.com/843042](http://pastebin.com/843042)

---

### Post by thomasa93 on 2006-12-27
I have am having the exact same problem.  I have [COLOR="Red"]SCOURED[/COLOR] the Net but to no avail!

PLEASE HELP!!

---

### Post by jordanmthomas on 2007-01-06
Well I have been waiting a few weeks for a solution but I decided to try to fix it myself.
Surprisingly, it has started working again.  The only major change I have done in the last two weeks is to upgrade to kernel 2.6.19-gentoo-r4

---

