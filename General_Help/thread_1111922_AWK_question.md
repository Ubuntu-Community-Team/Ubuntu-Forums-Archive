---
title: "AWK question"
date: 2009-03-31
forum: General Help
---

### Post by vandinsh on 2009-03-31
How 0.00009330 convert to  93,30 ?

Thanks a lot!! :)

---

### Post by akudewan on 2009-03-31
Your question doesn't make much sense. Could you elaborate? Are you talking about the *awk* command?

---

### Post by ibuclaw on 2009-03-31
You mean:
```
echo 0.00009330 | awk '{$1*=1e6; gsub(/\./, ","); print}'
```
?

Or, to make it more awk oriented:
```

awk '
BEGIN {
   printf "Type Number: ";
}

{
   $1*=1e6;
   gsub(/\./, ",");
   print $1;
   printf "Type Number: ";
}

END {
    print "";
}'

```

---

### Post by Odemia on 2009-03-31
I doubt this is what you meant but:
echo 0.00009330 | awk '{print $1*100000000}'

If you could be more specific on what you are converting.  Do you want 4 digits starting with the firts non-zero?  What should happen if the input were all zeros or didn't have a decimal place?  Do you want the output printed or as a variable for more processing?

---

