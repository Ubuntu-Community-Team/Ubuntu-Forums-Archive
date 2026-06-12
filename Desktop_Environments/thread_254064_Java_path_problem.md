---
title: "Java path problem"
date: 2006-09-09
forum: Desktop Environments
---

### Post by FIONEX on 2006-09-09
Hi

I installed the new JDK from sun microsystems.  I forget the command to switch the java compiler to the JDK.  If I do java --version, it says 1.4.  What was the command to switch the java command to the JDK rather than the jic?

---

### Post by darknlow on 2006-11-20
Hi,

The commands you are looking for are:

```
sudo update-alternatives --config java
```
and 
```
sudo update-alternatives --config javac
```

---

### Post by T_W on 2006-11-20
> **darknlow said:**
> Hi,

The commands you are looking for are:

```
sudo update-alternatives --config java
```
and 
```
sudo update-alternatives --config javac
```


Or 

```
update-java-alternatives --set java-1.5.0-sun
```

---

