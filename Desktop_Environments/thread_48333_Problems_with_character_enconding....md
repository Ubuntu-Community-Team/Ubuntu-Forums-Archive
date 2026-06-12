---
title: "Problems with character enconding..."
date: 2005-07-12
forum: Desktop Environments
---

### Post by dierre on 2005-07-12
Hi...

I have been given the source of a java project that I need to compile with sun's netbeans.

The problem is that the source, being written by Italian people, contains accented characters, both in the comments and the identifiers.

These characters do not render correctly. (I wish to point out that I configured my ubuntu box to use Italian locale as well) When I try to compile I get lots of errors like: 

```
warning: unmappable character for encoding UTF8
```
and
```
illegal character: \65533
```

And if i use the 'file' command with any of those source files, I get:
```
ISO-8859 Java program text
```

Yes, I know that the good practice would be not to use the accented letters in the source code -- but I need to compile the project quickly -- is there any way to quickly convert those files so that they may be read by my ubuntu?

THANK YOU!

---

### Post by Rhawi Dantas on 2005-09-27
I do have the same problem with Netbeans...
Did you solve it ?

---

### Post by Rhawi Dantas on 2005-09-27
Hi there,

Click with the right button to the *Source Packages* and go in

*Build->Compiling->Additional Compiler Options*

And JUST add **-encoding  Cp1251**

Anyway, I went searching through the internet and found that mostly russians use this format...

If I only could speak russian :rolleyes:

---

