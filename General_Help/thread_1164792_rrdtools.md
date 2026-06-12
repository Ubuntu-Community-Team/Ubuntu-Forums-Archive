---
title: "rrdtools"
date: 2009-05-20
forum: General Help
---

### Post by bperucchi on 2009-05-20
My syslog.log is full of this message below

May 20 01:52:19 go2b-server collectd[4902]: uc_update: Value too old: name = go2b-server/df/df-root; value time = 1242795139; last cache update = 1242795139;
May 20 01:52:19 go2b-server collectd[4902]: rrdtool plugin: (rc->last_value = 1242795139) >= (value_time = 1242795139)

Each 10 seconds this message are repeat.

---

### Post by KhurramM on 2009-05-20
One way around is to delete this file at some interval say 1minute using cron.

But the root of your problem has to be dug out. Cant help u here.

---

