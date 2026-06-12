---
title: "Quick help with mv"
date: 2009-06-04
forum: General Help
---

### Post by ranthal on 2009-06-04
I have a file whose name starts with a '-' so when I try to mv it to rename it (so it's easier to scp it later) it interprets the - as indicating an option and complains.  What's the solution to this?

I've tried to us a regex and a couple other options I've found online but can't seem to get the right one.  Thanks

---

### Post by pastalavista on 2009-06-04
> **ranthal said:**
> I have a file whose name starts with a '-' so when I try to mv it to rename it (so it's easier to scp it later) it interprets the - as indicating an option and complains.  What's the solution to this?

I've tried to us a regex and a couple other options I've found online but can't seem to get the right one.  Thanks


 put "-quotation marks" around the file name

---

### Post by DeMus on 2009-06-04
> **ranthal said:**
> I have a file whose name starts with a '-' so when I try to mv it to rename it (so it's easier to scp it later) it interprets the - as indicating an option and complains.  What's the solution to this?

I've tried to us a regex and a couple other options I've found online but can't seem to get the right one.  Thanks

Did you try to put the name between "quotes"?

---

### Post by ranthal on 2009-06-04
Crap just got it, of course the second after I posted.  For anyone who needs it in the future begin the filename with "./" to indicate the current directoy, then it will not treat the following '-' as an option.

---

### Post by Celauran on 2009-06-04
```
mv ./-filename newfilename
```

---

### Post by michy99 on 2009-06-04
Use the whole path of the file.```
mv /path/of/file/filename newpath
```

---

### Post by ranthal on 2009-06-04
> **pastalavista said:**
> put "-quotation marks" around the file name

FYI tried that including aswell as ".filename" to interpret the '.' as a single character for a regex and still didn't like it.

---

### Post by TopGun21 on 2009-06-04
Plkease read the manual  and info pages.
 
Example: mv
 
```
man mv
```

---

### Post by Celauran on 2009-06-04
> **TopGun21 said:**
> Plkease read the manual  and info pages.
 
Example: mv
 
```
man mv
```

Quite the first post. Also, can you show me where in the mv man page it addresses this? Because I sure don't see it...

---

