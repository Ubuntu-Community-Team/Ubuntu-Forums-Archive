---
title: "How to use &quot;cut&quot; command"
date: 2009-03-23
forum: General Help
---

### Post by MountainX on 2009-03-23
I want to cut out non-contiguous colums from a file that contains lines like this:

```
be...39 c 6nn2-13nn85 2nnn81 1235839696 1233262475 1235844896 21480 0 0 420 name with spaces
```I want to keep just these columns

```
be...39 1233262475 21480 name with spaces
```I'm looking at [cut]("http://www.oreillynet.com/linux/cmd/cmd.csp?path=c/cut"), but I can't seem to get it right. It must work in "one pass" -- i.e., a single command not two commands run in series.

For example, this does NOT work:
```
cut -d ' ' -f [anything I've tried]
```It gives output with the name cut off because the space delimiter is a problem for names with spaces:
```
be...39 name
```Can anyone give me the right approach?

---

### Post by Bachstelze on 2009-03-23
```
firas@iori ~ % echo "be...39 c 6nn2-13nn85 2nnn81 1235839696 1233262475 1235844896 21480 0 0 420 name with spaces" | cut -d ' ' -f 1,6,8,12-
be...39 1233262475 21480 name with spaces

```

---

### Post by MountainX on 2009-03-23
Thank you, thank you! That works perfect.

---

### Post by MountainX on 2009-03-23
> **HymnToLife said:**
> ```
 cut -d ' ' -f 1,6,8,12-

```
Can you explain the rules for the list of columns? Or maybe give me a better reference than the page I was looking at?

I know that means cut columns from 1 to 5 (which keeps  column 0), keep 6, cut 7, keep 8, cut 9 to 11, keep 12 and greater.

But I guess I don't feel like I understand the rules well enough to solve complex needs in the future...

Thanks again!

---

### Post by MountainX on 2009-03-23
If I now want to replace the space delimiters with commas, how would I do that? I suspect I can use a combination of "cut" and "paste" commands, maybe with **-output-delimiter=***string*
But I'm stumped as to how to actually do it.
using the same example:
```
be...39 c 6nn2-13nn85 2nnn81 1235839696 1233262475 1235844896 21480 0 0 420 name with spaces
```
I want to end up with:
```
be...39,1233262475,21480,name with spaces
```

---

### Post by Bachstelze on 2009-03-23
I don't think you can do that in one [font="monospace"]cut[/font] command. Since [font="monospace"]cut[/font] has no way to know whether a space belongs to the name or is an actual delimiter, it would replace all spaces with commas if you used [font="monospace"]--output-delimiter[/font]. You'll have to use more advanced tools like [font="monospace"]awk[/font]:

```
firas@iori ~ % echo "be...39 c 6nn2-13nn85 2nnn81 1235839696 1233262475 1235844896 21480 0 0 420 name with spaces" | awk '{printf("%s,%s,%s,", $1, $6, $8); for(i=12; i<NF; i++) printf("%s ", $i); printf("%s\n", $NF);}'
be...39,1233262475,21480,name with spaces

```

---

### Post by MountainX on 2009-03-23
Thank you again :)

I'm getting ready to try your awk code. But my text file is 50 MB. With the for-loop, I'm guessing this might take a while. Hopefully it won't overtax my machine.

Here's what I'm going to run (I hope):

```
cat <$pathToFile/FileToProcess | egrep -v 'aaa |^bbb|^ccc|^ddd|^eee|^fff' | sort | awk '{printf("%s,%s,%s,",$1,$6,$8); for(i=12; i<NF; i++) {printf("%s ", $i);} printf("%s\n", $NF);}' | uniq -w 32 -D
```

---

### Post by MountainX on 2009-03-23
> **MountainX said:**
> 
I'm getting ready to try your awk code. But my text file is 50 MB. With the for-loop, I'm guessing this might take a while. Hopefully it won't overtax my machine.


Wow! Impressive. It was fast and it works :)

---

