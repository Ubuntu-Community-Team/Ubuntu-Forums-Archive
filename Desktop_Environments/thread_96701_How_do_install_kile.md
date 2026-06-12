---
title: "How do install kile?"
date: 2005-11-29
forum: Desktop Environments
---

### Post by neural_dream on 2005-11-29
I've installed kubuntu for the sole purpose of installing kile. To cut a short story even shorter I failed. What does one need to do? just give me the steps :D.

I suppose:
go to the kile website.
download the source.
./configure. That's where I fail. It says "checking for C compiler default output file name... configure: error: C compiler cannot create executables".
...


An easier solution would be that you tell me how to install it with apt-get or synaptic since I can't find it. Which one is the correct repository

Very demanding for a first post, I know :rolleyes: .

---

### Post by Corvillus on 2005-11-29
```
sudo gedit /etc/apt/sources.list
```
Uncomment the lines for the universe and multiverse repositories.
```
sudo apt-get install kile
```
There's no need to compile it from source.

EDIT: Didn't realize you were using Hoary, in that case i'm not sure if it's in the repos.

---

### Post by neural_dream on 2005-11-29
That did it. Thanx Corvillus. It was much simpler than I thought. As for the hoary links, oops, one more of my mistakes. I'll remove it from the original post to save other noobs from similar mistakes :). Thanks again.

---

