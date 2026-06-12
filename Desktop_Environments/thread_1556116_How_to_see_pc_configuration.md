---
title: "How to see pc configuration"
date: 2010-08-19
forum: Desktop Environments
---

### Post by smtouhid on 2010-08-19
Dear,
How can i see my full configuration from ubuntu 10.04. I want to know my MB & Processor  model manufacturer, HDD , RAM.

How can I see these in ubuntu 10.04.


/touhid

---

### Post by rcayea on 2010-08-19
Go to synaptic and install a piece of software called, Hardinfo. Then you can find the program under System Tools. It will be called, System Profiler and Benchmark.

---

### Post by bigsmitty64 on 2010-08-19
You could also go to :
```
system> administration> system monitor

```It gives that info you want on the "system" tab.

---

### Post by stinkeye on 2010-08-19
....or in the terminal
```
sudo lshw -html > lshw.html
```
Will create a html file in your home folder which you can view in your browser.

---

