---
title: "Sleep Suffix"
date: 2009-01-27
forum: General Help
---

### Post by echo8413 on 2009-01-27
read a
echo "Enter a Larger Number"
read b
count+$a

clear
while [ $count -le $b ]

do echo $count
count=`expr $count = 1`
sleep 1 [`m]
done


Whenever I try inputting the sleep command with its suffix it the script doesn't work. However when I take out the suffix it works fine.

---

### Post by croto on 2009-01-27
the suffix must be appended to the number, like this:

sleep 1m

not like

sleep 1 m

so I'd fix your script like 
```

read a
echo "Enter a Larger Number"
read b
count=$a

clear
while [ $count -le $b ]

do echo $count
count=`expr $count + 1`
sleep 1m
done

```

---

