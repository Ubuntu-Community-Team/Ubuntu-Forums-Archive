---
title: "Left click moves scroll bar to where you click"
date: 2016-05-17
forum: Desktop Environments
---

### Post by rebeltaz on 2016-05-17
Ever since I "upgraded" to Ubuntu 14.04LTS, I have noticed that on some programs, when you left click on a windows scroll bar, instead of going up or down one page like it used to, the page jumps to where you clicked. To scroll by one page at a time, I have to right-click the scroll bar instead. I was living with it, but when I allowed firefox to "upgrade" just now, it started doing that too. Since I use firefox ALL of the time, this is a real pain in my... 

Is there no way to get the scroll bar to react like it used to? I honestly do not know why program developers always want to change every freaking thing!

---

### Post by vasa1 on 2016-05-17
[Mentioned before]("http://ubuntuforums.org/showthread.php?t=2306485&p=13430990#post13430990") but ...> **enable legacy scrolling in gtk3**: edit or create *$HOME/.config/gtk-3.0/settings.ini* to have [Settings] as the first line and *gtk-primary-button-warps-slider=false* on a subsequent line by itself. This works in _most_ gtk3 applications but is said not to work in some. Alternatively, right-click instead of left-clicking works in all applications. And, if you want legacy scrolling system-wide, sudo edit */etc/gtk-3.0/settings.ini*.

**Edit**: The first useful mention I could find in UF is this: [Bizarre scrollbar behaviour in GTK3]("http://ubuntuforums.org/showthread.php?t=2198380"). I'll point to this in future :)

---

### Post by rebeltaz on 2016-05-17
God bless you! I am sorry, though... I do normally try to research for my own answers before requesting help, but in this case, I just didn't know how to search that. 

Thank you again!

---

### Post by vasa1 on 2016-05-17
If the workaround works for you, you can come back and mark this thread [SOLVED]. Here's how: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by SantaFe on 2016-05-20
I usually just press the Page Up/Page Down keys on my keyboard to achieve the same effect myself. ;)

---

