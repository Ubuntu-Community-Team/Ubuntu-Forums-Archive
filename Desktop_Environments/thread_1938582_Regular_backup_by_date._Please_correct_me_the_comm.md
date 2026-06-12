---
title: "Regular backup by date. Please correct me the command"
date: 2012-03-09
forum: Desktop Environments
---

### Post by Bullz3y3 on 2012-03-09
I've created a script for backup up my Zimbra folder according to this
```
http://www.youtube.com/watch?v=xhUksAhpBxw&feature=related
```But exact command doesn't seem to work on ubuntu. here's the script

```
!/bin/bash
service zimbra stop

cp -rp /opt/zimbra /zimbkp/'date+%d%m%Y'/

service zimbra start

```The copied folder will names as "date+%d%m%Y" not the date I require. Please help :(

---

### Post by athampan on 2012-03-10
You need to use backquotes:

```
cp -rp /opt/zimbra /zimbkp/`date+%d%m%Y`
```


Please note the backquote "`" instead of the single quote "'"

---

### Post by codemaniac on 2012-03-10
Wrapping 'date+%d%m%Y' in single quotes prevents shell from understanding the special meanings of command and symbols .You need use command substitution as suggested by athampan above .Below syntax you can also use :

```
cp -rp /opt/zimbra /zimbkp/$(date+%d%m%Y)
```

---

