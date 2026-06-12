---
title: "Python question"
date: 2012-03-02
forum: Education &amp; Science
---

### Post by jeneverboy on 2012-03-02
I maybe want to give python a try. But this is remarkable:

```
>>> 0.26*2
0.52000000000000002

```

any thoughts on it?

---

### Post by diesch on 2012-03-02
That's nothing special to python but [a usual problem with floating point numbers](http://en.wikipedia.org/wiki/Floating_point#Accuracy_problems)

---

### Post by Aielyn on 2012-03-02
> **jeneverboy said:**
> I maybe want to give python a try. But this is remarkable:

```
>>> 0.26*2
0.52000000000000002

```

any thoughts on it?

It is, as diesch said, due to the way that floating point numbers are handled.

For more details, see this:

[http://docs.python.org/tutorial/floatingpoint.html](http://docs.python.org/tutorial/floatingpoint.html)

Also see this for the way to get around the problem:

[http://docs.python.org/library/decimal.html](http://docs.python.org/library/decimal.html)

---

### Post by jeneverboy on 2012-03-05
thanks, i guess i should have known that. ;)

---

