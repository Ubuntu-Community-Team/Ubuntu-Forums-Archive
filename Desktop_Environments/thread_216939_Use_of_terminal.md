---
title: "Use of terminal"
date: 2006-07-16
forum: Desktop Environments
---

### Post by Oddvar on 2006-07-16
How to keep a terminal program in open window after the commands complete? I have terminal command df -h in my top panel, but when its finished the window close at once. No chance to see what was the response....

---

### Post by jayemef on 2006-07-16
There might be a better way, but a quick and dirty way is to simply use read:
```
#!/bin/bash

df -h
read
```
read just looks for a response from standard input, so you could either press enter or hit the close window button to get rid of your window.

---

### Post by Ramses de Norre on 2006-07-16
As a command that would be ```
df -h; read
```

---

