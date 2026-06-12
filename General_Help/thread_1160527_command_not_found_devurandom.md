---
title: "command not found /dev/urandom"
date: 2009-05-15
forum: General Help
---

### Post by Dragonatorul on 2009-05-15
Hello. I am trying to write a bash script that generates a random password using /dev/urandom but I keep getting command not found error and I have no idea why. Could someone please help me figure this one out? 

Basically when I write :

```
cat /dev/urandom | tr -dc _A-Z-a-z-0-9 | head -c8
```

in the terminal it prints out a string of 8 random characters. But when I run this script: 

```
#!/bin/bash

PASSWORD = `cat /dev/urandom | tr -dc _A-Z-a-z-0-9 | head -c8`
echo $PASSWORD
```

I get 

```
./ascript.sh: line 4: PASSWORD: command not found
```

Please help. 
Also, this is somewhat urgent. Thank you.

---

### Post by spiderbatdad on 2009-05-15
the only problem i see are the spaces where your variable is defined. Should be:
```
#!/bin/bash

PASSWORD=`cat /dev/urandom | tr -dc _A-Z-a-z-0-9 | head -c8`
echo $PASSWORD
```with PASSWORD standing alone like that, bash thinks it is a command.

---

