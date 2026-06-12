---
title: "Single command, create lots of files?"
date: 2009-05-31
forum: General Help
---

### Post by Psycho.mario on 2009-05-31
Is there one single command that will put one word/sentence in ~1000 unique files?
Sort of like:
```
echo test > test1
echo test > test2
echo test > test3
...
```
Can't i use something like For...In...? I've heard of it, but don't knwo how to use it.

Thanks

---

### Post by .nedberg on 2009-05-31
> **Psycho.mario said:**
> Is there one single command that will put one word/sentence in ~1000 unique files?
Sort of like:
```
echo test > test1
echo test > test2
echo test > test3
...
```
Can't i use something like For...In...? I've heard of it, but don't knwo how to use it.

Thanks

```

for count in `seq 20`
do
	echo test > test${count}
done


```

Adjust the "seq 20" to what you need

---

### Post by Psycho.mario on 2009-05-31
Perfect!! Thanks

---

