---
title: "Echo a message on all terminals?"
date: 2008-12-29
forum: General Help
---

### Post by adcwoef on 2008-12-29
Hi

I want to make a script that prints/echos a message on all open terminals (virtual?) for all users. Like the *halt* does; a systewide message is printed.

How do I achieve this? Thanks!

---

### Post by guidop on 2008-12-29
Old Unix, not apple specific, but have you looked at the manual page for the wall command?

Try:

```
echo "This is a test." | wall
```

---

### Post by adcwoef on 2008-12-30
> **guidop said:**
> Old Unix, not apple specific, but have you looked at the manual page for the wall command?

Try:

```
echo "This is a test." | wall
```

Oh thanks! That's just what I was looking for

---

