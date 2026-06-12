---
title: "nautilus"
date: 2009-01-30
forum: General Help
---

### Post by sridarshan on 2009-01-30
help needed,
whenever i open my 44.4gb drive ,i get the following error message
"Nautilus can't be used now, due to an unexpected error.

Nautilus can't be used now, due to an unexpected error from Bonobo when attempting to locate the factory. Killing bonobo-activation-server and restarting Nautilus may help fix the problem."

i tried restarting many times,but it dint work ..
please tell me what to do????

---

### Post by kmac on 2009-01-30
```

kyle@mafolangdick:~$ ps -ef | grep -i bonobo
kyle     [COLOR="Red"] 6282[/COLOR]     1  0 Jan28 ?        00:00:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=17

kyle@mafolangdick:~$kill 6282


```

Then open nautilus and try again.

```

kyle@mafolangdick:~$ nautilus /path/to/disk
```

---

