---
title: "Problem Starting Programs sometimes"
date: 2006-02-05
forum: Desktop Environments
---

### Post by cobravap on 2006-02-05
hey guys i just reinstalled Ubuntu and i am having problems starting programs sometimes. The first time it was firefox, it would say loading firefox and then nothing would load. Then it would say firefox is already running and then not load. I went to system monitor and then closed it and now it works. But now Synaptic wont load (even through terminal) I get this in the terminal : FATAL: File /etc/gksu.conf is not owned by root.

Any idea on what is wrong?

Thanks guys.

---

### Post by cdhotfire on 2006-02-05
```

$ sudo chown root /etc/gksu.conf

```

???

---

### Post by taurus on 2006-02-05
Maybe next time you try to run firefox from a terminal to see if there is any error message.  Open a terminal and at the prompt, type

firefox &

---

