---
title: "Compiling C"
date: 2009-05-31
forum: General Help
---

### Post by Muscovy on 2009-05-31
How do you compile C in Ubuntu?

---

### Post by mikezila on 2009-05-31
gcc <input file> -o <output file>

---

### Post by Muscovy on 2009-05-31
What would the output be? I've never compiled C before.

---

### Post by mikezila on 2009-05-31
The output would be a single executable file.

The input is a plaintext file containing C source code.  Usually named "somethingorother.c", and the output is a name you choose.  The output will be created.

Are you learning C, or are you trying to compile some source that you've downloaded?  Because if you're trying to compile downloaded source, chances are it's more complicated than that.

---

### Post by Muscovy on 2009-05-31
I'm learning, not opening.
  One last question: would the output name need .something? I don't know what a Linux exectutable file type is yet...

---

### Post by mikezila on 2009-05-31
Traditionally, executables in Linux/Unix do not have an extension.

Though you do need to make it executable before you can run it.
```

chmod +x filename

```
Where filename is the compiled program, +x makes the file executable, so you can run it with:
```
./filename
```

---

### Post by ActiveFrost on 2009-05-31
> **Muscovy said:**
> I'm learning, not opening.
  One last question: would the output name need .something? I don't know what a Linux exectutable file type is yet...

As an example : 
```
gcc Source.c -o Executable
```
Now you have 2 files - Source.c ( which is your source file ) and Executable ( which is your application .. notice, without an extension ).

---

### Post by Muscovy on 2009-05-31
For <output file>, do I need an existing file or can I just call it something like cake?

---

### Post by mikezila on 2009-05-31
"cake" is fine.  It's a name that you choose.

---

### Post by Muscovy on 2009-05-31
Working, thank you!

---

### Post by Yellow Pasque on 2009-05-31
[http://pages.cs.wisc.edu/~beechung/ref/gcc-intro.html](http://pages.cs.wisc.edu/~beechung/ref/gcc-intro.html)

---

