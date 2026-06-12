---
title: "How to prevent closing terminals from closing child process?"
date: 2007-05-12
forum: Desktop Environments
---

### Post by greatman on 2007-05-12
On my ubuntu, I open my IntelliJIdea as such: 

    ./idea.sh

But as soon as I close the Terminal window, Idea stops.  So I thought, maybe I need to run it as a background process? 

    ./idea.sh &

Closed Terminal, Idea stopped again.  Looking into System Monitor and realized Idea (or actually, "java" is the process) is a child of the Terminal.  So it seems when I close a parent process, the child stops as well.  Is there a way to prevent that? 

For some reason, I've never run into this on other Linux/Unix installations I've used.  Using '&' allows process to run independently of the Terminal.  Maybe it's specific o Java? 

Any help appreciated.

---

### Post by Rinzwind on 2007-05-12
Try
nohup ./idea.sh &

:)

---

### Post by taurus on 2007-05-12
```
NOHUP ./idea.sh
```

---

