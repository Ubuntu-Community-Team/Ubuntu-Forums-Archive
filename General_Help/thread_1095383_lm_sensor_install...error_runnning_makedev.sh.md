---
title: "lm sensor install...error runnning makedev.sh"
date: 2009-03-13
forum: General Help
---

### Post by ozark_hillbilly on 2009-03-13
this was received after running mkdev.sh; beginning installation of mainboard sensor monitoring (lm-sensors): 

root@House:/home/eld/Desktop/lm-sensors# sudo ./mkdev.sh
/dev/i2c-0
/dev/i2c-1
/dev/i2c-2
/dev/i2c-3
/dev/i2c-4
/dev/i2c-5
/dev/i2c-6
/dev/i2c-7
/dev/i2c-8
/dev/i2c-9
/dev/i2c-10
/dev/i2c-11
/dev/i2c-12
/dev/i2c-13
/dev/i2c-14
/dev/i2c-15
/dev/i2c-16
/dev/i2c-17
/dev/i2c-18
/dev/i2c-19
/dev/i2c-20
/dev/i2c-21
/dev/i2c-22
/dev/i2c-23
/dev/i2c-24
/dev/i2c-25
/dev/i2c-26
/dev/i2c-27
/dev/i2c-28
/dev/i2c-29
/dev/i2c-30
/dev/i2c-31
./mkdev.sh: line 32: b.: command not found
./mkdev.sh: line 36: c.: command not found
/dev/i2c-0
mknod: `/dev/i2c-0': File exists

Is this a critical error or can I continue to try install lm sensors?

Ed

---

### Post by khelben1979 on 2009-03-13
Why not just do this (?):
```
sudo apt-get install lm-sensors
```

---

