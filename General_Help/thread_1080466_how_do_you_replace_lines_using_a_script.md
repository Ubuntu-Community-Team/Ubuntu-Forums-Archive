---
title: "how do you replace lines using a script?"
date: 2009-02-25
forum: General Help
---

### Post by Christian Christiansen on 2009-02-25
I have a file which has fifty lines and there is only one number on each line. The lines alternate between 0 and 1, on all the odd lines there is 0 and on all the even lines there is a 1. I want to change every third line (lines 3, 6, 9...) so that the 0s turn to 1 and the 1s turn to 0 and do the same for every fourth line, fifth line etc. up to the fiftieth line. I know this is possible with awk and replace but I still can't figure the exact command I need to use.

Any ideas?

---

### Post by Yellow Pasque on 2009-02-25
IMO, you should ask to have your thread moved to the programming forum. You're more likely to get a resolution there.

---

### Post by geirha on 2009-02-25
This should toggle the bit on every third line ...
```
awk '{if (NR%3 == 0) $1=!$1; print}' file
# in-place version:
awk '{if (NR%3 == 0) $1=!$1; print >FILENAME}' file

```

---

### Post by Christian Christiansen on 2009-02-25
Thanks. I'll just do it manually from there then.

---

### Post by geirha on 2009-02-25
You can also pass variables from bash to awk so that you can do it in a for loop ...
```

x=3
awk -v x=$x '{if (NR%x == 0) $1=!$1; print}' file

```

---

