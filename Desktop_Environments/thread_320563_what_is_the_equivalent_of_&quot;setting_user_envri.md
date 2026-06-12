---
title: "what is the equivalent of &quot;setting user envrionment variables of windows&quot; on ubuntu?"
date: 2006-12-17
forum: Desktop Environments
---

### Post by volkan kepoglu on 2006-12-17
I am very new user. I installed dapper 6.06 on amd64 at 3 days ago and downloaded java. I am quite sure whether I installed java or not, how can I check that java 2 sdk standard edition is properly installed? 

My real question is how can I set JAVA_HOME variable as PATH in the user defined environment settings?

---

### Post by jpkotta on 2006-12-17
If this is in the terminal, you would add a line like```
JAVA_HOME=/path/to/java
``` to your ~/.bashrc file.  To add a directory to the PATH variable, you do```
PATH=$PATH:/my/new/path
```

If this is something that should apply outside terminals, then I think the correct place is ~/.bash_profile or ~/.xsession or ~/.xinitrc

---

