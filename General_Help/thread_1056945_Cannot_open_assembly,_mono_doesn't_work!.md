---
title: "Cannot open assembly, mono doesn't work!"
date: 2009-02-01
forum: General Help
---

### Post by KanineN on 2009-02-01
Hello! When I am trying to use mono in ubuntu 8.10 i get this error code

```
Cannot open assembly
```

How do I fix it?

---

### Post by directhex on 2009-02-01
> **KanineN said:**
> Hello! When I am trying to use mono in ubuntu 8.10 i get this error code

```
Cannot open assembly
```

How do I fix it?

Give a useful report, perhaps?

What app are you trying to run? What's the FULL error report? What command are you running?

---

### Post by KanineN on 2009-02-01
The command i am using is 


```
mono namne_of_file.exe
```

and the error I get is

```
Cannot open assembly name_of_file.exe
```

---

### Post by directhex on 2009-02-01
> **KanineN said:**
> The command i am using is 


```
mono namne_of_file.exe
```

and the error I get is

```
Cannot open assembly name_of_file.exe
```

What does "monodis --assemblyref name_of_file.exe" report?

---

### Post by KanineN on 2009-02-01
> **directhex said:**
> What does "monodis --assemblyref name_of_file.exe" report?

```
Error while trying to process name_of_file.exe
```

---

### Post by directhex on 2009-02-01
> **KanineN said:**
> ```
Error while trying to process name_of_file.exe
```

I don't think this is a CLI assembly.

What does "file name_of_file.exe" report?

A CLI assembly OR a 64-bit Windows app will say:
"MS-DOS executable PE  for MS Windows (GUI) Intel 80386 32-bit, Mono/.Net assembly"

A 32-bit Windows app will say:
"MS-DOS executable PE  for MS Windows (GUI) Intel 80386 32-bit"

---

### Post by KanineN on 2009-02-01
> **directhex said:**
> I don't think this is a CLI assembly.

What does "file name_of_file.exe" report?

A CLI assembly OR a 64-bit Windows app will say:
"MS-DOS executable PE  for MS Windows (GUI) Intel 80386 32-bit, Mono/.Net assembly"

A 32-bit Windows app will say:
"MS-DOS executable PE  for MS Windows (GUI) Intel 80386 32-bit"

That's what it says. 

"error while trying to process"

---

### Post by XanTrax on 2009-02-01
> **KanineN said:**
> That's what it says. 

"error while trying to process"

When you type

```

file name_of_file.exe

```

WHERE name_of_file.exe is the NAME of the file you are trying to execute with mono command, what happens?  It says "error while trying to process"?

What happens when you try to run

```

wine name_of_file.exe

```

where name_of_file.exe is the NAME of the file YOU are trying to execute.

---

