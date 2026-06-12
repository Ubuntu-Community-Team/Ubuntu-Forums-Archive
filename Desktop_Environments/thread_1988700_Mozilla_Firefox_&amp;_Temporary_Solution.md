---
title: "Mozilla Firefox &amp; Temporary Solution"
date: 2012-05-28
forum: Desktop Environments
---

### Post by UltimateCat on 2012-05-28
Hi!:)

Another member and I have the solution to the web browser not performing it's duty.  By that I mean Firefox opens but does not have the min/max or the X to close.  This command in the terminal worked for me but as soon as I went to another article on yahoo news I than lost all I did in the terminal.

In the past I would just restart.

```
metacity -- replace && compiz -- replace &

```

Any one have any further recommendations, solutions or other commands?

 After this command works at it's initial input but when the terminal is closed the command no longer works.

It's this a Ubuntu bug or a Firefox bug?

I'm having trouble determining which is the case-

Any advise and wisdom is greatly appreciated.
Thanks in advance

---

### Post by zombifier25 on 2012-05-28
> **UltimateCat said:**
> 
```
metacity -- replace && compiz -- replace &

```

That's a bad command IMO, since it effectively launches a WM - Metacity - only to close it and launch another - Compiz. When window borders disappears, there is a chance that Compiz's configuration is messed up somehow, and you should reset it.
```
gconftool --recursive-unset /apps/compiz-1
```

---

### Post by UltimateCat on 2012-05-29
Zombifier:

I wrote down the new code you advised me on.

I copied it and pasted it into my terminal and well...I didn't get any response at all.  The curser just continued to flash.

Just before writing to you the browser did it again....not sure why this keeps happening.....not sure how compiz could be messed up somehow-

Don't think it's my graphic's card because my desktop and GIMP are working fine-

  Can you think of anyway or any other command?

---

