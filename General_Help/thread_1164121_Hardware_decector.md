---
title: "Hardware decector"
date: 2009-05-19
forum: General Help
---

### Post by jo$h on 2009-05-19
Hello i am looking for a program that tells you all of your hardware such as ram graphics card ect i am using ubuntu 9.04 i tried system monitor but it only told me how much resources are being used.

Specs.

Dell inspiron 1525

---

### Post by dhughes on 2009-05-19
> **jo$h said:**
> Hello i am looking for a program that tells you all of your hardware such as ram graphics card ect i am using ubuntu 9.04 i tried system monitor but it only told me how much resources are being used.

Specs.

Dell inspiron 1525

Try this ```
sudo lshw
```

---

### Post by jo$h on 2009-05-19
Woah thank you ok problem solved.

---

### Post by ActiveFrost on 2009-05-19
```
cd $HOME
sudo lshw -html > comp_spec.html

```
Now, open your home directory and launch comp_spec.html ( which should open you a new browser window/tab ) ;)

---

### Post by colau on 2009-05-19
+1 for dhughes

---

### Post by coffeecat on 2009-05-19
> **ActiveFrost said:**
> ```
cd $HOME
sudo lshw -html > comp_spec.html

```

Excellent tip. Until now I've been doing:

```
sudo lshw > lshw.txt
```... which is effective but crude. I much prefer the html output. Thanks. :)

---

### Post by wiebeest on 2009-05-19
> **ActiveFrost said:**
> ```
cd $HOME
sudo lshw -html > comp_spec.html

```Now, open your home directory and launch comp_spec.html ( which should open you a new browser window/tab ) ;)

+1
Damn good tip! Thanks!

Greets,

Wiebeest

---

### Post by bacardiandwatermelon on 2009-05-19
If you want something with a gui you could try [http://www.getdeb.net/app/Hardinfo](http://www.getdeb.net/app/Hardinfo) It sits under System->Preferences->System Profiler and Benchmark.

---

### Post by wiebeest on 2009-05-19
> **bacardiandwatermelon said:**
> If you want something with a gui you could try [http://www.getdeb.net/app/Hardinfo](http://www.getdeb.net/app/Hardinfo) It sits under System->Preferences->System Profiler and Benchmark.

How about ***Sysinfo*** (from synaptic)?

---

