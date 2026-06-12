---
title: "shift-select 'file list' in nautilus opens top-most sub-folder"
date: 2009-05-09
forum: General Help
---

### Post by gregconquest on 2009-05-09
In Nautilus under ubuntu 9.04 (AMD64), when I select one file, and then move my cursor down the list of files, press <Shift> and try to select the end of a list of mulitple files, the sub-folder at the top has a triangle that changes to black and *it* opens; the files remain unselected.

So, I cannot use shift-select to select mulitple files!

Is this a bug, or is it an option that has been mis-set from the normal default? How do I "fix" it?

Thanks,
Greg

---

### Post by KhurramM on 2009-05-09
Its better to use CTRL button for multi select with shift.

Hope this resolves your issue.

---

### Post by gregconquest on 2009-05-09
> **KhurramM said:**
> Its better to use CTRL button for multi select with shift.

Hope this resolves your issue.

If I want to select several hundred files in the middle of a total of a thousand files, you think I should <CTRL> click several hundred times? Are you serious?

Come on. There has to be another way -- and there was. <Shift> multi-select was basic functionality in nautilus, and it disappeared with the 8.10 upgrade, I guess it was. It still works now sometimes, but I haven't been able to reliably get it to work. Sometimes it multi-selects; sometimes it opens the top-most sub-folder. The must be some method to this.

Greg

UPDATE: I checked the same terms using 8.10 specifically, and that got me to this:
[https://bugs.launchpad.net/nautilus/+bug/295408]("https://bugs.launchpad.net/nautilus/+bug/295408")
It does appear that this is a bug that cropped up in 8.10 and has continued into 9.04.

It is really annoying, but this hasn't been discussed much. Has no one figured out a reliable work-around?

UPDATE 2: OK. I've found a reliable work-around. Select your first file, and then *after* you press and hold the <Shift> key, you *have to* move the mouse. That fixes it. This means that you cannot choose your first file, move the cursor to the last file, then click the mouse.

There are two routes for the work-around, but the critical thing is that you just have to move the mouse around after you press <Shift> and before you click the mouse button.

---

### Post by KhurramM on 2009-05-10
Actually I meant:

CTRL + SHIFT

any how, if its a bug, then lets wait for it to bug away.....

---

### Post by plotkin on 2009-06-15
> **KhurramM said:**
> Actually I meant:

CTRL + SHIFT

any how, if its a bug, then lets wait for it to bug away.....

*I think I found a better work around for everyone. *

**First let me restate the problem:**
You are viewing a folder in nautilus in list view, sorted by file type. All the folders are grouped at the top and all the files are grouped by type. You want to select some contiguous subsequence of the files, not the folders. You click on the first item in the subsequence you want. You then locate the last item you want which defines the whole subsequence, you hold shift and click on the item. Now instead of making a selection of a subsequence you have expanded one of the folders.

**The Workaround:**
This works for me, I hope it helps. Instead of defining your subsequence as I mentioned above, do it like this: 
First click on the LAST item in the subsequence you want, then hold shift, then click on the FIRST item in the subsequence. So basically, you just to the normal process in reverse.

**If that is annoying:**
then this might be less annoying: change the sorting order for the list. Keep it sorted by type but invert the order, so the folders appear at the bottom of the list and the items which were previously last in the file list will be first. Now should be able to make a subsequence selection where you click on the first item in the sequence and then hold shift and then click on the last item in the sequence (i.e. the normal way).

I hope this helps some people. This issue has been catching me off guard for months now and I never got around to doing anything about it until now and I hope there are hidden caveats associated what I have said.

---

### Post by blackdalek on 2009-06-26
this bug has been giving me the $#@%s for weeks too.

> **plotkin said:**
> 
**The Workaround:**
This works for me, I hope it helps. Instead of defining your subsequence as I mentioned above, do it like this: 
First click on the LAST item in the subsequence you want, then hold shift, then click on the FIRST item in the subsequence. So basically, you just to the normal process in reverse.

**If that is annoying:**
then this might be less annoying: change the sorting order for the list. Keep it sorted by type but invert the order, so the folders appear at the bottom of the list and the items which were previously last in the file list will be first. Now should be able to make a subsequence selection where you click on the first item in the sequence and then hold shift and then click on the last item in the sequence (i.e. the normal way).

The first method did not work for me, the second method did work... but having to remember to play with sort orders every time you look at a new folder is just as annoying too.
Is there some way to set the default folder view and sort order so that the bug can be avoided all the time?


edit: Ok, I just re-read update 2 on post #3... this method seems to work better, but will take some getting used to.

---

