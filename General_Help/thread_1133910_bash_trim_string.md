---
title: "bash trim string"
date: 2009-04-23
forum: General Help
---

### Post by prem1er on 2009-04-23
How would I trim a 13 character string to make it an 8 character string in bash?  Thanks.

Edit: The string has no white space in it, I simply need to remove the last 5 digits.

---

### Post by prem1er on 2009-04-23
Got it.

${variable:start_trim_position:end_trim_position}

Is this the best way to do this?

---

### Post by iponeverything on 2009-04-23
```
echo $string | cut -c1-13

```

---

