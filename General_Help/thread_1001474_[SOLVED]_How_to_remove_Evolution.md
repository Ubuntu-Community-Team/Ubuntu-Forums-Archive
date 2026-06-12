---
title: "[SOLVED] How to remove Evolution"
date: 2008-12-04
forum: General Help
---

### Post by Terry@nz on 2008-12-04
Every time I try to remove Evolution from my computer, I am left with absolutely **nothing** on the desktop, not even a drop-down menu. 

Is it possible to remove Evolution? It is a program I will never use on this machine.

Terry

---

### Post by sstusick on 2008-12-04
You can remove it by using Synaptic package manager. I've successfully removed it without any problems.

---

### Post by Terry@nz on 2008-12-04
That is how I did remove it. It worked for me too. But it removed everything else too. That is what I didn't want.

Terry

---

### Post by slowth5 on 2008-12-04
Hi Terry, I had the same issue when I used Synaptic to remove Evolution, so I use apt-get instead. It seems to work just fine.

```
sudo apt-get autoremove evolution
```

---

### Post by Terry@nz on 2008-12-04
Thanks, slowth5. Worked perfectly.
BTW - for the sake of anyone coming here later and using your suggestion - it is 'evolution', lower-case.

One last thing: having removed evolution, I still have the evolution icon in Applications/office. It points nowhere, and a right-click offers possibilities only to add to panel, add to desktop or adding the entire menu to the panel. Probably easy, except I don't know how.

Terry

---

### Post by RequinB4 on 2008-12-04
> **Terry@nz said:**
> Thanks, slowth5. Worked perfectly.
BTW - for the sake of anyone coming here later and using your suggestion - it is 'evolution', lower-case.

One last thing: having removed evolution, I still have the evolution icon in Applications/office. It points nowhere, and a right-click offers possibilities only to add to panel, add to desktop or adding the entire menu to the panel. Probably easy, except I don't know how.

Terry

Right click the ubuntu symbol and edit menus

---

### Post by sstusick on 2008-12-04
> **slowth5 said:**
> Hi Terry, I had the same issue when I used Synaptic to remove Evolution, so I use apt-get instead. It seems to work just fine.

```
sudo apt-get autoremove Evolution
```
That worked perfectly for me too. Thanks!

---

### Post by Terry@nz on 2008-12-04
Thanks, sstusick.

I feel I am getting the hang of Ubuntu. It's a great distro.

Now. One last thing: how do I put [solved] on the subject line?

Terry

---

### Post by RequinB4 on 2008-12-04
> **Terry@nz said:**
> Thanks, sstusick.

I feel I am getting the hang of Ubuntu. It's a great distro.

Now. One last thing: how do I put [solved] on the subject line?

Terry

Go to the top of the first page, under thread tools

---

### Post by Terry@nz on 2008-12-05
Today I am thick 8-(
I wondered why I couldn't even see 'Mark this thread solved'.
Oh Yes! you have to be logged in. Makes sense.

Thanks all.

Terry

---

### Post by dcstar on 2008-12-05
> **Terry@nz said:**
> That is how I did remove it. It worked for me too. But it removed everything else too. That is what I didn't want.


Removing anything that is part of a meta-package and agreeing to remove the other packages will do exactly that.

Evolution is part of the ubuntu-desktop meta-package, so you should have seen a message saying other components were also being removed.

---

