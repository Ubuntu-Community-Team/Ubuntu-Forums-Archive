---
title: "Closing konsole, closes launched programs"
date: 2005-07-01
forum: Desktop Environments
---

### Post by SGC on 2005-07-01
Sometimes while working on konsole, I launchs others programs, let say:
*"konqueror www.ubuntuforums.org"*

But then closing konsole will close konqueror in this case or any other program launched from konsole

So my question is, How to make these programs stay even after closing konsole. So Instead of making these programs a childs processes of konsole , making them separate ones.

---

### Post by Seti on 2005-07-01
To do what you want to do, (launch a program from a console but then close the console so that the application stays, you want to do```
nohup yourprogram
``` 
and that will do it.
Do a ```
man nohup 
``` 
for more info.

---

### Post by SGC on 2005-07-01
Thanks Seti

---

