---
title: "Terminal question"
date: 2009-01-25
forum: General Help
---

### Post by UglieFrog on 2009-01-25
Ok lil back ground.....I plqy diablo2 on wine and some times i need to know what game server iam on.

So i asked in the ubuntu chatroom what i coud type into the terminal to get what i needed and i got the following which works great

sudo watch -n 5 'netstat -putan | grep 4000'

I copied and pasted it into a text file so i could remember it. Now my issue

if i type it in. it doesnt work. But if i copy and paste it. it works/

what am I doing wrong

---

### Post by heindsight on 2009-01-25
Not sure why it wouldn't work if you type the command, perhaps you're making a small typo eg. using the wrong quotes.

what you can do though, is to create a file looking like:
```

#!/bin/sh
sudo watch -n 5 'netstat -putan | grep 4000'

```
save it in your home directory call it gameserver.sh and give yourself permission to execute it by doing:
```
chmod u+x gameserver.sh
```

Now, whenever you want to know what gameserver you're on you need only type:
```
~/gameserver.sh
```

---

### Post by UglieFrog on 2009-01-25
> **heindsight said:**
> Not sure why it wouldn't work if you type the command, perhaps you're making a small typo eg. using the wrong quotes.

what you can do though, is to create a file looking like:
```

#!/bin/sh
sudo watch -n 5 'netstat -putan | grep 4000'

```
save it in your home directory call it gameserver.sh and give yourself permission to execute it by doing:
```
chmod u+x gameserver.sh
```

Now, whenever you want to know what gameserver you're on you need only type:
```
~/gameserver.sh
```

which quote command is it?. the one by shift i have to hit the key twice for it to come up but it does

---

### Post by taurus on 2009-01-25
> **UglieFrog said:**
> which quote command is it?. the one by shift i have to hit the key twice for it to come up but it does

It looks to me like the key right next to the Return, ' and Shift for ".

---

### Post by UglieFrog on 2009-01-25
[QUOTE=taurus;6615141]It looks to me like the key right next to the Return, ' and Shift for ".[/QUO


my shift doest activate it i have to hit the key twice for ´ and shift " then space for the it come up

---

### Post by heindsight on 2009-01-25
> **UglieFrog said:**
> 
my shift doest activate it i have to hit the key twice for ´ and shift " then space for the it come up

I think that may be your problem, hitting the quote key twice gives you a ´ character which is different from ' (which you can get by hitting the quote key followed by space). You need the second one, not the first.

---

### Post by UglieFrog on 2009-01-25
> **heindsight said:**
> I think that may be your problem, hitting the quote key twice gives you a ´ character which is different from ' (which you can get by hitting the quote key followed by space). You need the second one, not the first.


Hurray....oh what key is that then...where is it :)

---

### Post by UglieFrog on 2009-01-25
Thank you very much that was the problem.. I can type it in now. Ty Ty ..it was driving me nuts

---

