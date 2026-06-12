---
title: "Command that will print last line"
date: 2009-01-21
forum: General Help
---

### Post by hardysummer on 2009-01-21
I need a command that will print just the last line of a file.  Prefer a short code.

---

### Post by snova on 2009-01-21
```
tail -n1 <file>
```

tail = command to print the last lines of a file
-n**1** = specifies to only print the last **1**

---

### Post by iaculallad on 2009-01-21
> **hardysummer said:**
> I need a command that will print just the last line of a file.  Prefer a short code.

On your terminal:

```
tail -n**[COLOR="DarkRed"]X[/COLOR]** filename
```

X represents the number of line to display. So to display the last line of a file, do:

```
tail -n1 filename
```

for more information on tail:

```
man tail
```

EDIT: Just make sure that no newlines are present on the very last part of your file as executing the command above will just give you blank result.

---

### Post by hardysummer on 2009-01-24
So if there is going to be new lines at the bottom, how do I get the last line?

The file will be constantly written to automatically. And I would like to get the updated information on the last line.

---

### Post by dcstar on 2009-01-25
> **hardysummer said:**
> So if there is going to be new lines at the bottom, how do I get the last line?

The file will be constantly written to automatically. And I would like to get the updated information on the last line.

```
tail -f filename
```

---

