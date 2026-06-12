---
title: "RPG Dice Roller"
date: 2010-03-12
forum: Gaming &amp; Leisure
---

### Post by paulhair on 2010-03-12
Hey Guys hope you are well.

Just wondering if there is a Dice Roller (1d4-1d100) Program for RPG Games, hoping there is and look forward to hearing from you.

Safe Travels, speak soon. 
Paulhair.

---

### Post by howlingmadhowie on 2010-03-12
> **paulhair said:**
> Hey Guys hope you are well.

Just wondering if there is a Dice Roller (1d4-1d100) Program for RPG Games, hoping there is and look forward to hearing from you.

Safe Travels, speak soon. 
Paulhair.

This should work: 
```

#!/bin/bash

echo -n "enter number: "
read NUM

while (( "$NUM" != 0 )); do
    number=$RANDOM
    expr $number \* $NUM / 32768 + 1
    echo -n "enter number[$NUM]: "
    read NEWNUM
    if [ -n "$NEWNUM" ];
        then
        NUM=$NEWNUM
    fi
done

```

enterering 0 will cause it to quit.

---

### Post by Toffeeapple on 2010-03-12
There might be lots of stuff [here]("http://www.rptools.net/") : )

---

### Post by Tolaris on 2010-06-29
See the package "rolldice". It's command-line, but it rocks. Generate a D&D 3/4 character:

sudo apt-get install rolldice
rolldice -s 6x4d6s1

---

### Post by donkyhotay on 2010-07-02
I just google "dice roller" and use whatever I find there.

---

### Post by calicojack73 on 2012-06-26
I normally create my own customized dice roller in LibreOffice Calc.  Use the random number function to create your numbers and then you can modify and combine it with other numbers and functions in any way you please.  IMHO it is the best way to make a dice roller that works exactly the way you want it.

---

### Post by Perfect Storm on 2012-06-26
Old thread.

Closed.

---

