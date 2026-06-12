---
title: "Line count and transform a text file"
date: 2012-08-09
forum: Desktop Environments
---

### Post by ashkot on 2012-08-09
hi all,
i have a tab delimited text file and i have data such as

Col 1 Col 2
1     a
1     b
1     c
1     d
1     d
2     a
2     b
3     a

(the numbers are in Col1 and alphabets are in Col2, the formatting on this page can cause some confusion)

so and so forth....

what i would like is to transform this structure such as

     a b c d

1 1 1 1 2
2 1 1 1 1
3 1 0 0 0

so that now, a,b,c,d become columns and 1,2,3 becomes a single row and the numbers represent count, for e.g. 1 has 1 a but 2 d's....

how can this be accomplished using awk or other similar tools?

thanks,
a

---

### Post by cybergalvez on 2012-08-09
not the prettiest of python code but this will do what you want. testfile.csv represent the file you put in the example

```


rows = [x.strip() for x in open('testfile.csv').readlines()]
rows = [x.split('\t') for x in rows]
rdict = dict()

count = []

for r in rows:
    if r[1] not in rdict:
        rdict[r[1]] = {r[0]:1}
        if r[0] not in count:
            count.append(r[0])
    
    elif r[1] in rdict:
        if r[0] in rdict[r[1]]:
            rdict[r[1]][r[0]] += 1
        if r[0] not in rdict[r[1]]:
            rdict[r[1]][r[0]] = 1
            if r[0] not in count:
                count.append(r[0])

print rdict

cols = rdict.keys()
cols.sort()
print cols

i = 1
out = open('out.txt', 'w')
header = [x for x in cols]
header.insert(0, '')
header.append('\n')
out.write('\t'.join(header))
for c in count:
    y = str(i)
    r = [y]
    for col in cols:
        if y in rdict[col]:
            r.append(rdict[col][y])
        else:
            r.append(0)
    r.append('\n')
    r = [str(x) for x in r]
    out.write('\t'.join(r))
    i += 1

```

---

### Post by asmoore82 on 2012-08-09
I'm not sure I understand but I think you want the "grid" of data in the middle of the new file to count unique combinations of letters and numbers. If so, you can do this very easily but without the "grid" layout:

```
cat *file* | sort | uniq -c
```

This will put the counts in a column on the left and the letter/number combo's on the right.

Here's a generator for a random test file of 64 lines:
```
array=(a b c d)
for i in $(seq 64)
do
    echo -e "$((RANDOM%4+1))\\t${array[$((RANDOM%4))]}"
done > file1
```

Here's the output of the 1st command, counting the combo's:
```
      1 1	a
      4 1	b
      4 1	c
      4 1	d
      2 2	a
      4 2	b
      3 2	c
      5 2	d
      3 3	a
      7 3	b
      5 3	c
      5 3	d
      7 4	a
      5 4	b
      1 4	c
      4 4	d
```

You could then build the grid easily with the `paste` command, **IF** you can assume every combination appears at least once...

```
cat file1 | sort | uniq -c | cut -c-7 | paste - - - -
```

Here's the grid from the above sample:
```
      1	      4	      4	      4
      2	      4	      3	      5
      3	      7	      5	      5
      7	      5	      1	      4
```

If you can't assume every combo is there at least once, you could inject 1 of every combo from the start and just decrease all the counts by 1 at the end.

Here's a full run through with nested while loops to inject all the combo's. The cool thing about it is that it dynamically cuts out the columns from the original file to make all of the possible combo's:

```
[B]cat file1 | cut -f1 | sort | uniq | while read cola
do
    cat file1 | cut -f2 | sort | uniq | while read colb
    do
        echo -e "$cola\\t$colb"
    done
done > inject
cat inject file1 | sort | uniq -c | cut -c-7 | paste - - - -[/B]
      2	      5	      5	      5
      3	      5	      4	      6
      4	      8	      6	      6
      8	      6	      2	      5
```

I enjoy that shell scripts can accomplish almost anything, even when not really the best possible tool for the job :D. So here's going way out on a limb and forcing bash to decrement all of the counts by 1.

```
cat inject file1 | sort | uniq -c | cut -c-7 | while read count
do
    echo $(( count - 1 ))
done | paste - - - -
```

And now we can craft a file with missing combo's that will break the first solution but not the final one:
```
array=(a b c d)
for i in $(seq 64)
do
    echo -e "$((RANDOM%4+1))\\t${array[$((RANDOM%4))]}"
done | grep -v -e "2.c" -e "3.b" > file2
```
grep was used to remove the combo's "2 c" and "3 b", so that a file that should have been 64 lines, is only:
```
**wc file2** 
 50 100 200 file2
```

Now use the naive grid maker and see the breakage:
```
**cat file2 | sort | uniq -c | cut -c-7 | paste - - - -**
      5	      5	      1	      3
      4	      6	      1	      3
      5	      4	      3	      6
      1	      3
```

Now use the injection trick to get the right answers (there should be 2 0's in the middle of the grid) ...
```
[B]cat inject file2 | sort | uniq -c | cut -c-7 | while read count
do
    echo $(( count - 1 ))
done | paste - - - -[/B]
5	5	1	3
4	6	0	1
3	0	5	4
3	6	1	3
```

It works! but it's not very "pretty" :D.

---

