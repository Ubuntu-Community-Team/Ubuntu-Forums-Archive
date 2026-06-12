---
title: "Split fields in a tab delimited file"
date: 2012-08-08
forum: Desktop Environments
---

### Post by ashkot on 2012-08-08
Hi all,
I have a tab delimited file with 8 columns, in one of the column i have data such as 

1:1000
2:2000
3:3000

What i want to do is to split the entire file such that a new column is created as follows
1 [tab] 1000
2 [tab] 2000

How can this be done?

Thanks in advance.
A

---

### Post by Lars Noodén on 2012-08-08
Would something like this work?

```

 awk 'FS="[:\t]"{printf "%s\t%s\t%s\n", $1, $2, $3}' /tmp/x.csv

```

You'd have to pad it out for the appropriate number of columns.

---

### Post by drmrgd on 2012-08-08
You can also use the Output Field Separator (OFS) function of awk to put tabs in.  This should work as well:

```
awk -F':' 'BEGIN{OFS="\t"} {print $1,$2}' test.txt
```

---

### Post by SeijiSensei on 2012-08-08
I usually handle problems like this in an editor.  I use [jed]("http://www.jedsoft.org/jed/") in Emacs mode and can enter the tab character as ^Q^I.  So I would just do a global search and replace for ":" and replace it with tab sequence.  Works for me.

I used sed for a variety of things, but it's not always as easy as using a full-screen text-mode editor.

---

### Post by Lars Noodén on 2012-08-08
The first example I gave would give a problem if the colon appears elsewhere in a column.  This restricts the substitution to one column.  Swap $1 for the number of the column to be split:
```

awk '{sub(/:/,"\t",$1);printf "%s\t%s\t%s\n", $1, $2, $3}' /tmp/x.csv

```

---

### Post by steeldriver on 2012-08-08
or you could even use 'tr' I think

if you want to extract just one column (I may be reading that wrong) then something like

```
cut -f*n* file | tr ':' '\t'
```where *n* is the index of the column containing the 1:1000 data

If I *am* reading it wrong, and you just want to split the data column, then I would use awk as well - to be absolutely safe (in case there are : characters elsewhere) you could do something like

```
 awk 'BEGIN{OFS="\t"} { split($5,a,":"); print $1,$2,$3,$4,a[1],a[2],$6,$7,$8; }' 
```(adjust the $5 as appropriate)

---

### Post by papibe on 2012-08-08
Hi ashkot.

Another approach is to replace the delimiter ':' for 'tab'. This may work for you if the delimiter is not used in another field:
```
sed  's/:/\t/g'  file.txt
```
Regards.

---

### Post by ashkot on 2012-08-09
This worked the best for me, thank you all again.

ashkot


> **steeldriver said:**
> or you could even use 'tr' I think

if you want to extract just one column (I may be reading that wrong) then something like

```
cut -f*n* file | tr ':' '\t'
```where *n* is the index of the column containing the 1:1000 data

If I *am* reading it wrong, and you just want to split the data column, then I would use awk as well - to be absolutely safe (in case there are : characters elsewhere) you could do something like

```
 awk 'BEGIN{OFS="\t"} { split($5,a,":"); print $1,$2,$3,$4,a[1],a[2],$6,$7,$8; }' 
```(adjust the $5 as appropriate)

---

