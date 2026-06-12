---
title: "find and replace in shell script"
date: 2009-03-17
forum: General Help
---

### Post by stek_87 on 2009-03-17
Hi.

I need a script that can locate some text in a textfile and replace it with some other text..

I have tried this one:
find . -name 'test.txt' |xargs perl -pi -e 's/find/replace/g'

And it works just great, but in my case I would like to find a string like that looks like this: :/findthis/ and replace it with /replace

The script then looks like this:
find . -name 'test.txt' |xargs perl -pi -e 's/:/findthis///replace/g'

And fails when trying to run it...

how can I fix this??

/S

---

### Post by sisco311 on 2009-03-17
```
perl -pi -e 's/:\/find\//\/replace/g'
```

man perlre :evil:
```
 In particular the following metacharacters have their standard
       egrep-ish meanings:

           \   Quote the next metacharacter

```

 a backslash causes the metacharacter to be treated as a literal character.

---

### Post by stek_87 on 2009-03-17
> **sisco311 said:**
> ```
perl -pi -e 's/:\/find\//\/replace/g'
```

man perlre :evil:
```
 In particular the following metacharacters have their standard
       egrep-ish meanings:

           \   Quote the next metacharacter

```

 a backslash causes the metacharacter to be treated as a literal character.

Thanks alot.. :) problem solved!

---

