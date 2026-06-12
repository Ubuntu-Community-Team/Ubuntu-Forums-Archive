---
title: "Launcher for more than one program"
date: 2010-05-04
forum: Desktop Environments
---

### Post by rogerdean on 2010-05-04
Hello all

I'd like to make a launcher that starts a couple of programs at once. When I switch my brain into 'work mode' I'd like one click to start evolution, firefox and sunbird. Does anyone know how this'd work?

Many thanks
Roger

---

### Post by 3rdalbum on 2010-05-04
Create a text file somewhere. The first line should be:

```
#!/bin/sh
```

The subsequent lines should consist of a program that you want to run, followed by an ampersand, like so:

```
#!/bin/sh
evolution &
firefox &
sunbird
```

You need to make it executable by right-clicking it in the file browser, choosing Properties and then clicking "Allow executing as a file".

Create a launcher in your panel. Next to the 'command' field there's a Browse button. This is where you select the script you just made.

---

### Post by rogerdean on 2010-05-04
Magic! Thanks very much indeed
Roger

---

