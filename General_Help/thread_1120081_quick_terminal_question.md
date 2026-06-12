---
title: "quick terminal question"
date: 2009-04-08
forum: General Help
---

### Post by imaginarythomas on 2009-04-08
I have a directory with and ampersand in the folder name. How can I escape it?

ex: cd /projects/b&b/

and I get
bash: cd: lushconcepts/projects/b: Not a directory
[1] 26281
bash: b/: No such file or directory
[1]+  Exit 1                  cd lushconcepts/projects/b

---

### Post by unutbu on 2009-04-08
```
cd "/projects/b&b/"
```

You might want to think about changing the directory name. 
Having things like spaces and ampersands in file and directory names makes writing commands (and scripts) a bit harder to do properly.

---

### Post by imaginarythomas on 2009-04-08
I am using it for a script actually :P

It's a folder I pulled off a server so to out it back I should really keep the same structure.

---

### Post by coffeecat on 2009-04-08
You can also escape it with a backslash.

```
cd /projects/b\&b/
```

---

### Post by kryptikos on 2009-04-08
In the bash environment you use a back slash '\'.

ie. you have a file: some&file.txt

if you wanted to display the contents you would issue:

**less some\&file.txt**

---

### Post by imaginarythomas on 2009-04-08
Perfect!

Thanks guys

---

