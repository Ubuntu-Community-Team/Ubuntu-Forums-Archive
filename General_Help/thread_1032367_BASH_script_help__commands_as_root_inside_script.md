---
title: "BASH script help / commands as root inside script \"
date: 2009-01-06
forum: General Help
---

### Post by max_power on 2009-01-06
im writing a script that will mount samba shares and then run rsync to back them up locally. 

i have 2 issues. 

Im getting an error when the script checks for root. When the script is NOT run as root the script performs the correct action but if the user IS root i get an error

Here is the root check code:
```
# make sure we're running as root
if (( `$ID -u` != 0 )); then { $ECHO "Sorry, must be root.  Exiting...";exit; } fi;
```

when run as root i get this message:
*25: 0: not found*

which i assume means there is a error on line number 25 (which is the line of the root check)


Now my second issue is i need to be able to mount the shares as root in the script currently my code is this:
```

SMBMOUNT=/usr/bin/smbmount;
MYSERVER="//10.0.0.8/Recovered/ /mnt/servers/mysserver -o credentials=/root/.credentials,uid=1000,mask=000";

$SMBMOUNT $MYSERVER;

```

The error i get:
*mount error 13 = Permission denied *


Any help?

Thanks

---

### Post by alarme on 2009-01-06
For the first issue, you can try:

#!/bin/bash

# make sure we're running as root
if [ "$UID" != "0" ]; then
	echo "Sorry, must be root.  Exiting..."
	exit
fi

---

### Post by max_power on 2009-01-06
> **alarme said:**
> For the first issue, you can try:

#!/bin/bash


Thanks that fixed my first issue.

---

