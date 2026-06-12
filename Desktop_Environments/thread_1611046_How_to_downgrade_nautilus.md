---
title: "How to downgrade nautilus"
date: 2010-11-01
forum: Desktop Environments
---

### Post by gadolinio on 2010-11-01
Hi, all. Ubuntu 10.04 has nautilus 2.31, which has a couple of features i don't like:
·space bar doesn't open multiple folders, like ENTER does. Sometimes it's more comfortable to hit the space bar instead of the enter key. I could do this in fomer versions (ubuntu 8.10 and 9.04).
·when i copy folders or files which are called the same as the ones in the destination folder, the prompt to replace/merge has the options accept and skip, and if i want to do the same every time the soincidence of names takes place, y have to first tick "always do the same" and then click "replace", for example. In former versions of nautilus/ubuntu (8.10, 9.04 at least) the prompt had buttons replace-replace all-skip-skip all, so a single click could do the job.

How can i go back to those versions of nautilus, while still using ubuntu 10.04?
Thanks in advance!

---

### Post by aarongc on 2011-01-17
Hi Gadolinio, sorry to see you haven't gotten a reply for over a month on this one! Another annoyance in the new nautilus is that the editable text box which used to hold the file path is now replaced by a series of non-editable buttons, one for each level in the tree. This is a real pain for me because I'm used to constantly copying and pasting (well, middle-mousebuttoning) file paths.

The way to downgrade (apologies if you know this already) it would be to open Synaptic, go to Package -> Force version... and choose an older version. You will probably have to enable old repositories using Settings -> Repositories. I'm worried that it may have many old dependencies which means it will install lots of old packages. This probably wouldn't cause a problem... but I'm not going to try it just now since I'm in the middle of a project and can't afford a broken computer. Also I don't really know how integrated nautilus is to the operating system, but it's possible it would break things like the desktop for example if the old nautilus is incompatible with the new Ubuntu. Would be interested to hear if it works for you. Either way, I will probably try in a few days.

---

### Post by aarongc on 2011-01-18
Uh, wow, I feel dumb. I just realized that although the "replace / merge / skip all" button is gone, there is a new checkbox called "apply this action to all files" which does the same thing.

---

### Post by gadolinio on 2011-02-26
> **aarongc said:**
> Hi Gadolinio, sorry to see you haven't gotten a reply for over a month on this one! Another annoyance in the new nautilus is that the editable text box which used to hold the file path is now replaced by a series of non-editable buttons, one for each level in the tree. This is a real pain for me because I'm used to constantly copying and pasting (well, middle-mousebuttoning) file paths.

The way to downgrade (apologies if you know this already) it would be to open Synaptic, go to Package -> Force version... and choose an older version. You will probably have to enable old repositories using Settings -> Repositories. I'm worried that it may have many old dependencies which means it will install lots of old packages. This probably wouldn't cause a problem... but I'm not going to try it just now since I'm in the middle of a project and can't afford a broken computer. Also I don't really know how integrated nautilus is to the operating system, but it's possible it would break things like the desktop for example if the old nautilus is incompatible with the new Ubuntu. Would be interested to hear if it works for you. Either way, I will probably try in a few days.

Thanks for your reply! I knew the option "force version" existed, but had never thought about its use... I'll try it in a virtual machine one of these days, and reply what happens. 

Regarding the location bar, it was actually the first disappointment when I tried Lucid Lynx. But I could fix it, more or less, with a script that changes the location bar's behavior (change between button-mode and text-mode) with a panel launcher, which is not located exactly next to the path but at least does the job. And there's also a patch/addon/whatever called "nautilus elementary", which directly lets you re-establish that functionality. That is the final solution to the problem.

---

### Post by mihaiadrian on 2011-04-05
DO NOT DO IT. I've tryed that and I had to reinstall ubuntu.

---

