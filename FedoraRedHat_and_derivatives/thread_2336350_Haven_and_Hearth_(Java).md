---
title: "Haven and Hearth (Java)"
date: 2016-09-07
forum: Fedora/RedHat and derivatives
---

### Post by pebbles22 on 2016-09-07
[list=1] 
[*]I've installed a .jnlp file linux client for the game Haven and Hearth. But I don't want to install Java itself, but a substitute.   Are there any substitute java programs that would open this file or do I need java?    (I tried to install OpenJDK, and while it works for Runescape, I cannot open this file with it.)   
[*] Also, I accidentally installed Ruby for my Fedora and now I don't know how to uninstall it. (I installed Ruby from source from somewhere else and didn't know I couldn't remove it.) ([https://www.ruby-lang.org/en/documentation/installation/](https://www.ruby-lang.org/en/documentation/installation/) at the very bottom Building from Source) Is there a way to remove it?   
[*]And also after I installed Ruby I now have a OpenJDK 8 Policy Tool in my applications menu. How do I get that removed? 
[/list]

---

### Post by QIII on 2016-09-07
Hello!

You will need to install a JRE (Java Runtime Environment) with a JVM (Java Virtual Machine).  That leaves you with two choices in Linux:  OpenJDK or Oracle Java.  Not that there is much difference, since Oracle is the biggest contributor to OpenJDK and OpenJDK is the open source reference implementation for Oracle Java.

Some developers do not understand this relationship and design their software to specifically check for Oracle Java.

Why do you not want to install Java?  Which release of Ubuntu are you using?

Cheers!

---

### Post by howefield on 2016-09-07
Moved to the "*Fedora/RedHat and derivatives*" forum.

---

### Post by pebbles22 on 2016-09-09
Sorry mod.  @QII: Well...I wasn't using ubuntu. I was using fedora...sorry.  Thanks though.

---

### Post by QIII on 2016-09-09
The situation remains the same:  You need either OpenJDK or Oracle Java.  What keeps you from installing Oracle Java?

---

### Post by pebbles22 on 2016-09-10
I installed fedora because my windows kept getting viruses. It finally had one that corrupted everything and I decided to use linux. I use fedora. I do not use adobeflash. I don't use java. I heard that java has security issues and the former has privacy issues. I like privacy. It makes me happy.

---

