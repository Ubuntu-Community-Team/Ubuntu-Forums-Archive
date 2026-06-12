---
title: "Problems with grub"
date: 2009-06-22
forum: General Help
---

### Post by NoctisCaelum on 2009-06-22
Before expose my problem I just want to say that I'm a ubuntu newbie :(

I installed kubuntu, but later I installed ubuntu hmm in a bad way.. I installed ubuntu over kubuntu partition.. let's say that I deleted the partition and created it again!

So.. the grub was still there, after rebooting the computer I could see that grub had every option two times (two ubuntu-generic; two ubuntu safemode), and windows offcourse (but only one of these one). I simple choosed ubuntu, and windows that I didn't got any error. But today.. when I tried to use **any key**.. I couldn't, when grub loads, I **cannot use any button** of my keyboard.. so I'm here asking for help.

Thanks.

[COLOR=Red]**EDIT:**[/COLOR] I used the Start Up Manager like sugested here [http://ubuntuforums.org/showthread.php?t=46558](http://ubuntuforums.org/showthread.php?t=46558) and I changed the time to load and then seted the loading time like It was before.. now I can use the keyboard.. but I still have those entries twice.. can anyone tell me if I can change it in /grub/...list ? without blowing up something.

---

### Post by ahndoruuu on 2009-06-22
Feel free. If one entry is for an outdated kernel or whatever and you are sure you don't need to boot into it, go ahead and remove its entry from /boot/grub/menu.lst, it won't break anything, it'll just leave you with a tidier menu ;) 

You can reference this thread if necessary:[URL="http://ubuntuforums.org/showthread.php?t=144025"]
http://ubuntuforums.org/showthread.php?t=144025[/URL]

---

### Post by NoctisCaelum on 2009-06-22
thanks for the help, I guess I should give it a try.
thanks :D

---

