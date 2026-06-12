---
title: "ps1 customization"
date: 2009-03-30
forum: General Help
---

### Post by NaF on 2009-03-30
Is it possible to set up ps1 (or something else) so that, when i load up a new shell - it will display something once, and not on every new entry? 
say: ```

[date]
[hostname]

[user]: ls
(output)
[user]:  

```

if you catch my drift. On load it will display the date and hostname or whatever, and when a command is executed, it wont show up again?

---

### Post by NaF on 2009-03-30
> **NaF said:**
> Is it possible to set up ps1 (or something else) so that, when i load up a new shell - it will display something once, and not on every new entry? 
say: ```

[date]
[hostname]

[user]: ls
(output)
[user]:  

```

if you catch my drift. On load it will display the date and hostname or whatever, and when a command is executed, it wont show up again?
/facepalm.
Yes, this is one of those, when I posted this I realized what I was doing wrong. 

You obviously just have to add the code you want displayed once, above the ps1 info, in the script you're calling it from.

```
dato1=`date +%A`; #day of the week
dato2=`date +%d`; #day of the month
dato3=`date +%B`; #month of the year
dato4=`date +%Y`; #Year
dato5=`date +%U`; #week of the year

echo "$dato1 $dato2. $dato3, $dato4 - Week $dato5"
echo "Running from: `hostname`"
export PS1='\u> '

```

---

