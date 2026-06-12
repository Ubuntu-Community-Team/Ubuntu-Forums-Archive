---
title: "How to Select in XTerm/UXTerm and then Copy-Paste into another application?"
date: 2015-05-04
forum: Desktop Environments
---

### Post by bjbraams2 on 2015-05-04
I have found, courtesy of Ubuntuforums.org, that it is possible to copy a selection from my clipboard into an XTerm or UXTerm window by using shift-insert (instead of ctrl-v or a mouse-click operation). However, I cannot find any way to go in the other direction: get a selection from my XTerm or UXTerm window and paste it into a different application, such as my browser address bar.

I am using Ubuntu 14.04, everything default. Within my UXTerm, the command 'wmctrl -m' informs me that my window manager is Metacity; I would not have guessed that. On the other hand, 'ps -A' shows a process gnome-panel and a few other processes with "gnome" in the name, so I think that I'm running the Gnome WM. ('ps -A' also shows some processes with "unity" in the name.) I have a two-button mouse that also has a clickable central wheel, but the wheel click does not appear to function like a middle-click on a three-button mouse.

Steps whereby I can reproduce my own problem:
- Use ctrl-c to select some text from my browser window (or any non-XTerm application) into my clipboard; use ctrl-v to paste it into (for example) my browser address bar. It works fine.
- Now visit my XTerm or UXTerm window.
- Highlight some text in that window, then do ctrl-v in my browser address bar. It just copies the earlier selection, not the attempted selection from the XTerm window.
- Try to highlight some text in that XTerm or UXTerm and do ctrl-insert as an attempt to select it. Do ctrl-v in the browser address bar and again I get the earlier selection.
- Highlight text in the XTerm or UXTerm and then try wheel-click or try to click left and right simultaneously; nothing that I try will get the selection saved in a way that ctrl-v will paste it into my browser.

---

### Post by bapoumba on 2015-05-04
Are you saying that highlight in xterm and middle click in the browser url does not work ? Does it work in a text editor ?

---

### Post by ajgreeny on 2015-05-04
If you can remember to highlight with mouse and then middle click to paste that buffer you will save yourself a huge amount of time.

It is one of the many marvels of this OS.

---

