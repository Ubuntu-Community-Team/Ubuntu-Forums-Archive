---
title: "how to setup JDK_HOME???"
date: 2006-07-30
forum: Desktop Environments
---

### Post by fouadk on 2006-07-30
i use intellij idea to develop java software...im used to the windows version since im new to linux...
i downloaded intellij and when i try to use it it says that it cant find JDK_HOME...
how can i solve this ???

---

### Post by Tomosaur on 2006-07-30
type this into a terminal for a temporary fix:

```

export JDK_HOME=<whichever directory you have your jdk/bin/>

```

And to fix it permenantly, edit your /home/<you>/.bashrc file so that it has the following lines at the bottom:

```

# add extra paths
export PATH=$PATH:/bin/java/jdk1.5.0_07/bin
export JDK_HOME=/bin/java/jdk1.5.0_07

```

Obviously, alter it so that they point to the right directories. Log out and log back in for the changes to take effect.

---

