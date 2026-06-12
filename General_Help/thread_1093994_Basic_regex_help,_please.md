---
title: "Basic regex help, please"
date: 2009-03-12
forum: General Help
---

### Post by sexcopter on 2009-03-12
Hi,

I'm not really familiar with regex, but want to use it for something (and learn while I'm at it!). Basically I have a ton of png files of the form apg_0005.png through apg_0564.png, and I want to list them in batches of 9 for tiling (using montage, but that's not what I need help with right now). I'm trying to build up a little script, and I feel like I'm getting there, but it's not behaving how I think it should, so I must be misunderstanding something. The code below is really just me trying to figure out how things work, and just for now I've made it stop at 50 for simplicity:
```

#!/bin/bash

start=5

while [ $start -lt 50 ]
do
        echo $start
        subfilelist=`ls | grep "apg_00$(seq $start $[$start+9]).png"`
        echo $subfilelist
        start=$[$start + 10]
done

```
Thing is, this is still matching apg_0105.png, despite the "00" in my expression. What I want to aim for (I think) is to have only zeros followed by exactly the output of seq (thus 0105 is excluded). I've tried a whole bunch of things, but nothing I do seems to enforce there being zeros!

Can anyone clarify this for me and point me in the right direction?

Thanks,

James

---

### Post by heindsight on 2009-03-12
If you want to learn about regular expressions, I recommend you read the grep manual:
```
man grep
```
There's quite a good description of regular expressions in there.

You don't need regular expressions for what you're trying to achieve here though. The following should do the trick:
```
#!/bin/sh
STEP=9
LO=5
HI=50
for start in $(seq $LO $STEP $HI); do
  N=$(printf "apg_00%02d.png " $(seq $start $((start+STEP-1))));
  ls $N;
done
```
This for loop starts off with $start as 5 ($LO) and increments it by 9 ($STEP) each time until it reaches 50 ($HI).
For each value of $start we generate the sequence of numbers from $start to $start+$STEP-1 and pass them as arguments to printf which prints each in the form:
```
apg_00%02d.png
```
where the %02d means print a whole decimal number with 2 digits (pad with zeros if the number has less than 2 digits). This generates $STEP names of the form apg_0005.png which are placed in the variable $N.

Have a look at the shell manual
```
man sh
```
for more details on the syntax and meanings of the commands used.

---

### Post by sexcopter on 2009-03-12
Wow, that worked a treat. Thanks!

There were a couple of new elements I didn't know, namely the printf and placeholder. I believe I understand what they do in this context, and I see there's plenty of documentation on the printf command too.

I also like the use of LO STEP and HI, quite clever (to me anyway)!

Thanks again,

James

---

