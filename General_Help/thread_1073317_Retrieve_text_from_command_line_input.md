---
title: "Retrieve text from command line input"
date: 2009-02-18
forum: General Help
---

### Post by yeleek on 2009-02-18
Hi,

Given this line (which itself comes from a grep of a curl).

Global Threat ConditionElevatedLearn More

How can I add a space after the n of condition, add a space before the L of learn? and then only retrieve the fourth word?

I can't specifically search for elevated, as that word may change.

Any ideas please?

Thank you

---

### Post by sdennie on 2009-02-18
Maybe pipe it to something like:

```

sed -e 's/.*Condition\(.*\)L.*/\1/'

```

---

### Post by yeleek on 2009-02-18
Hey,

Thanks for prompt reply - what i'm trying is this [PHP] curl -s "http://www.mcafee.com/us/threat_center/default.asp" | grep "Global Threat Condition" | sed -e :a -e 's/<[^>]*>//g;/</N;//ba' | sed -e 's/.*Condition\(.*\)L.*/\1/'[/PHP]

which then gives me

ElevatedLearn MoreMcAfee Avert 
  Global Threat Condition

Just want Elevated - problem is as I say with the security condition that word will change...

Thank you

---

### Post by sdennie on 2009-02-18
```

curl -s "http://www.mcafee.com/us/threat_center/default.asp" | grep "Global Threat Condition" | sed -e :a -e 's/<[^>]*>//g;/</N;//ba' | sed -e 's/.*Condition\(.*\)Learn.*/\1/' -e 's/^\s.*$//' -e '/^$/d'

```

:)

---

### Post by yeleek on 2009-02-18
Thank you very much.  Now i just need to read up on what you did ;-)

Cheers

---

### Post by sdennie on 2009-02-18
Get the word between Condition and Learn.
```

sed -e 's/.*Condition\(.*\)Learn.*/\1/'

```

Erase any line with a space in it
```

-e 's/^\s.*$//'

```

Delete empty lines
```

-e '/^$/d'

```

I'm sure this could be done more elegantly but, it was the first syntax that came into my head.

---

### Post by yeleek on 2009-02-18
Thanks again!!!  Thats great.

---

