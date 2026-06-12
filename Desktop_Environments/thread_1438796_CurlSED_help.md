---
title: "Curl/SED help"
date: 2010-03-25
forum: Desktop Environments
---

### Post by yeleek on 2010-03-25
Hi,

I've this line of 'code'

```
curl -s "http://www.mcafee.com/us/threat_center/default.asp" | grep "Global Threat Condition" | sed -e 's/critical-image-date.*//' | sed -e s/'McAfee Labs'//g -e s/'Global Threat Condition'//g | sed -e :a -e 's/<[^>]*>//g;/</N;//ba' | sed -e 's/^[ \t]*//' | tr -d '\r'

```

Which is pulling the status out of Mcafee.com, however its also pulling some carriage return or something which I just cannot remove.  Can someone help me please?

Thanks

---

### Post by yeleek on 2010-03-26
Anyone?

---

### Post by yeleek on 2010-03-26
Blooming thing...  fixed it

```
curl -s "http://www.mcafee.com/us/threat_center/default.asp" | grep "Global Threat Condition" | sed -e 's/critical-image-date.*//' | sed -e s/'McAfee Labs'//g -e s/'Global Threat Condition'//g | sed -e :a -e 's/<[^>]*>//g;/</N;//ba' | sed -e 's/^[ \t]*//' | sed 's/.$//' | tr -d '\n'
```

---

