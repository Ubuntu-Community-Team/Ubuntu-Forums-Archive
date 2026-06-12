---
title: "Running &quot;Worms United&quot; in WINE"
date: 2006-12-09
forum: Gaming &amp; Leisure
---

### Post by happy-and-lost on 2006-12-09
Dos anyone remember the "Strategy" game "Worms" from the days of Win3.1 and MSDOS? Well, I've never been able to get it running on a Win > 95, and I want to play it in Wine. I've never managed to get anything working in Wine before. Any tips?

This is what I've got so far...

```
jo@mithos:/media/cdrom$ wine INSTALL.EXE 
Warning: unprotecting memory to allow real-mode calls.
         NULL pointer accesses will no longer be caught.
Not enough memory on exec

jo@mithos:/media/cdrom$ 

```

---

### Post by slimdog360 on 2006-12-09
is it a dos game? If it is try dosbox.

 Otherwise maybe try the crossover office beta.

edit: I just saw the /media/cdrom part so Im guessing its not a dos game (but it still could be). Try taking the files off the cd and onto your hdd then run wine.

---

### Post by hikaricore on 2006-12-09
I'm a big fan of the series and I've never heard of United... here's a list of the known versions tested with wine:

[http://appdb.winehq.org/search.php?sSearchQuery=worms](http://appdb.winehq.org/search.php?sSearchQuery=worms)

---

### Post by Frem on 2006-12-09
Yes, it's a DOS game. You'll need to get DosBox setup, becuase Wine, Cedega, and Crossover won't do you any good.

hikaricore: Worms United wasn't actually a a worms game the way you're thinking of. It was a combo pack of both *Worms* and the Expansion set, *Worms Reinforcements*.

If you *still* can't get worms to run, I'd reccommend hunting for a copy of Worms Armaggeddon. It is, imho, the best of the 2D Worms games. Turorial on getting it working [here]("http://www.nanacide.com/wahelp/installguide-original4.php")

---

### Post by happy-and-lost on 2006-12-10
I'm struggling a bit with DOSbox, it doesn't like my DVORAK keyboard. Any suggestions?

---

### Post by Frem on 2006-12-18
You'll have to use some external utility. This page (1) lists something called Xkey. It's a program that you run from within DOSbox which looks like exactly what you need.

1. [http://www.dosgamesonline.com/index/utilities.html](http://www.dosgamesonline.com/index/utilities.html)

---

### Post by tomplast on 2006-12-18
> **happy-and-lost said:**
> Dos anyone remember the "Strategy" game "Worms" from the days of Win3.1 and MSDOS? Well, I've never been able to get it running on a Win > 95, and I want to play it in Wine. I've never managed to get anything working in Wine before. Any tips?

This is what I've got so far...

```
jo@mithos:/media/cdrom$ wine INSTALL.EXE 
Warning: unprotecting memory to allow real-mode calls.
         NULL pointer accesses will no longer be caught.
Not enough memory on exec

jo@mithos:/media/cdrom$ 

```

Doesn't it work if you just run it like dosbox INSTALL.EXE?

---

