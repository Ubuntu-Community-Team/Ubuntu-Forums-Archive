---
title: "emacs23 versus emacs 22"
date: 2010-11-14
forum: Desktop Environments
---

### Post by duduntu on 2010-11-14
Hi,

I do not understand, who made emacs23? and why this version is distributed at all?
The functioning of scrollbar moving by mouse vs. text highlighting vs. copy and paste is mad.
The movement and editing is completely uncontrolled in this setup. 
I suspect that I could spoil some my program files before I realized that this mad editor has 
a trend to insert something whenever it wants.

It is however very fortunate that ubuntu distributes emacs22.
This seem to keep old well designed behaviour.
I hope that this version  will not disappear in future from Ubuntu distributions, untill newer 
versions don't return to normal behaviour? 
This is my request or a vote, if I am allowed...

   ... From a new Ubuntu user.

---

### Post by jpkotta on 2010-11-14
C-h n

You're probably upset about line-move-visual and transient-mark-mode, but you're not specific enough.

There is a known bug in the Ubuntu version where dragging the scroll bar highlights text.  I don't know if there's a workaround, because I almost never scroll that way.

---

### Post by circum0 on 2011-02-16
Hi,

This has nothing to do with emacs23 or 22. Setting the env var GDK_NATIVE_WINDOWS=1 helps, i.e., start emacs from cmdline with

GDK_NATIVE_WINDOWS=1 emacs

---

