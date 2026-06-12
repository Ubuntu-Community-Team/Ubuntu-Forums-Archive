---
title: "merging two terminal emulators"
date: 2012-08-20
forum: Desktop Environments
---

### Post by bencouve on 2012-08-20
I want to merge two open terminal emulators. How do I do this. Did it once by mistake so know it is possible. Thanks in advance.

---

### Post by vandorjw on 2012-08-20
ctr+t opens a new tab?

Otherwise, try terminator. It can open and display multiple terminals in a single window.

Not sure how to do it in gnome-terminal.

---

### Post by bencouve on 2012-08-21
Ok, thanks. I will take a look at terminator. Have seen it on a google search recently. Just thought there would be a simple command to merge terminals into tabs.

---

### Post by mcduck on 2012-08-21
You can drag & drop tabs between gnome-terminal windows, but I'm not aware of any way to do this when the window only has one tab (and therefore the tab bar is hidden).

---

### Post by markbl on 2012-08-21
> **cc7gir said:**
> 
Otherwise, try terminator. It can open and display multiple terminals in a single window.
Yes, right click in terminator to "Split vertically" or "Split horizontally". I use terminator instead of gnome terminal but another approach I also use is to run tmux and split vertical and horizontal panes. tmux (modern successor to gnu screen) is an excellent tool which all linux terminal power users should know about.

---

### Post by mrvh on 2012-09-10
[https://github.com/vahidhedayati/termssh](https://github.com/vahidhedayati/termssh)

been working on this shell script which automates terminator layouts/connections.

Feel free to give it a go, its working perfectly for me at work :)

---

