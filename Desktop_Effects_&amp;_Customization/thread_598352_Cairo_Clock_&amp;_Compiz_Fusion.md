---
title: "Cairo Clock &amp; Compiz Fusion"
date: 2007-10-31
forum: Desktop Effects &amp; Customization
---

### Post by _simon_ on 2007-10-31
Cairo Clock seems to be loading before compiz fusion, so because there isn't a compositing manager running at the time it tries to load, it gives me an error.

How do I get it to load AFTER compiz-fusion has loaded?

---

### Post by orange2k on 2007-10-31
Well, I load Cairo clock manually after Compiz is loaded, so I don`t have this problem.
But Cairo clock runs even without Compiz, so I`m not sure why you get this error...:confused:

---

### Post by _simon_ on 2007-10-31
Must be a new thing with 0.3.3.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=48587&d=1193840275[/IMG]

---

### Post by meindian523 on 2007-10-31
No such problem in 0.3.2.

---

### Post by meindian523 on 2007-10-31
maybe add in the sessions menu for startup,a launcher with the command

```
compiz --replace && cairo-clock
```

?:)Just off the top of my head.Can you try that please?

---

### Post by _simon_ on 2007-10-31
> **meindian523 said:**
> maybe add in the sessions menu for startup,a launcher with the command

```
compiz --replace && cairo-clock
```

?:)Just off the top of my head.Can you try that please?

Unfortunately the clock doesn't load when I try that.

---

### Post by meindian523 on 2007-10-31
> **_simon_ said:**
> Unfortunately the clock doesn't load when I try that.

well,I can't think up something better.Is the order of starting up of apps in the Sessions in the order in which they were created (or) in the order they are seen in?Anyone?

---

### Post by _simon_ on 2007-10-31
I tried putting the clock lower down the list in sessions under compiz but that makes no difference, so I guess the order has no impact on when they load.

---

### Post by meindian523 on 2007-10-31
suppose you delete the entries for both compiz and cairo clock,then recreate them with the order following:

1>compiz --replace

then 

2>cairo-clock

??

---

### Post by _simon_ on 2007-10-31
See my post above, if only it were that simple!

---

### Post by meindian523 on 2007-10-31
Oh,I was under the impression that entries could be moved above and below by dragging and dropping or by using buttons like [Move Up] or [Move Down].I stand corrected.:)

---

### Post by _simon_ on 2007-10-31
The only way to postiion them is alphabetically but I tried that and it didn't work.

---

### Post by meindian523 on 2007-10-31
hmmm,well I can't think anything more now.Best Of Luck and I hope you get someone else who can solve your problem.

---

### Post by _simon_ on 2007-10-31
Thanks for your help anyway :)

I guess what I need is a timed script of some sort.

---

### Post by meindian523 on 2007-11-01
> **_simon_ said:**
> Thanks for your help anyway :)

I guess what I need is a timed script of some sort.

maybe using the bash equivalent of a sleep() function in C would do the trick.

edit:There exists a sleep command in bash.It has nearly the same arguments as the sleep() function in C.After writing the script you could put a launcher for the script in your sessions menu.:)

---

