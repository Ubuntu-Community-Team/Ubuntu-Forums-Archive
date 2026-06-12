---
title: "Need help with awk script!!"
date: 2009-05-11
forum: General Help
---

### Post by systemdowned on 2009-05-11
I'm having trouble with the awk command and was wondering if someone could provide some insight. 

I have a command that gives me a pipe delimited output of customers that looks like this:
$customers equals this output
```
customer1|customer2|customer3|customer4|
```

$numberofcustomers equals the number of customers, in this case 4.

What I would like to do is output each customer from the pipe delimited file as the do while script runs through so I would get an output of:
```
customer1
customer2
customer3
customer4
```

Here is what I have so far:

```
customernumber=1

while [ $customernumber -le $numberofcustomers ]
	do
echo $customers | awk -F"|" '{print $1}'

customernumber=$((customernumber+1))
	done


```

My problem is I can't seem to put a value in '{print $1}' like '{print $customernumber}'. I just want to increase '{print $1}' by 1 every time the script runs though so it's '{print $1}' then '{print $2}' then '{print $3}' etc.

Any ideas?

---

### Post by mcduck on 2009-05-11
try this:

```
#!/bin/sh

customers="customer1|customer2|customer3|customer4"
numberofcustomers=4

customernumber=1
while [ $customernumber -le $numberofcustomers ]
  do echo $customers | awk -F "|" '{print $'$customernumber'}'
  customernumber=`expr $customernumber + 1`
done
```

---

### Post by systemdowned on 2009-05-11
Thanks!

I just couldn't figure out the right syntax for what I wanted. 

Appreciate it.

---

