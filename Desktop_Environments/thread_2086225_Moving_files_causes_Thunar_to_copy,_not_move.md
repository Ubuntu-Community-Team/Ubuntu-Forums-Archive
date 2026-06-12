---
title: "Moving files causes Thunar to copy, not move"
date: 2012-11-20
forum: Desktop Environments
---

### Post by Cheule on 2012-11-20
Hello all,

I recently changed from the Unity interface to xfce to try and combat some bugs I was having.

All is well except one annoyance. When I move a file from one folder to another, Thunar makes a copy. This takes ages if I have many files to move.

On all previous incarnations of Ubuntu I've used, moving a file just moves it (unless moving to another HDD of course), but not this?

I am aware after reading some threads that using shift makes it move not copy, but I was hoping to restore the behaviour that I'm used to.

Anyone else having this?

---

### Post by kr651129 on 2012-11-20
It sounds like you are using Thunar to copy not mv from bash, is this correct?

---

### Post by Cheule on 2012-11-20
Hi there and thanks for replying :)

Basically I've been using Ubuntu regular for a number of years and I've become used to just dragging and dropping a file from one open window to another in Nautilus.

I'm new to xfce and I tried doing the same thing, but this time a dialog box pops up telling me the progress of the file copy - with several files each several hundred megabytes long this can take a while! :)

Basically I'd just like it's drag and drop behaviour to move, not copy :)

---

### Post by LewisTM on 2012-11-20
Sorry for not being very helpful but I cannot replicate what you are describing. Dragging and dropping files between Thunar windows triggers a move operation for me, always has. 

Are you sure you are moving files inside the same partition? Thunar will switch to copy mode if the source and destination are not on the same drive. I think this is hardcoded but can indeed be overridden with the shift key.

Cheers!

---

### Post by Cheule on 2012-11-20
Yep, the files are on the same drive, same partition, just trying to move from one drawer to another :)

---

### Post by ufugu on 2012-11-20
What happens for me is: drag a file from the desktop to a Thunar window and it makes a copy (instead of moving the file).  

Drag between two non-desktop Thunar windows, works as expected (the file is simply moved).

It's as if for some reason Thunar sees the desktop as a mounted drive or something.

That and tabs is why I replaced Thunar with PCManFM.

---

### Post by Seb71 on 2012-11-20
Same behavior here (Xubuntu 12.04):

- if I drag a file from a folder to another folder (inside the same partition), the file is moved;

- if I drag a file from desktop to a folder (for instance to a folder that is also on desktop), then the file is copied to that folder, not moved.

Very annoying.

---

### Post by LewisTM on 2012-11-20
> **ufugu said:**
> What happens for me is: drag a file from the desktop to a Thunar window and it makes a copy (instead of moving the file).  

Drag between two non-desktop Thunar windows, works as expected (the file is simply moved).

It's as if for some reason Thunar sees the desktop as a mounted drive or something.

That and tabs is why I replaced Thunar with PCManFM.
It's a Xfdesktop issue, not a Thunar one. You get the same copy-to-desktop behavior with PCManFM or Nautilus.

Tabs are going to be featured in the [next version]("http://www.webupd8.org/2012/11/install-thunar-with-tabs-support-in.html") of Thunar. Yay!

We are straying away from the OP's problem: a copy behavior _everywhere_. That is abnormal. 

@Cheule: If you create a new user account, do you have that same problem??

---

### Post by Ken Wood on 2013-02-01
Yep, it's shitting me up the wall too.

---

