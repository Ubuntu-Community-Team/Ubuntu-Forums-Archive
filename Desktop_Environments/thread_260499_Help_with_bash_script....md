---
title: "Help with bash script..."
date: 2006-09-18
forum: Desktop Environments
---

### Post by 1337 on 2006-09-18
Hello I'm newbie in bash scripts but I want to make a script that trigger action when it will check some info via dmesg. In other words I want to put it in rc.local, this script will do "dmesg | grep -i 640" if number 640 is present in dmesg it will run a /path/to/program/program, if you know what I mean. The best way would be also if the number 640 isnt present then wait and do dmesg check again. Please give me some examples of that script.

Regards

---

### Post by LotsOfPhil on 2006-09-19
I'd just write this script and then use cron to make it run as often as you need to check dmesg.

Obviously replace echo "dmesg ...  with what you want to run.

```
#!/bin/sh
#
# Check dmesg for 640
#
qzb=`dmesg | grep -c 640`
if [ $qzb -ne 0 ]
then
  echo "dmesg has 640 in it, what now?"
  exit 1
else
  exit 1
fi
```

---

### Post by 1337 on 2006-09-19
Thanks, I'm grateful for your support.

Regards

---

### Post by Ramses de Norre on 2006-09-19
Why do you exit with 1? That's an erroneous exit.. I think you'll want to change that to exit 0.

---

### Post by LotsOfPhil on 2006-09-19
Right, oops. I was just changing an old script. "exit 0" it is.

---

