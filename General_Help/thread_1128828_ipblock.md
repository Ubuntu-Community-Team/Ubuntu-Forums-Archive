---
title: "ipblock"
date: 2009-04-18
forum: General Help
---

### Post by mikeyd612 on 2009-04-18
Yo, I just upgraded to 9.04 and so far it seems to be working pretty well. However I appear to be having a problem with IPblock. It worked great for me for over a year but not anymore. I was using the 0.24 version up until now and thought that the latest 0.25 version might solve the problem. But it keeps giving me the message "touch: missing file operand". Any ideas of what this might mean? I tried reinstalling and looking online but didn't find much. Any ideas for a solution or an alternative??? Thanks

---

### Post by uljanow on 2009-04-18
It looks like you're using an old config. Try the default configuration file:

```
sudo cp /usr/share/doc/iplist/examples/ipblock.conf /etc
```

---

