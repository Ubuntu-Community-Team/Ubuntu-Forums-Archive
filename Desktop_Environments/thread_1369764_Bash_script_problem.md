---
title: "Bash script problem"
date: 2010-01-01
forum: Desktop Environments
---

### Post by xx77aBs on 2010-01-01
Hello ! I have this script:

```
#!/bin/bash

for direc in $(ls -d */) ; do
echo $direc
done


```

It works great when folders don't have space in their names. When some folder does have space in name, it get's printed out in two rows. Is there any way to get whole name (including spaces) in one row ?

Thanks :)

---

### Post by sisco311 on 2010-01-01
```
#!/bin/bash

for direc in "$(ls -d */)" ; do
echo "$direc"
done
```

---

### Post by xx77aBs on 2010-01-01
ha, I've tried that, but without quotes in echo .. stupid :D 

Thanks ;)

---

### Post by DaithiF on 2010-01-01
no need for ls in fact, just this will do:
```
for direc in */; do
  echo "$direc"
done
```

---

### Post by xx77aBs on 2010-01-01
wow, I didn't know about that, thank you !! :)

---

