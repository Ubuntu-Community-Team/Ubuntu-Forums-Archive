---
title: "Problem while running synaptic"
date: 2006-08-20
forum: Desktop Environments
---

### Post by dolarsrg on 2006-08-20
Hi everyone!

When I try to run synaptic I got this message:

> $ synaptic
synaptic: error while loading shared libraries: libvte.so.4: cannot open shared object file: No such file or directory

Is there any way to fix this? I was updating Compiz and XGL using the update-manager when this happend...

Thanks a lot in advance :(

---

### Post by xinix on 2006-08-20
[try this tread]("http://www.compiz.net/topic-3191-can-run-synaptic")

Edit:  The solution offered in this thread is not really a good idea. abetter solution is posted further down this thread.

---

### Post by dolarsrg on 2006-08-20
Thanks a lot xinix!!

Sorry... I thought I was the only one and I didn't look for any solution in other post...

Sorry again ](*,)

---

### Post by nrayever on 2006-08-20
thanks a lot, now my problem is solved too!! :KS :KS

---

### Post by xinix on 2006-08-20
I let my system sit there broken for a while.  Hadn't quite narrowed it down to the source of the problem.  I had applied the updates at the same time I installed some other software.  You cleared up the cause for me. So thank you.

---

### Post by HanZo on 2006-08-20
I had this problem too... but I'm not sure I understood where this come from... could anybody give me a hint... I'd just like to know.

---

### Post by xinix on 2006-08-20
I'm guessing you are all using the compiz repos like I do.  I'm not completely clear what the deal is.  But, it seems that we shouldn't be using the ubuntu.compiz.net/xgl.compiz.info repos (at least for a while).  Something about bad packages and being out of sync.

It's been suggested that people should use these instead:
```
deb http://www.beerorkid.com/compiz dapper main
deb http://media.blutkind.org/xgl/ dapper main
```

I don't how accurate all of this really is.

There are hacked (for transparency) versions of gnome-terminal on the compiz repos.  I imagine that these require a modified version of the libvte packages which we were getting from a bad source.  If someone else knows more it would be great to hear it.

Maybe we should move the topic into a "compiz repo" thread.  I haven't followed the ubuntuforums compiz threads since I started going to compiz.net for that.  Maybe this repo thing is already being discussed.

---

### Post by xinix on 2006-08-20
this topic is also being discussed [here]("http://www.ubuntuforums.org/showthread.php?t=239238") as well.  It makes the good point that this fix is a hack and not a solution.

---

### Post by xinix on 2006-08-21
at the moment a better solution is to downgrade some stuff and wait for a proper fix to come out in updates.

this seems to be working for folk on the compiz forum:
```
sudo apt-get install --reinstall libvte4/dapper libvte-common/dapper
```

---

