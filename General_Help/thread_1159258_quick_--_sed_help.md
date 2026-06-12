---
title: "quick -- sed help"
date: 2009-05-14
forum: General Help
---

### Post by khm on 2009-05-14
Hi, I'm trying to filter std out with sed.  I want to delete all string that does not match a given set. An example of the type of set:
{"apple", "cat", [0-1000]}

So, with this example, I don't want to spit out anything from standard out, unless it matches the string "apple", the string "cat", or an integer from 0-1000.

I know I can filter out certain words by using
sed 's/word//g'

But I want to filter out ALL BUT certain words.

Is this possible?

---

### Post by Sunon on 2009-05-14
awk will do that...

awk '/apple|cat|[0-1000]/ {print $0}'

---

### Post by khm on 2009-05-14
> **Sunon said:**
> awk will do that...

awk '/apple|cat|[0-1000]/ {print $0}'

Okay, I tried that with this:
```
echo "cat blah apple foo 22 bar 1001" | awk '/apple|cat|[0-1000]/ {print $0}'
```

and it get:

```
cat blah apple foo 22 bar 1001
```

Any suggestions?

---

