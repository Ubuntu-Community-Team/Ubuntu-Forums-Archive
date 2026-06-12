---
title: "How to use grep to find one of several words"
date: 2006-10-25
forum: Desktop Environments
---

### Post by johnusa on 2006-10-25
I am an Ubuntu newbie.
I have a file name scratch.  I want to search the file for the presence of the word "now" or "what".  I issued the following command:
```
localhost:/home/johni/Documents# **grep now|what scratch**
bash: what: command not found
```
I then issued the following command:
```
localhost:/home/johni/Documents# **grep (now|what) scratch**
bash: syntax error near unexpected token `now'
```
What is the correct syntax to search the scratch file for the presence of the word "now" or "what"?
Thanks in advance for your help.

---

### Post by mvdw on 2006-10-25
This is a tricky one, because bash will try to grab the "|" character as the pipe, so you will have trouble with it.

I did the following to get around the grabbing:
```

egrep -e $(echo "now|what") <file-list>

```
It works, but surely it's not the most elegant solution going around.

Cheers,
mvdw

---

### Post by johnusa on 2006-10-25
Thank you **mvdw** for your solution.  I played around with your solution until I was able to simplify it as follows:
```
localhost:/home/johni/Documents# **egrep -e $(echo "now|what") scratch**
now is the time for all good men to come to the aid of their country.
what time of day is it?
what are you doing?
```
modified to:
```
localhost:/home/johni/Documents# **egrep "now|what" scratch**
now is the time for all good men to come to the aid of their country.
what time of day is it?
what are you doing?
```
Using **egrep** instead of **grep** made a significant difference.  Thanks again for your help.

---

### Post by johnusa on 2006-10-25
The following is an alternate method of achieving the same result:
```
localhost:/home/johni/Documents# **egrep now\|what scratch**
now is the time for all good men to come to the aid of their country.
what time of day is it?
what are you doing?
```

---

