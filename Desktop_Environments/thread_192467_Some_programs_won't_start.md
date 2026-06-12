---
title: "Some programs won't start"
date: 2006-06-08
forum: Desktop Environments
---

### Post by Rondonjin on 2006-06-08
I have problems with at least three programs not starting. After a fresh install of Dapper I installed RealPlayer and Acrobat Reader 7 and plugin. RealPlayer would segfault and Acroread would immediately just return me to a prompt when run from a terminal. I also downloaded Firefox 1.5.0.4 from moz.org and that also segfaults. 

Yesterday I found there were a handful of updates, which I installed. Acroread now waits a while before returning me to a prompt and RealPlayer just hangs until  I kill it. Firefox 1.5.0.4 still segfaults.

Is there a cure for this or do I have to do the unthinkable and return to FC5, where they all work?

Wayne

---

### Post by Trab on 2006-06-08
why not just install firefox via synaptic?
have u tried reinstalling the programs?
are u using debs/synaptic, or from source?

---

### Post by taurus on 2006-06-08
Why don't you try to run those programs from a terminal so at least you can paste the error messages here.  Without the error messages, it's kind of hard to tell you what's wrong with those apps...

---

### Post by Rondonjin on 2006-06-08
[QUOTE=Trab]why not just install firefox via synaptic?
have u tried reinstalling the programs?
are u using debs/synaptic, or from source?[/QUOTE]

Because the new version of Firefox is not availble via Synaptic.

Everything else was installed via Synaptic, deinstalled, config files deleted from my home and reinstalled.

Wayne

---

### Post by Rondonjin on 2006-06-08
[QUOTE=taurus]Why don't you try to run those programs from a terminal so at least you can paste the error messages here.  Without the error messages, it's kind of hard to tell you what's wrong with those apps...[/QUOTE]

You obviously didn't read my post or you would have seen that I am running them from a terminal and there are no error messages, excpet for Firefox, which is a segfault, which I didn't save and I've removed that version of Firefox.

"Acroread returns me to the prompt and RealPlayer just hangs until I kill it"

RealPlayer used to segfault before I installed updates yesterday but doesn't now, it just hangs. I'd paste the old segfault message:

wayne@Merlin:~$ realplay
/usr/bin/realplay: line 75: 11791 Segmentation fault $REALPLAYBIN "$@"

Wayne

---

### Post by andresv on 2006-06-26
[QUOTE=Rondonjin]I have problems with at least three programs not starting. After a fresh install of Dapper I installed RealPlayer and Acrobat Reader 7 and plugin. RealPlayer would segfault and Acroread would immediately just return me to a prompt when run from a terminal. I also downloaded Firefox 1.5.0.4 from moz.org and that also segfaults. 

Yesterday I found there were a handful of updates, which I installed. Acroread now waits a while before returning me to a prompt and RealPlayer just hangs until  I kill it. Firefox 1.5.0.4 still segfaults.

Is there a cure for this or do I have to do the unthinkable and return to FC5, where they all work?

Wayne[/QUOTE]

I am having here *exactly* the same problem: after fresh install, RealPlayer segfaults and Acroread returns me to a prompt when run from a terminal (if run from the menu it just does not start).

I am beginning to have a suspicion that the language packages (in particular, Japanese) may have to do with this: Rodonjin says he writes from Tokyo, so I suspect he has installed the packages to type in katakana/hiragana/kanji. I also installed those packages here and see the same behavior.

Any thoughts?

Thanks,

Andrés Villaveces

---

### Post by andresv on 2006-06-26
I found a solution in an older post by zuoliang:

> You can add
GTK_IM_MODULE=xim
to the very beginning of the file acroread which can be found by
which acroread
Same methode works for realply

It seems to resolve the conflict between SCIM (the Japanese or Chinese input method) and, precisely, acroread and realplay!

At least on my system (fresh dapper), this now works.

---

### Post by watertraveller on 2008-04-19
I'm having the same problem with Mousepad and Thunar File Manager. The latter gives me a segfault and the former doesn't give me any error message at all. 

I would try adding GTK_IM_MODULE=xim to the files for those programs, but (I feel a little silly admitting this) I don't know how to open the files in a format I can read. When I do "which thunar" and "which mousepad", the files I find are not readable by a human being; probably they're in some other format that I'm not opening them in. [ETA: At first I had thought they must be binaries, but then people wouldn't be advising for others to edit them like that, would they?] Could someone give me advice on how to do this much at least?

---

