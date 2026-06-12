---
title: "Beryl: Desktop effects work; themes do not"
date: 2007-06-28
forum: Desktop Effects &amp; Customization
---

### Post by Pandemic187 on 2007-06-28
I know this topic has been touched upon countless times, but I can't figure out why Beryl isn't working properly. I have the Intel 3945 chipset and am trying to run the latest version of Beryl on Feisty. As the topic says, desktop effects work but custom themes do not. This is strange because Beryl has worked perfectly on a previous install of Feisty. Can anyone help? I know this is vague, but I can answer any question about my system/setup that may help to solve the problem. Thanks!

-Pandemic

---

### Post by speaker219 on 2007-06-28
have you tried
 beryl --replace -c emerald

---

### Post by Pandemic187 on 2007-06-28
No I have not, but, uhh...
```

bob@BobsLaptop:~$ beryl --replace -c emerald
beryl: invalid option -- c

```
Did I do something wrong?

---

### Post by Pandemic187 on 2007-06-28
Bump?

---

### Post by speaker219 on 2007-06-28
Try running
```
beryl --replace
```
and then run in another terminal
```
emerald --replace
```

---

