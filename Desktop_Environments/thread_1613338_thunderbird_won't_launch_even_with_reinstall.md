---
title: "thunderbird won't launch even with reinstall"
date: 2010-11-04
forum: Desktop Environments
---

### Post by bluethundr on 2010-11-04
thunderbird is telling me it can't launch because a copy is already running. but I checked ps and there is no pid for it 

```

[root@dunphy:~/Downloads/thunderbird]#ps auxwww | grep thunderbird | grep -v grep
[root@dunphy:~/Downloads/thunderbird]#

```

I have tried uninstalling it and reinstalling it with aptitude under Ubuntu 10.

Does anyone have any suggestions on how I can get this working again?

thanks in advance!

---

### Post by wojox on 2010-11-04
Reboot, open a terminal and run 

```
thunderbird
```

And stay out of root. :)

---

### Post by mcduck on 2010-11-04
Try removing it's configuration files from your home directory. 

If you want to play it safe then move them somewhere else instead of deleting.

Uninstalling/reinstalling a program won't touch user's own configuration files, so if you have problems caused by bad settings reinstalling packages won't have any effect.

edit: +1 for staying out of root.

---

### Post by bluethundr on 2010-11-04
deleting the .thunderbird directory did it guys!! thanks! also my Nomachines setup wasn't working either and I extrapolated your advice and deleted the .nx directory which got that working again too!! thanks again so much for your help!!

---

