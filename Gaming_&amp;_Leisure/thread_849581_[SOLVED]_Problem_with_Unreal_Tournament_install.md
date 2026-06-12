---
title: "[SOLVED] Problem with Unreal Tournament install"
date: 2008-07-04
forum: Gaming &amp; Leisure
---

### Post by CatKiller on 2008-07-04
I installed Unreal Tournament on my computer with few problems back when it was on Dapper. My other half's got a new computer which is running Hardy. When I try to run ut-install-436.run I get ```
Verifying archive integrity...tail: cannot open `+6' for reading: No such file or directory
Error in check sums 1237260170 2341625838
```

I understand that this is mostly because the script is really old (# This script was generated using Makeself 1.5.4), and so is making assumptions that are no longer valid. I recall having to change the awk lines to sed lines in the ut script after it was installed for similar reasons.

I don't know enough even to know if it's deprecated stuff in tail, cksum, sed, or something else entirely, that's being used.

Can anyone help me to isolate the problem, or even suggest a solution?

---

### Post by CatKiller on 2008-07-04
I managed to find something out. The makeself website has this to say: > Important note for recent GNU/Linux distributions: Archives created with Makeself prior to v2.1.2 were using an old syntax for the head and tail Unix commands that is being progressively obsoleted in their GNU forms. Therefore you may have problems uncompressing some of these archives. A workaround for this is to set the environment variable $_POSIX2_VERSION to enable the old syntax, i.e. :
```
export _POSIX2_VERSION=199209
```

On my machine, doing this got to the bad trap message that I understand is a solved problem. On my other half's, there was no change. So obviously my computer has something that my other half's lacks. But I have no idea what.

---

### Post by CatKiller on 2008-07-04
In the end, I copied the installation over the network using SSH. Sub-optimal at best. If anyone has any thoughts, they'd probably still be useful.

---

### Post by CatKiller on 2008-07-19
I've managed to find some more information. The version of makeself that the people that made these scripts were using used a deprecated syntax for **tail**. It should be *tail -n +number*. The POSIX2 declaration tells tail to use the old behaviour.

However, since I was running the scripts with **sudo**, so that they could install in /usr, running export as a normal user didn't really affect the running of the script. And *sudo export* doesn't work.

So in the end, I properly became root with **sudo su**, then ran the export line, then ran the script, and everything behaved as it should.

Hopefully this information will be helpful to someone.

---

