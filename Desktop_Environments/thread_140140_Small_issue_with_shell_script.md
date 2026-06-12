---
title: "Small issue with shell script"
date: 2006-03-05
forum: Desktop Environments
---

### Post by MichaelZ on 2006-03-05
Hello,

I have a minor issue with a shell script (in Windows would be a .bat file). I cannot start it from the terminal. The terminal says

> update: command not found

Anyway, I can execute it by using the File Browser and chosing to run it in a Terminal. The problem is that something goes wrong and after execution the terminal is automatically closed. And I cannot check which was(were) the problem(s).

How could I start the shell script from the terminal?

Thank you very much.

Best wishes,
Michael

---

### Post by MichaelZ on 2006-03-05
Hello,

It seems to work when I use:

> bash update

But I am not sure if this is the correct way.

Best wishes,
Michael

---

### Post by schilcha on 2006-03-05
try ```
./update
```if you're in the same directory as the script. Usually "." (the current dir) is not part of your path, so bash will not look for executables in the directory your sitting in.

---

### Post by MichaelZ on 2006-03-05
Thank you very much for the suggestion:) .

Best wishes,
Michael

---

