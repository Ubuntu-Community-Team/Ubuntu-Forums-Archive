---
title: "[SOLVED] posting a howto..."
date: 2008-07-01
forum: Forum Feedback &amp; Help
---

### Post by estyles on 2008-07-01
Basic question: about how long does it take for a topic posted in tips & tutorials to get moderated?  If I'm jumping the gun by asking, then I apologize.

I posted a topic in howto about 2 days ago.  Silly me, I didn't realize that the forum was moderated - I figured I could go back and reference the post as needed after it was posted (as well as edit content as needed).  I also didn't realize it was my first post - kind of silly for a noob writing a howto as his first post (meant it more as a quick tip, i.e. "**Tips** and Tutorials").  I've been around here for a few months, lurking, and it didn't occur to me that I hadn't actually posted before - had found most of the help I needed by searching.  Which, I assume, would be considered a good thing.  :)

Anyway, since I don't have a backup, I just want to make sure that my post wasn't lost.  I can understand if it's not good enough to be in the tutorials section, but I just hope I get a PM, or it gets reposted somewhere else so I don't lose it.  So, yeah, just asking...  if 2 days isn't an unusual time to wait for moderation, then I'll just wait patiently.  Sorry to bother whoever might be bothered by this post... O:)

---

### Post by LaRoza on 2008-07-01
> **estyles said:**
> Basic question: about how long does it take for a topic posted in tips & tutorials to get moderated?  If I'm jumping the gun by asking, then I apologize.


Time isn't set. It happens when someone goes through them. I typically don't work with the tutorials and tips, but here is the link (so you know it isn't lost)

[http://ubuntuforums.org/showthread.php?t=844849](http://ubuntuforums.org/showthread.php?t=844849)

---

### Post by popch on 2008-07-01
> **LaRoza said:**
> Time isn't set. It happens when someone goes through them. I typically don't work with the tutorials and tips, but here is the link (so you know it isn't lost)

[http://ubuntuforums.org/showthread.php?t=844849](http://ubuntuforums.org/showthread.php?t=844849)

That yields:
> Invalid Thread specified. If you followed a valid link, please notify the [administrator]("http://ubuntuforums.org/sendmessage.php")

---

### Post by LaRoza on 2008-07-01
> **popch said:**
> That yields:

Yes, it does (to you).

I think the OP and staff are the only ones who can see it. At least, I can see it fine. (It has a **moderated** prefix)

---

### Post by jpeddicord on 2008-07-01
estyles:

I've moved your HOWTO to The Jail for now, as I see a few problems with it:
[LIST=1]
[*]Step 3 should be removed, allowing any user access to menu.lst is a big security risk in that it allows any user to become root at boot. This invalidates step 4 as well
[*]A lot of that could be simplified by using the command "savedefault" in grub - that will make sure you never have to edit the default entry. From menu.lst:
```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0
```
[/LIST]

Feel free to edit your tutorial and resubmit it to Tutorials and Tips anytime once you have fixed those issues. :)

---

