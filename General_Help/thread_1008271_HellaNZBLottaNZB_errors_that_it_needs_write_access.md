---
title: "HellaNZB/LottaNZB errors that it needs write access?"
date: 2008-12-11
forum: General Help
---

### Post by Lupusceleri on 2008-12-11
Heya,

I installed HellaNZB/LottaNZB from the repos (and Lotta from the .deb their website gave me).

HellaNZB - 0.13
LottaNZB - 0.3.1

Previously, it worked without a problem. But yesterday it, without anything to alert me, deleted the downloaded rar-parts. The result wasn't there, either.

So I decided to use synaptic and completely uninstall hellanzb and lottanzb. Then reinstall them.

However this only added another problem: it says it needs write access to directories (without specifying what directories) now.

Added a screenie.

Anyone's got a clue what's wrong?

Thanks, Lup.

PS: Running it with sudo from a terminal lets me open and use it, but.. it's not really smart to sudo every program out there, especially if it should work without sudo, is it?

---

### Post by Octagonal on 2008-12-11
I would change your password asap Lupusceleri.
Or remove the picture.
Or... maybe that's a post and I'm being an idiot.

---

### Post by Lupusceleri on 2008-12-11
> **Octagonal said:**
> I would change your password asap Lupusceleri.
Or remove the picture.
Or... maybe that's a post and I'm being an idiot.

Yeah, maybe it is in fact [a post](http://ubuntuforums.org/showthread.php?t=650832). ;)

---

### Post by Lupusceleri on 2008-12-11
So, any ideas what is wrong? :)

[size=1]disguised bump![/size]

---

### Post by Lantash on 2009-06-26
Hi Lupusceleri,

it's unlikely that you still have the problem but I'll try to answer you nonetheless. Another user had the same problem:

[https://answers.edge.launchpad.net/lottanzb/+question/73803](https://answers.edge.launchpad.net/lottanzb/+question/73803)

I guess removing the hidden config directories .lottanzb and probably also .hellanzb in your home directory and launching LottaNZB again (not using sudo!) should fix the problem. You may want to take a look at the more detailed description by following the link.

Regards,
Lantash

---

