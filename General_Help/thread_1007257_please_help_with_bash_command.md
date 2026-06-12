---
title: "please help with bash command"
date: 2008-12-10
forum: General Help
---

### Post by realthor on 2008-12-10
Hello,

I have searched on the internet without much success. i am trying to get the text which can be considered delimited both by " " and "|" and I want to extract the text after every 20 or so spaces (ex below):

|2384| 491| 6| 136|Nov 28 00:43| 24| 154| |2387| |3452| |Nov 29 00:12| ETC

Let's say I want every 3rd field, can I do that with sed or awk so that there will be at the and a row consisting of each 3rd field?

ex: 6 24 3452 ETC

Thanks for the help.

---

### Post by iponeverything on 2008-12-10
Lets say your delimiter is "|"

cat file |awk -F\| '{print $3" "$9" "$12}'

---

### Post by realthor on 2008-12-10
hy,

Thanks for the quick answer but there is one issue...my file is hundreds of such "every 3rd field needed" worth. I need to get all of them, not the first 3 or four.

Regards.

---

### Post by hyper_ch on 2008-12-10
I'd do that in php as that is more familiar to me... however I'm sure it can be done with bash also.

---

### Post by iponeverything on 2008-12-10
Gota love awk.


```
cat <file> | awk -F\| '{for (x=0; x <= NF; x+=3) { if (x!=0) { s=s $x " " }  else {s="" } } if ($s) print s}'

```

---

### Post by realthor on 2008-12-10
works wonderfully...many many thanks.

Regards.

---

