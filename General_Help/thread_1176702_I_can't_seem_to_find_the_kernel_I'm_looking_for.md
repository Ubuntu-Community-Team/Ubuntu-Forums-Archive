---
title: "I can't seem to find the kernel I'm looking for"
date: 2009-06-02
forum: General Help
---

### Post by kevindubrow on 2009-06-02
Hi, I need to find the 2.6.28.12-generic kernel and upgrade my 9.04 computer to it. I am using a HP Mini and I need to upgrade to get the internal microphone working.

I looked all over this website, but I can't seem to find the exact version I'm looking for: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
I'm thinking that I just don't understand the numbering system...could someone help me find the kernel I'm looking for? Thanks!

---

### Post by DeMus on 2009-06-02
> **kevindubrow said:**
> Hi, I need to find the 2.6.28.12-generic kernel and upgrade my 9.04 computer to it. I am using a HP Mini and I need to upgrade to get the internal microphone working.

I looked all over this website, but I can't seem to find the exact version I'm looking for: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
I'm thinking that I just don't understand the numbering system...could someone help me find the kernel I'm looking for? Thanks!

Open Synaptic
In menu Settings choose Repositories
On tab Updates choose the same items as I did (see image)
Now search for image in Synaptic
2.6.28.12 should be there. That's how I installed it.

---

### Post by kevindubrow on 2009-06-02
Hah, when I saw your solution I thought "man, I'm so glad its going to be that easy" and I think I jinxed myself. I have my updates tab set up the same as yours and I reloaded, but the 2.6.28.12-generic kernel does not show up in the package manager. Am I doing something wrong? Thank you!

---

### Post by DeMus on 2009-06-02
> **kevindubrow said:**
> Hah, when I saw your solution I thought "man, I'm so glad its going to be that easy" and I think I jinxed myself. I have my updates tab set up the same as yours and I reloaded, but the 2.6.28.12-generic kernel does not show up in the package manager. Am I doing something wrong? Thank you!

Just look at the attached picture: in my Synaptic I do see it.
I did choose the button Status bottom-left and top-left I choose All. It could be that those two choices do the trick.
As you can see I unloaded 2.6.28.12 again since I gave me more computation errors than I get in 2.6.28.11

---

