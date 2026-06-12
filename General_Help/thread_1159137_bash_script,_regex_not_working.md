---
title: "bash script, regex not working"
date: 2009-05-14
forum: General Help
---

### Post by Druzi on 2009-05-14
I'm having a problem with one of my scripts on Jaunty, bash version 3.2-5 

The following does not work on Jaunty with bash version 3.2-5 but works fine on an older Debian machine with bash version 3.1

```

#!/bin/sh

if [[ "gsdf" =~ g* ]]; then
    echo "yes"; 
else
    echo "not";
fi

```

im getting: 
```
./test: 7: [[: not found
```

---

### Post by ibuclaw on 2009-05-14
In Ubuntu, /bin/sh points to /bin/dash, not /bin/bash as is in Debian.
```
$ ls -l $(which sh)
lrwxrwxrwx 1 root root 4 2009-04-28 15:05 **/bin/sh -> dash**

```


To change this, either update your script
```
#!/bin/bash
```
Or change the link
```
sudo ln -fs /bin/bash /bin/sh
```

Regards
Iain

---

### Post by Druzi on 2009-05-14
well, changing the first line to /bin/bash obviously worked :-D but why would the Debian machine eat that?

---

### Post by Druzi on 2009-05-14
> **tinivole said:**
> In Ubuntu, /bin/sh points to /bin/dash, not /bin/bash as is in Debian.
```
$ ls -l $(which sh)
lrwxrwxrwx 1 root root 4 2009-04-28 15:05 **/bin/sh -> dash**

```
To change this, either update your script
```
#!/bin/bash
```Or change the link
```
sudo ln -fs /bin/bash /bin/sh
```Regards
Iain


Thanks!

---

