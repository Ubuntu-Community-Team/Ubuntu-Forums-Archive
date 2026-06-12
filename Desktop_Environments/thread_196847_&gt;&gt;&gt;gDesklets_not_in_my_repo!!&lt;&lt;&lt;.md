---
title: "&gt;&gt;&gt;gDesklets not in my repo!!&lt;&lt;&lt;"
date: 2006-06-14
forum: Desktop Environments
---

### Post by kickstar on 2006-06-14
hello this is really anoying, i cant get gDesklets - is it not in the repository? im using dapper...

what line do i need to add to my sources.list?

---

### Post by taurus on 2006-06-14
First of, it's gdesklets, not gDesklets.  And if gdesklets doesn't show up, then perhaps you need to remove the # in front of all the lines for universe and multiverse...
```

sudo gedit /etc/apt/sources.list

```
Save it and then run (from a terminal as well...)
```

sudo apt-get update
sudo apt-get install gdesklets gdesklets-data

```

---

