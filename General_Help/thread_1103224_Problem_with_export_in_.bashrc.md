---
title: "Problem with export in .bashrc"
date: 2009-03-22
forum: General Help
---

### Post by polargimp on 2009-03-22
I'm trying to set CLASSPATH in .bashrc using the following command 

export CLASSPATH .:$HOME/3515:$HOME/polargimp/3515/mysql-connector-java-5.0.8-bin.jar

however, when I open the terminal i get the following error

bash: export: `.:/home/polargimp/3515:/home/polargimp/polargimp/3515/mysql-connector-java-5.0.8-bin.jar': not a valid identifier


anyone know how to solve this?

polargimp

---

### Post by whollycow on 2009-03-22
> **polargimp said:**
> export CLASSPATH .:$HOME/3515:$HOME/polargimp/3515/mysql-connector-java-5.0.8-bin.jar

Wouldn't your CLASSPATH need to be followed by '='?  i.e.

```
export CLASSPATH=.:$HOME/3515:$HOME/polargimp/3515/mysql-connector-java-5.0.8-bin.jar

```

---

