---
title: "Beep! And: how to monitor startup errors?"
date: 2009-04-28
forum: General Help
---

### Post by wgw on 2009-04-28
I recently upgraded to Hardy and now (after some tinkering with hardware issues -- particularly ATI video) I am mostly back on track. BUT... at the end of a boot I hear a beep. So my guess is that my setup is not quite right.

Is there any way to know why it is beeping?

I have been rummaging through log files, but I'm not sure what would cause the beep. 

A thought occurred to me however: is there any command that will scour the log files and try to find possible errors?

This is an example. With:
```
cat /var/log/Xorg.0.log | grep EE
```

I get:

```
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized
```. 

Could that be the source of the beep? I would love to have a set of such commands that would extract anything fishy in the log files. Anyone have any suggestions?

Thanks!

---

### Post by freonchill on 2009-04-28
boot up or shutdown?

---

### Post by wgw on 2009-04-28
boot up is the focus for the moment.

---

