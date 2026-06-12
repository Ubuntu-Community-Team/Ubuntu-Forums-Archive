---
title: "Strange file ordering by nautilus, sort, ls -l, considering LC_COLLATE value"
date: 2010-10-04
forum: Desktop Environments
---

### Post by olivier.cailloux on 2010-10-04
Hello,

I observe a strange Nautilus behavior when asking it to sort files by filename. Searching for it I saw that the matter had already been discussed quite a lot (see e.g. [https://bugzilla.gnome.org/show_bug.cgi?id=458707](https://bugzilla.gnome.org/show_bug.cgi?id=458707)). But there doesn't seem to be a consensus about where the problem is (or even if there is a problem at all).

So I did a few tests in a folder where I had created a few files named appropriately, trying to shed a bit of light on the matter. I tested LC_COLLATE=C (or POSIX), and LC_COLLATE="fr_FR.UTF-8" (the default on my system). I compared the order displayed by Nautilus with the output order of "sort" and "ls -l". The result is quite surprizing as you may see in the tables in the attached file (I'm sorry but apparently this forum does not accept tables, hence I could not typeset these in this post).

Basically it seems that
1) ls -l, sort and Nautilus all display the files according to an ordering that depends on LC_COLLATE. (That is expected.)
2) ls -l, sort and Nautilus all use different orders for both LC_COLLATE=C and LC_COLLATE="fr_FR.UTF-8". (That is much more unexpected.)
3) Nautilus' ordering for French can, it seems to me, be considered unreasonable, with 0aa being ordered after 000 and before 001. Bug or feature, that is the question.
4) ls -l uses an ordering compatible with the ASCII ordering for LC_COLLATE=C, the others two do not. The standard says, if I'm not mistaken, that LC_COLLATE=C should respect the ASCII ordering.
5) IMHO none of the orderings for the French LC_COLLATE value are fully satisfactory. This can be qualified as subjective, but I think that about all French speaker would agree.

The attached file includes these tables and a bit more details about how I built the tables.                   

If anybody has any idea about what's happening and where I should file bug reports (or where I could ask for more informations) I'd be very happy. Also is there a published (and accepted) standard about the ordering which should be used for a given LC_COLLATE?

---

### Post by toehser on 2010-10-19
Well, I think someone thought it was a "feature" to make "numeric" stuff work better:
3aa.txt
4aa.txt
20a.txt
assuming that they were "numbered" as 3,4,20.

Of course, if they are 3-digit numbers in base 16, you're screwed.

And, apparently, they didn't think the ability for Gnome to sort like, say, "ls" has FOREVER might matter to anyone... When they added this "feature"...

And, as far as I know, there is no option to turn on or off this "feature"...

---

### Post by toehser on 2010-10-19
But, see 355152 which is still open.

---

### Post by olivier.cailloux on 2010-10-20
Please note that the problem is not simply that Nautilus added a "feature" to sort in a different manner than the other ones. Also ls uses a different order than sort, and also ls order is not entirely appropriate (at least  as far as French locale is concerned).

---

