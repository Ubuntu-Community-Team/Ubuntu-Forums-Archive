---
title: "shell the usage of for"
date: 2009-06-06
forum: General Help
---

### Post by HAPPYZZX on 2009-06-06
What is wrong with my code? Did I use the 'for' incorrect?
How to resolve it?
#!/bin/sh
for (( i=0;i<3;i++))
 do
        for ((j=1;j<5;j++))
           do
                 echo $i $j 
           done
 done 
error:      ./forfor.sh: 2: Syntax error: Bad for loop variable
Looking forward your answer. Thank you in advance.

---

### Post by Tibuda on 2009-06-06
No.
```
for i in 0 1 2; do
  for j in 1 2 3 4; do
    echo $i $j
  done
done
```
or better
```
for i in `seq 0 2`; do
  for j in `seq 1 4`; do
    echo $i $j
  done
done
```
See also  **man seq**

---

### Post by lswb on 2009-06-06
I don't see a problem with what you've posted and it runs OK on my system. Perhaps there is just a typo in the actual file.

---

### Post by HAPPYZZX on 2009-06-12
I still don't find any syntax error. My ubuntu is 9.04

---

### Post by kaibob on 2009-06-12
Dash does not support (( i=0;i<3;i++)). Either use bash or use dash and substitute `seq 0 2` as suggested by danielrmt.

[https://wiki.ubuntu.com/DashAsBinSh](https://wiki.ubuntu.com/DashAsBinSh)

---

### Post by HAPPYZZX on 2009-06-15
Thank you very much. I now understand it.

---

### Post by ghostdog74 on 2009-06-16
> **danielrmt said:**
> No.
```
for i in 0 1 2; do
  for j in 1 2 3 4; do
    echo $i $j
  done
done
```
or better
```
for i in `seq 0 2`; do
  for j in `seq 1 4`; do
    echo $i $j
  done
done
```
See also  **man seq**
if you sequence is simple , then no need to use external command
```

for i in {0..2}

```

---

### Post by kaibob on 2009-06-16
> **ghostdog74 said:**
> if you sequence is simple , then no need to use external command
```

for i in {0..2}

```
I don't believe this is supported by Dash, though.

---

### Post by ghostdog74 on 2009-06-16
is OP using dash? i personally do not use dash, so i don't know, however, bash is widely used in most *nix so i can safely say, it will work most of the time.

---

### Post by lswb on 2009-06-16
ubuntu has been using dash rather than bash as the default non-interactive shell for some time now. ( /bin/sh is linked to /bin/dash rather than /bin/bash) The reasoning is that dash runs somewhat faster than bash and would speed up most scripts, particularly at start-up. If you use bash-only features or are not sure, use #!/bin/bash instead of #!/bin/sh in scripts.

---

