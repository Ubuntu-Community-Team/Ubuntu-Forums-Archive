---
title: "Mass file rename in CLI"
date: 2009-01-28
forum: General Help
---

### Post by @B6Mwu8fN9M on 2009-01-28
I have an icon theme that has many folder colors. The default is green and I want to use the blue folders. The defaults are named like they should be for ubuntu to use them. The blue ones have "blue-" at the beginning of them. I want to rename all the files starting with "blue-" so that part is removed. There are many files so I was wondering how I could do that from the CLI. 

I want the original file names (the ones starting with blue) to be unchanged; I want them to overwrite the ones not starting with blue. All the files are in the same folder.


Thanks in advance..:D

---

### Post by mgol on 2009-01-28
> **vlad003 said:**
> I want to **rename** all the files starting with "blue-" so that part is removed.
(...)
I want the original file names (the ones starting with blue) to be unchanged
There's a bit inconsistency here... ;) I suppose You want to make a copy of these files, not actually rename them? So, this is it:

```

for file in blue-*
do
    cp "$file" "${file:5}"
done

```

It's very simple - "${file:5}" means that You take the $file string and cut off its first 5 symbols.

---

### Post by @B6Mwu8fN9M on 2009-01-28
Thanks, it worked perfectly..:D

---

### Post by jms1989 on 2009-01-29
Nice. What would you use to cut off 5 characters on the end of the files?

Referring to "${file:5}", that is. Would using a negative work?

---

### Post by mgol on 2009-01-29
> **jms1989 said:**
> Nice. What would you use to cut off 5 characters on the end of the files?

Referring to "${file:5}", that is. Would using a negative work?

Yes, but with an additional space (to avoid ':' and '-' being not separated) or within brackets. See:
[Manipulating Strings: Substring Extraction](http://tldp.org/LDP/abs/html/string-manipulation.html#SUBSTREXTR01)
for more information about manipulating strings in bash.

---

