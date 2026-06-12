---
title: "sed matched pattern"
date: 2009-06-22
forum: General Help
---

### Post by desperateone on 2009-06-22
Say I want to replace all things matching "bought [number] golds" with "golds bought: [the_same_number]". I gonna access the matched pattern, how can I do that?

---

### Post by Nepherte on 2009-06-22
The exact command is:
```
sed 's/<pattern_to_be_replaced>/<the_replacing_value>/g' -i <filename>
```
where <somevalue> should be replaced with an actual pattern or filename.

---

### Post by desperateone on 2009-06-22
> **Nepherte said:**
> The exact command is:
```
sed 's/<pattern_to_be_replaced>/<the_replacing_value>/g' -i <filename>
```
where <somevalue> should be replaced with an actual pattern or filename.
Yes, I know that, but my problem is that I need to use a part of the matched pattern in the replacing pattern, so I have to extract it somehow.

---

### Post by Nepherte on 2009-06-22
Well, the patterns are regular expressions. The pattern should look like:
bought [1-9]+ golds

I am however not completely familiar with the POSIX regexp syntax.

---

### Post by geirha on 2009-06-22
```
sed -r 's/bought ([0-9]+) golds/golds bought: \1/'
```

---

### Post by desperateone on 2009-06-22
> **Nepherte said:**
> Well, the patterns are regular expressions. The pattern should look like:
bought [1-9]+ golds

I am however not completely familiar with the POSIX regexp syntax.

And how would the replacing pattern look like? I want to use the thing that matched the [0-9]+ in the first pattern.

---

### Post by desperateone on 2009-06-22
> **geirha said:**
> ```
sed -r 's/bought ([0-9]+) golds/golds bought: \1/'
```

That's what I've been looking for, thank you.

---

