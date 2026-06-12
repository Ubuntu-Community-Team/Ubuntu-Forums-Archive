---
title: "program path"
date: 2010-08-27
forum: Desktop Environments
---

### Post by houshdaran on 2010-08-27
Hello.I have installed some programs trough the ubuntu software center..now I don't know where they are installed.how to figure it out?

---

### Post by aweber on 2010-08-27
Does this help?

Ubuntu Software Center > Installed Software > Click the program you're interested in - Chromium Web Browser for example > Click More Info. 

In the bottom right corner you should see the program name in gray text within parentheses, for example (chromium-browser). Noting that, open Applications > Accessories > Terminal and type

```
dpkg -L chromium-browser
```

You should see a list of that program's installed files.

---

### Post by GregBrannon on 2010-08-27
You can also use the whereis command in a terminal window:

```
> whereis firefox 
```

---

