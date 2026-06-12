---
title: "Extract a Substring from Grep?"
date: 2009-04-14
forum: General Help
---

### Post by codeseer on 2009-04-14
I have:

```

sensors -f | grep "Core 0"
Core 0:     +118.4°F  (high = +179.6°F, crit = +212.0°F)

```

How can I get just the "+118.4°F" part by piping the data further?

I think the regexp is "\+.*?F", but I have no clue how to use it to grab the first temperature (only). I've been reading through what I believe to be related posts on many forums that have 'cut', 'ack', 'awk' and 'sed', but I'm not making much sense of them and when I have forced away at it I get 'invalid reference', 'unterminated' and blanks.

---

### Post by Alekz_ on 2009-04-14
IF you output is ALWAYS the same format you can use this way:

sensors -f |grep "Core 0" |awk '{print $3}'

[]'s

Alekz_

---

### Post by codeseer on 2009-04-14
> **Alekz_ said:**
> IF you output is ALWAYS the same format you can use this way:

sensors -f |grep "Core 0" |awk '{print $3}'

[]'s

Alekz_

Well, isn't that just magical; It subdivides with a delimiter of <white space>. Thank you.

```

sensors -f | grep "Core 0" | awk '{print $3}'
+118.4°F

sensors -f | grep "Core 0" | awk '{print $3}'
+120.2°F

```

Is there a way to do it with regular expressions though? For those times where format might change or finer precision is required.

---

### Post by Alekz_ on 2009-04-14
Yeah! You can use `cut`! But I still prefer (in this case) to use `awk`

Take a look:

sensors -f |grep "Core 0" |cut -d: -f2 |cut -d"(" -f1

Just for you understand:
cut -d: -f2
Means that ":" is a delimiter and -f2 means that I want the second field

And we have the same for cut -d"(" -f1, where:
-d"(" means that the "(" is the delimiter and I want the first field

[]'s

Alekz_

---

### Post by codeseer on 2009-04-14
> **Alekz_ said:**
> Yeah! You can use `cut`! But I still prefer (in this case) to use `awk`

Take a look:

sensors -f |grep "Core 0" |cut -d: -f2 |cut -d"(" -f1

Just for you understand:
cut -d: -f2
Means that ":" is a delimiter and -f2 means that I want the second field

And we have the same for cut -d"(" -f1, where:
-d"(" means that the "(" is the delimiter and I want the first field

[]'s

Alekz_

```

sensors -f | grep "Core 0" | cut -d: -f2 | cut -d"(" -f1 | awk '{print $1}'
+120.2°F

```

:p

Thank you!

---

