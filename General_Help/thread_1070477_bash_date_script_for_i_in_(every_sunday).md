---
title: "bash date script: for i in (every sunday)"
date: 2009-02-15
forum: General Help
---

### Post by goldfish2 on 2009-02-15
I want to write a bash script to fetch files from a website which are named after sundays of the month.

So something like

for i in $(seq 1 10)
do wget http://www.example.com/$i.wav
done

except it would output the sundays of the year, so it would fetch:
wget [http://www.example.com/20071125.wav](http://www.example.com/20071125.wav)
wget [http://www.example.com/20071202.wav](http://www.example.com/20071202.wav)
wget [http://www.example.com/20071209.wav](http://www.example.com/20071209.wav)

any ideas?

I ran into a dead end with "date +%Y%m%d --date=20080101"... since my input has to be the sunday away, thought I might be able to use an integer.

Thanks,
~GoldFish

---

### Post by heindsight on 2009-02-15
OK, I'm not sure this is the best way, but it should work.

```

#!/bin/bash
STARTDAY=20090104
for i in $(seq 0 51); do
    D=$(date +%Y%m%d --date $STARTDAY+${i}weeks)
    URL="http://www.example.com/$D.wav"
    wget $URL
done

```
Change STARTDAY to the date of the first file you want to download

---

### Post by goldfish2 on 2009-02-15
The --date input is a lot smarter than I thought!

Thanks!  That worked perfectly.

GoldFish

---

