---
title: "help with background processes"
date: 2009-03-16
forum: General Help
---

### Post by DeepSeaNautilus on 2009-03-16
I want to open through the terminal two image files  with eye of gnome at the same time, and then get back my terminal. 
I am trying with this:
```
$ eog image.jpg &; eog image.png &
```
But it doesn't work, how can I fix this?

---

### Post by khelben1979 on 2009-03-16
I don't know how to do that, but why not just choose 2 files from the list while the program has been opened?

---

### Post by Berserker v7 on 2009-03-16
instead of trying to combine both the commands, just give them separately one after the other

$ eog image1.jpg &
$ eog image2.jpg &
$

---

### Post by DeepSeaNautilus on 2009-03-16
Because it is easier to open several files with the terminal rather than searching with a gui in the file system.

---

### Post by DeepSeaNautilus on 2009-03-16
> **Berserker v7 said:**
> instead of trying to combine both the commands, just give them separately one after the other

$ eog image1.jpg &
$ eog image2.jpg &
$

Thanks, I know I can do it that way, but I was hoping I could do it ina single line.

---

### Post by Cheesehead on 2009-03-16
This should fail with an error: "bash: syntax error near unexpected token `;'" - dash doesn't like the '&;' together. ```
$ eog image.jpg &; eog image.png &
```

This will open one image at a time, the second opening only after the first is closed.```
$ eog image.jpg && eog image.png &
``` 

Or you can try it without the semicolon, which works wonderfully for me.```
$ eog image.jpg & eog image.png &
```

---

### Post by DeepSeaNautilus on 2009-03-16
> **Cheesehead said:**
> This should fail with an error: "bash: syntax error near unexpected token `;'" - dash doesn't like the '&;' together. ```
$ eog image.jpg &; eog image.png &
```

This will open one image at a time, the second opening only after the first is closed.```
$ eog image.jpg && eog image.png &
``` 

Or you can try it without the semicolon, which works wonderfully for me.```
$ eog image.jpg & eog image.png &
```

Thanks very much :D, but I still don't understand why it doesn't work without semicolon, since they are two separate instructions and as far as I know the semicolon is needed to separate several instructions in a single line.

---

