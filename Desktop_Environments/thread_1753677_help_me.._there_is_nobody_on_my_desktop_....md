---
title: "help me.. there is nobody on my desktop ..."
date: 2011-05-09
forum: Desktop Environments
---

### Post by zm_caglar on 2011-05-09
&#305; have a problem .. &#305; download compiz fasion..and &#305; change something..when &#305; change something on compiz then &#305; can not see my toolbar on my desktop .there is nobody on my desktop.because of that &#305; can not firefoñ , command screen ... ect.
please help me..

---

### Post by Copper Bezel on 2011-05-09
Press Ctrl+Alt+T to open a terminal.

Now, run this command:

```
gconftool-2 --recursive-unset /apps/compiz-1
unity --reset
```

That should restore your Compiz settings and bring back Unity.

---

### Post by zm_caglar on 2011-05-09
> **Copper Bezel said:**
> Press Ctrl+Alt+T to open a terminal.

Now, run this command:

```
gconftool-2 --recursive-unset /apps/compiz-1
unity --reset
```

That should restore your Compiz settings and bring back Unity.

&#305; cannot open a terminal! &#305; press Ctrl+Alt+T but it is not open ...

---

### Post by Krytarik on 2011-05-09
Please see this troubleshooting guide:
[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)

Also, if you tried to enable the Cube, make sure to re-enable the "Ubuntu Unity Plugin" as the last one, after enabling the Cube and any other plugins that may have been disabled.

Greetings.

---

### Post by zm_caglar on 2011-05-09
when &#305; press /usr/share/applications/launcher & menus this come to display 

There was an error the launching application 

Details: Failed to execute child process "unity-preferences" (No such file or directory)

and ......... &#305; can not see top bar

---

