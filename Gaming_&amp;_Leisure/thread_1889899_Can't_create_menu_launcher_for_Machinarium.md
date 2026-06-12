---
title: "Can't create menu launcher for Machinarium?"
date: 2011-12-02
forum: Gaming &amp; Leisure
---

### Post by Inkpot on 2011-12-02
I have the Machinarium folder located in my home folder and if I run the executable from there, the game starts up just fine. But, for some reason trying to create a menu launcher linking to that exact same file results in nothing but a black screen. Any ideas?

---

### Post by Perfect Storm on 2011-12-02
What did you add as a command in the launcher?

---

### Post by Inkpot on 2011-12-02
/home/<my user name>/Machinarium/Machinarium

---

### Post by Perfect Storm on 2011-12-02
Try instead;
```
sh -c "cd ~/Machinarium && ./Machinarium"
```

first try it via the terminal, then as a launcher command.

---

### Post by Inkpot on 2011-12-02
> **Artificial Intelligence said:**
> Try instead;
```
sh -c "cd ~/Machinarium && ./Machinarium"
```

first try it via the terminal, then as a launcher command.

That worked like a charm! Thank you so much! Would you mind explaining what that just did and where I went wrong before? I'd greatly appreciate it! :)

---

