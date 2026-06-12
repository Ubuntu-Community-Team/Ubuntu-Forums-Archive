---
title: "Restoring Updates and &quot;Using&quot; them."
date: 2005-06-28
forum: Desktop Environments
---

### Post by duffmckagan on 2005-06-28
I have installed Ubuntu Hoary, and I need to download all the available updates.

I followed the instructions in the Unofficial Ubuntu Guide to backup and restore the stuff in the folders.

But now the question is, after restoring, how do I use them?

I have a computer which has Dial-Up and needs updating. So how can I use the tar.gz file on that comp, to use all the updates in that file?

I hope you guys have understood the problem, and I am not confusing.

---

### Post by dfghost on 2005-06-28
You need to add suppositories to your apt-get to allow for the updates, then just go to the update manager and click update.  It should be somewhere in applications, i think.  If you already have the updates, just start a terminal.  gunzip and tar vxf it, then there should be .deb files in there.  Just go to each in terminal and dpkg install them each.  Personally, i think the first is easier.  Then again, what is Ubuntu w/o broadband.

---

### Post by duffmckagan on 2005-06-28
But I have broadband on a computer at my other home. I can just put the updates into a cd, then restore them to the proper places on this computer with Dial-Up.

If we can't install it again after restoring the backup of the updates, then what is the use of backing up then?

---

### Post by skoal on 2005-06-28
[QUOTE=dfghost]You need to add suppositories to your apt-get to allow for the updates[...][/QUOTE]
rofl.  suppositories??  Yes, I guess that's one way of looking at it.  I'm just curious though how you go about *inserting* them into apt-get...

\\//_

---

### Post by duffmckagan on 2005-06-29
:wink: I did not take a look at that before!

---

### Post by dfghost on 2005-06-29
sigh.  It's called the unoficial guide to ubuntu.

[Just, Go here, k](http://ubuntuguide.org/#repositories)

---

### Post by duffmckagan on 2005-06-30
[QUOTE=dfghost]sigh.  It's called the unoficial guide to ubuntu.

[Just, Go here, k]("http://ubuntuguide.org/#repositories")[/QUOTE]

Is there anything wrong in there?

---

