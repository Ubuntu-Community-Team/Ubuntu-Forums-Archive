---
title: "Konsole command &quot;-e&quot; How to get to the $ prompt"
date: 2018-10-13
forum: Desktop Environments
---

### Post by shag00 on 2018-10-13
Kubuntu 18.04.01.

If I enter:
```
konsole --separate --hold --workdir / 
```
I get a new Konsole window with the cursor positioned to the right of the $ prompt, as expected at the root directory.

If I type this command:
```
konsole --separate --hold --workdir / -e ls
```
it gives the expected output but no $ prompt.

So my question is how to modify the 2nd command to produce the output and then present the $ prompt.

---

