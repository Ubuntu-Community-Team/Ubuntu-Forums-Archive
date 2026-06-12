---
title: "conky : use $eval within $image?"
date: 2009-12-27
forum: Desktop Environments
---

### Post by wlourf on 2009-12-27
Hi,

With conky 1.7.2, I try to  display a picture depending  on time, (seconds in my example) so I tried this :
```

1.${eval ${time ~/img%S.png}}
2.${eval $${image ${time ~/img%S.png}}
3.${image ${eval ${time ~/img%S.png}}}

```and the results are :
```
for line 1: ~/img00.png as excepted
for line 2 : ${image ~/img00.png} --> why the image is not displayed here?
for line 3 : error message : Unable to load image '${eval'

```thanks for any help

w

---

### Post by londonali1010 on 2009-12-27
> **wlourf said:**
> Hi,

With conky 1.7.2, I try to  display a picture depending  on time, (seconds in my example) so I tried this :
```

1.${eval ${time ~/img%S.png}}
2.${eval $${image ${time ~/img%S.png}}
3.${image ${eval ${time ~/img%S.png}}}

```and the results are :
```
for line 1: ~/img00.png as excepted
for line 2 : ${image ~/img00.png} --> why the image is not displayed here?
for line 3 : error message : Unable to load image '${eval'

```thanks for any help

w

I don't think you can really use the $eval command like that, unfortunately.  You can do it explicitly, using the $if_match and $updates variables:
```
${if_match ${updates}=12}${image ~/img12.png}${endif}
```
Does that get you close enough?

Otherwise, you can definitely do it using a Lua function from Conky...

---

### Post by wlourf on 2009-12-28
thanks, i will try Lua. I read your air clock, it's a good beginning !

---

