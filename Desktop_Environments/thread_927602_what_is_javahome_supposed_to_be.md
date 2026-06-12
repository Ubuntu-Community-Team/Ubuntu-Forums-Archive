---
title: "what is javahome supposed to be?"
date: 2008-09-23
forum: Desktop Environments
---

### Post by ireneshusband on 2008-09-23
I am trying to run a java app and getting the following error message:
[INDENT]robert@ermintrude:/usr/local/Jalmus$ jalmus
Unable to find a supported JDK or JRE version. Version 1.3.1 or higher is required.
Check your installation and use +javahome to specify the JDK or JRE location
[/INDENT]
Is there something missing from Debian/Ubuntu here? Or has something gone wrong with my installation?

I presume that what I am supposed to do is set the JAVA_HOME variable, but I can't work out what I am supposed to set it to. Am I on the right track here? And if so, what should the correct value be?

Many thanks in advance, good people, as always :)

---

### Post by Idefix82 on 2008-09-23
What output do you get from
```
java -version
```?

---

### Post by ireneshusband on 2008-09-23
> **Idefix82 said:**
> What output do you get from
```
java -version
```?
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) 64-Bit Server VM (build 10.0-b22, mixed mode)

---

### Post by pipepupo on 2008-12-13
I get the same error with the program Jalmus.

I readed that add in .bashrc in the HOME:

export JAVA_HOME=/usr/lib/jvm/java-6-sun/jre
export PATH=${JAVA_HOME}/bin:${PATH}

but it don't works for me.


Obtuve el mismo error con el programa Jalmus.

Lei que agregara en .bashrc en HOME:

export JAVA_HOME=/usr/lib/jvm/java-6-sun/jre
export PATH=${JAVA_HOME}/bin:${PATH}

pero esto no resolvio mi problema.

Felipe R.

---

### Post by jamesstansell on 2008-12-14
> **pipepupo said:**
> I get the same error with the program Jalmus.

I readed that add in .bashrc in the HOME:

export JAVA_HOME=/usr/lib/jvm/java-6-sun/jre
export PATH=${JAVA_HOME}/bin:${PATH}

but it don't works for me.


I've never used Jalmus before, but I downloaded and installed it and was able to run it with this command.

```
bin/jalmus-linux +javahome /usr/lib/jvm/java-6-sun/jre/

```

---

