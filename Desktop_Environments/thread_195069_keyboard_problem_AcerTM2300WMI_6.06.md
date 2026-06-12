---
title: "keyboard problem AcerTM2300WMI 6.06"
date: 2006-06-12
forum: Desktop Environments
---

### Post by k225yt on 2006-06-12
Hi, everybody,

I was happy with Breezy and found myself working primarily with it, not with XP. Thought upgrading to 6.06 would make things even better ... The most annoying thing I've got with Dappeeeeeer is theeeeeeee the strange behaviour of my keyboard: it seems to be less responsive now, and writing a simple text becomes a headache :-( . It either swallows several keypresses without oding (sorry, the previous word should read "producing") any ymbols or repetes symbols after single short keypress.   NO, NO, iiiit is clean!  No food or cofee. It works ok under XP.
     Another small "problem" : I used to have a virtual esktop bigger than my native 1280x800. A line in Xorg.conf gave me that in Breezy. After upgrading to 6.06 this feature doesn't work in KDE, but works in Gnome. The xrandr utility helps, but ...

Any ideas?

PS Sorry for typping errors. Not all of them are mine

---

### Post by jrobinson5 on 2006-06-12
Sorry for stating the obvious, but...

If Breezy works better for you than Dapper, why don't you just use Breezy?

---

### Post by k225yt on 2006-06-14
Well, no ideas? I was expecting that.
A bit more information I collected recently. The kb works fine with the 2.6.12-10-386; the problem only appears with 2.6.15-23-386 and -686 and only in KDE. Gnome seems more bugfree, but I'd like to use KDE. I would be satisfied with 2.6.12-10-386 if autodetection and mounting my USB drives worked (it did with the same kernel in Breezy with KDE from Dapper). 
Hey, Gurus, what would you suggest? Compile a custom kernel? Never tried, but going to. Fight autodetection and mounting with the old kernel? Reinstall KDE?

:?: :confused:

---

### Post by k225yt on 2006-06-14
Huuuuh. Spainnnnnn won 4:0. Recompiled 2.6.15-7 with Timer frequency
 --1000 Hz and a lot of other things (thx to Luca_Linux for howto)... Works faster, but   kb got even worse.:-x

---

### Post by bytey on 2006-06-14
I having exactley the same problem with kernel 2.6.15-23-386 running gnome.  It seems to be only with certain strokes for me ie to get a ¨ I have to press shift+ double tap 2 and, I have the same problem with getting a ´ character I need a double tap.

I´m running Dapper on a AMD 3500+, 2 gig DDR 400, Nvidia drivers for a 6800LE, and a ASUS motherboard.  Its a virgin install and I still getting the trouble.  I currently using the UK-English 104 with dead keys, layout.

Any suggestions?  It was running fine with Breezy, but I would rather stay with Dapper if I can get around this niggle.  As k225yt says its a very annoying problem :/

---

### Post by k225yt on 2006-06-16
Hi, friends,
Below are the results  of my kb tests on Dapper
(Acer laptop Travelmate 2303WLMi CeleronM 1.5GHz, 752Mb RAM):

fresh boot kde custom kernel 2.6.15-7-686
the quick brown fox jumps over the lazy dg
the quick brown fox jumps over the lazy dg
the quicbrown fox jumps over the lazy dog
the quick brown fox jum over the lazy do
the quick brooown fox jumps over the lazy dog

3 min later, Gnome
the quick brown fox jumps or the lazy dog
the quick brown fox jumps over the lazy dog
the quick brown fox jumpover the lazy dog
the quick brown fox jumps over the lazy dog
the quick brown fox jumps over the lazy dog
the quick brown fox jums over the lazy dog

3 min later, reboot with 2.6.15-23-686(original kernel from Ubuntu), kde
the quick brown fox jumps over the lazy dog
t quick brown fo jumps over the lazy dog
the quick brown fox jumps over the lazy dog
t quick brown fox jumps over the lazy dog
the quik brown fox jumps over the lazy dog
the quick rown fox jumppppover the lazy dog

3 min later, Gnome
the quk brown fox jumps over the lazy dog
the quick brown fox jumps over the lazy dog
the quick brown foxumps over the lazy dog
the quick brown fox jumps over the lazy dog
the quick brown fox jumps over the lazy dog
the quick brown fox jumps over the lazy dog
the quick brown fox jumps over the lazy dog

3 min later, boot with 2.6.12-10-386(original kernel from Breezy), kde
the quick brown fox jumps over the lazy dog
the quick brown fox jumps over the lazy dog
the quick brown fox jumps over the lazy dog
the quick brown fox jumps over the lazy dog
the quick brown fox jumps over the lazy dog
the quick brown fox jumps over the lazy dog
the quick brown fox jumps over the lazy dog
the quick brown fox jumps over the lazy dog

Smmary:
In Gnome kb works better, but not gooddd enough with 2.6.15.
In KDE - a total headache.

With 2.6.12-10-386 - no problm in either G or K

I don't like to go completely back to Breezy, but I'd like to use the Breezy's kernel in Dapper. The only thing that doesn't work with it is autodetection and mounting my USB drives (flash, HD). They changed the way this mechanism works. Who knows how to make it work in Dapper like it did in Breezy?

---

### Post by Wheazel on 2006-06-29
Got same problem aswell.
Unacceptable problem!

---

