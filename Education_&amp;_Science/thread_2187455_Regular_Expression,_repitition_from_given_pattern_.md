---
title: "Regular Expression, repitition from given pattern ONLY"
date: 2013-11-12
forum: Education &amp; Science
---

### Post by ice-simx on 2013-11-12
Hi,

need a regular expression ( for python ) to match sequence of digits followed by '+'
ie, it should match following
+1234
+12
12345
+123456789

but NOT
+123A
+12A45


tried re.search(r'[\+]?[0-9]+', var)
but it matches with all, as '+' at end of exp means 1 or more

---

### Post by ice-simx on 2013-11-12
or, **not-in-set** will also work ( can reverse the logic )

re.search(r'[\+]?[all-non-digit]+')

if patten found, reject it
else if pattern not found, its the required pattern ( as it will contain all digits then )

ie something similar like -v in grep

---

### Post by TheFu on 2013-11-12
Don't know python, sorry, but 

'[0-9]+[+]' will match it in regex.  At least 1 digit and a single '+' following it without any space or other characters.

Do you care about unicode? If so, do you care if the digits are ascii or will digits in any language be ok?  Do you need to convert the other-language-digits into ASCII so they can be used in equations?

BTW, seems your words and examples do not match. Is the '+' required or not?  Is it before or after the digits? 
I followed the words for the requirements which would have these examples:
1234+
12+
12345 <---- would not match at all. No "+" character.
123456789+

but NOT
123A+ <-- no match
12A45+   <--- this would match on the "45+" however.

---

### Post by steeldriver on 2013-11-12
Have you tried adding word anchors (aka zero length matches)? in grep they'd be \< to only match the pattern at the beginning of a word, and \> to only match at the end of the word e.g.

```

$ echo -e "+12345\n+123A45" | egrep '\+?[0-9]+'
+12345
+123A45
$ 
$ echo -e "+12345\n+123A45" | egrep '**\<**\+?[0-9]+**\>**'
+12345
$ 

```

In python, the equivalents are \A and \Z I think e.g.

```

>>> valid = re.compile(r"**\A**[\+]?[0-9]+**\Z**")
>>> valid.match("+123456").group(0)
'+123456'
>>> 
>>> valid.match("+1234**A**56").group(0)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: 'NoneType' object has no attribute 'group'
>>> 

```

---

### Post by ice-simx on 2013-11-13
thanks steeldrive, it works
and explanation you provide is really helpful.

---

