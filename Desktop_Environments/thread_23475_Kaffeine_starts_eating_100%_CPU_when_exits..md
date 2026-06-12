---
title: "Kaffeine starts eating 100% CPU when exits."
date: 2005-04-02
forum: Desktop Environments
---

### Post by malte on 2005-04-02
Fresh Kubuntu installation, I just installed libdvdcss and w32codecs... anyone has the same problem?

---

### Post by meldroc on 2005-04-02
Yep, I've seen that behavior too - something gets stuck when Kaffeine exits, and it sits and spins its wheels until I do a kill -9.

---

### Post by getaceres on 2005-04-07
[QUOTE=meldroc]Yep, I've seen that behavior too - something gets stuck when Kaffeine exits, and it sits and spins its wheels until I do a kill -9.[/QUOTE]
 At least! I thought I was the only person having this bug.
I sent a bug report to the Debian maintainer when I was using Debian but it was closed due to nobody having the same issue.
So it happens to someone else. Good.
By the way, do you know about other video and dvd player for kde? I'll use it while this bug is resolved

---

### Post by silvio on 2005-04-08
[QUOTE=malte]Fresh Kubuntu installation, I just installed libdvdcss and w32codecs... anyone has the same problem?[/QUOTE]
same problem too.

---

### Post by Twelc on 2005-04-12
glad to see I'm not the only one with this problem :)
(fresh kubuntu - installed it yesterday).

Could it be possible to have a bash script that 
1) launch kaffeine
2) Kill kaffeine once we close it

---

### Post by dermotti on 2005-04-12
Yep i have the same thing, and this happens for every instrance of Kaffiene i open too.

---

### Post by josete on 2005-04-12
There's a bug opened for this (search for kaffeine in the bugzilla interface). The maintainer claims to have solved the problem and it will be ready for ubuntu3 version of kaffeine. Does anybody know when this new release will be out?

---

### Post by kal_zakath on 2005-04-12
I have the same problem too, really annoying, I hope a bugfix will be relased soon

---

### Post by windymiller on 2005-04-14
[QUOTE=kal_zakath]I have the same problem too, really annoying, I hope a bugfix will be relased soon[/QUOTE]
 I have the same problem, but don't have to do a kill -9, just a normal kill works for me.

KPlayer is another KDE movie player, which looks very similar, but uses mplayer behind the scenes instead of xine.  I head that there were problems with mplayer and (k)ubuntu, but haven't tried it myself.

---

### Post by getaceres on 2005-04-14
[QUOTE=windymiller]I have the same problem, but don't have to do a kill -9, just a normal kill works for me.

KPlayer is another KDE movie player, which looks very similar, but uses mplayer behind the scenes instead of xine.  I head that there were problems with mplayer and (k)ubuntu, but haven't tried it myself.[/QUOTE]
 MPlayer doesn't work for me so KPlayer won't work. Also I installed it but I don't see in it how to start a DVD.

---

