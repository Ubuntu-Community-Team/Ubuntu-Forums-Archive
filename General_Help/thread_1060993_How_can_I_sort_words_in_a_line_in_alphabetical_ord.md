---
title: "How can I sort words in a line in alphabetical order?"
date: 2009-02-05
forum: General Help
---

### Post by Rytron on 2009-02-05
Hi.
This is a simple example but how could I sort words in a line?

For example I want to change this:

sugar bread milk butter

to

bread butter milk sugar

---

### Post by geoglitch on 2009-02-05
Not sure how you want to do this but if you use python you could do:
unorderedstring = 'sugar bread milk butter'
wordlist = unorderedstring.split(' ')
wordlist.sort()
orderedstring = ' '.join(wordlist)

---

### Post by DGortze380 on 2009-02-05
> **Rytron said:**
> Hi.
This is a simple example but how could I sort words in a line?

For example I want to change this:

sugar bread milk butter

to

bread butter milk sugar

You can do this with a bash script and a simple bubble sort. Google should yield plenty of examples, if you can't find one post back and I'll put on together.

---

### Post by Dr Small on 2009-02-05
If the words are on individual lines, you can do it like this (of course, with a script, just read input and pipe it to sort):
```
[drsmall@darkghost ~]$ echo '
> sugar
> bread
> milk
> butter' | sort -d

bread
butter
milk
sugar

```

---

### Post by Rytron on 2009-02-05
> **geoglitch said:**
> Not sure how you want to do this but if you use python you could do:
unorderedstring = 'sugar bread milk butter'
wordlist = unorderedstring.split(' ')
wordlist.sort()
orderedstring = ' '.join(wordlist)

Hi.Do you have a script for that?

---

### Post by Dr Small on 2009-02-05
> **Rytron said:**
> Hi.Do you have a script for that?
I think that was the script ;)
```
#/usr/bin/python
unorderedstring = 'sugar bread milk butter'
wordlist = unorderedstring.split(' ')
wordlist.sort()
orderedstring = ' '.join(wordlist)
print orderedstring
```

---

### Post by geoglitch on 2009-02-05
Yeah, that was the guts of the script.  If you wanted to have it read in a string from the command line you could put this in the file order.py:

```
#!/usr/bin/env python
import sys
unorderedstring = sys.argv[-1]
wordlist = unorderedstring.split(' ')
wordlist.sort()
orderedstring = ' '.join(wordlist)
print orderedstring
```

then call it as:
```
$ ./order.py "sugar bread milk butter"
```

---

### Post by Rytron on 2009-02-05
> **geoglitch said:**
> Yeah, that was the guts of the script.  If you wanted to have it read in a string from the command line you could put this in the file order.py:

```
#!/usr/bin/env python
import sys
unorderedstring = sys.argv[-1]
wordlist = unorderedstring.split(' ')
wordlist.sort()
orderedstring = ' '.join(wordlist)
print orderedstring
```

then call it as:
```
$ ./order.py "sugar bread milk butter"
```


Nice one. Thanks.

---

