---
title: "gdesklets graphs showing inverted"
date: 2006-02-22
forum: Desktop Environments
---

### Post by larsemil on 2006-02-22
my gdesklets are running fine with the little exception that they all show the inverted graph... 

example my cpu desklet:
```
Cpu: 10%
Amd Athlon
@2105M      
```
And this information is correct.

My graph below it(same desklet) shows 90% full.

If i run a program that uses 100% cpu the graph does not show anything at all.

I have the same problem with MEM, SWAP and HD.


At first i did not get any graphs at all(they all showed 100%) but efter looking around i found out that you should change a line in the sources.
Change:
```
<gauge id="mem" fill="50" anchor="sw" relative-to="swap,y" y="-10">
```

```
<gauge id="mem" fill="50" anchor="se" relative-to="swap,y" y="-10">
```

And then i got them monitoring, but INVERTED. 

What to do?

---

