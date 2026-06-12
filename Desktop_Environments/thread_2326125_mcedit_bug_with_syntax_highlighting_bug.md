---
title: "mcedit bug with syntax highlighting bug"
date: 2016-05-28
forum: Desktop Environments
---

### Post by CrewDK on 2016-05-28
Hallow. 

 I got simple script 

```
#!/bin/bash

if [ -e ~/passwd.txt ]; then
  BDPASS=$(grep "MySQL" /root/passwd.txt | awk '{print $4}')
else
  BDPASS=123456798
fi

BDUSER=root
TOPATH=/root/
TOFILE=$(date "+%Y.%m.%d.%H.%M.%S").sql

for BDNAME in $(mysql -u${BDUSER} -p${BDPASS} --execute="SHOW DATABASES;" | grep -v -E "(Database|information_schema|mysql|performance_schema|phpmyadmin)"); do 
    mysqldump -u${BDUSER} -p${BDPASS} ${BDNAME} | gzip > ${TOPATH}/${BDNAME}_${TOFILE}.gz
done
```

...and if i paste this code into some big script after last double quote everything looks like comment or something. 

[ATTACH=CONFIG]269345[/ATTACH]

Is there any way i can fix that or i did something wrong?

---

