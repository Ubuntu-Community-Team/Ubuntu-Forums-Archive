---
title: "chnge a folder ownership"
date: 2009-04-16
forum: General Help
---

### Post by Vishnu V on 2009-04-16
When i tried to run far manager from my administrative account(vishnu) using the command

sudo wineconsole --backend=user far.exe

i got the error message
wine: /home/vishnu/.wine is not owned by you

how can i sokve this problem ???
I can run it from 'root'

Sorry for asking this simple doubt

Thanks in advance

---

### Post by squaregoldfish on 2009-04-16
sudo chown -r vishnu:vishnu /home/vishnu/.wine

---

### Post by aaronp on 2009-04-16
> **Vishnu V said:**
> When i tried to run far manager from my administrative account(vishnu) using the command

sudo wineconsole --backend=user far.exe

i got the error message
wine: /home/vishnu/.wine is not owned by you

how can i sokve this problem ???
I can run it from 'root'

Sorry for asking this simple doubt

Thanks in advance

Unusual that it wouldn't be owned by you but try this:

```
sudo chown vishnu ~/.wine
```


hth
Aaron

---

