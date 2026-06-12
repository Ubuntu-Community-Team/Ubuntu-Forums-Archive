---
title: "12 hour (am &amp; pm) in Orage"
date: 2007-05-28
forum: Desktop Environments
---

### Post by SpanishFranks on 2007-05-28
What is the value in the settings for Orage to set the time in 12 hour format and display 'am' or 'pm' appropriately?

Thanks

---

### Post by RedSquirrel on 2007-05-29
Have a look at the manpage for 'date'. In a terminal, run:

```
man date
```

You will see all of the formats you can use.

For something like 10:20 am, it would be:

```
%I:%M %P
```

If you want AM/PM instead of am/pm, then use %p instead.

---

### Post by SpanishFranks on 2007-05-29
thanks, worked a treat. I should have looked at date:oops:

---

### Post by RedSquirrel on 2007-05-30
> **SpanishFranks said:**
> thanks, worked a treat. I should have looked at date:oops:
No problem. Now you know where to look next time you want to try a new clock format. :)

I use:

```
%a %b %e, %I:%M %P
```

---

