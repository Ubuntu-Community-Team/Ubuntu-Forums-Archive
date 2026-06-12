---
title: "Any way to display only folders with ls command?"
date: 2009-06-05
forum: General Help
---

### Post by Buttons840 on 2009-06-05
When I run the command```
cd / ; ls -d
```it returns```
.
```

Is this normal?  Is there any way to list only the "folders."

Thanks.

---

### Post by Tibuda on 2009-06-05
That's strange. Does not work with me too.
You can also use ```
find -maxdepth 1 -type d
``` but it does not uses columns, and shows hiddens dirs.

---

### Post by Buttons840 on 2009-06-05
I've also tried "ls -l | grep ^d" which works, but the formating is not desired.

I would like a simple output, like the standard ls command gives, but that only show the "folders."

Seems a feature that could be commonly used, I'm surprised at the difficulty of it.

---

### Post by blueridgedog on 2009-06-05
Try:

```
ls -d */
```

---

### Post by Tibuda on 2009-06-05
That was simple! Thanks blueridgedog!

---

### Post by Buttons840 on 2009-06-05
> **blueridgedog said:**
> Try:

```
ls -d */
```

Explain what is happening here.

---

### Post by blueridgedog on 2009-06-05
> **Buttons840 said:**
> Explain what is happening here.

ls -> list files
-d ->  man page states list directories, but I think that is off and it restricts the depth
*/ -> pattern matches any directory name since they all end in a slash

If you like, you can

```
ls -dal */
```

---

