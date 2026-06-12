---
title: "Bug in Indicator sector of the gnome panel"
date: 2010-09-25
forum: Desktop Environments
---

### Post by Toxicbits on 2010-09-25
Hi everyone,

In the past one bug appereared to me several times (using 10.04 and 10.10, too) but I still cannot reproduce it in order to file it. After logging into Ubuntu or just while usnig Ubuntu a small gap appears at the indicator sector of the gnome panel. 
Did anyone else see this happening and can reproduce it? It's not a big thing but still it influences a smooth user expeience, in my opinion.

Toxicbits

---

### Post by ajgreeny on 2010-09-25
Two possibilities?

1.  The gap is there waiting for the tracker icon to appear, if you have tracker enabled.  I do and there is a similar gap in my panel until that tracker icon shows up, after about 45 secs, I think.

2.  Or it is there because the clock panel applet width varies slightly as the date changes from single digit dates to double digit dates.  I wonder if that may occur if you have locked your applets positions when there was a wider clock applet showing from a double digit date.

I'm not sure how you could test these theories, but just throw them out for consideration.

---

