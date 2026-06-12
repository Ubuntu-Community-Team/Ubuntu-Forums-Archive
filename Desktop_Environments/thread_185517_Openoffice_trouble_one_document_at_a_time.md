---
title: "Openoffice trouble: one document at a time"
date: 2006-05-31
forum: Desktop Environments
---

### Post by wyth on 2006-05-31
I ran into the bug that a number of people with ATI Radeon cards ran into after the last fglrx upgrade --openoffice wouldn't open ([bug #47371]("https://launchpad.net/distros/ubuntu/+bug/47371/+index")).  

So I did the quick fix of putting fglrx in the restricted modules list.  That worked to a point.  Now I can open **a** document, but not more than **one** document.  

This is a real problem in my case, and I'm sure for some others, if they're experiencing it.  I'm a grad student and need to have more than one document open at once.  

I've scoured the forums and haven't found anything like this so far.  If anyone has a fix or is experiencing the same problem, let's have it.  If there are a number of people experiencing this, I'll probably file a bug.  If not, and if there's something silly simple that I'm missing, put me in my place so I can get back to work.

[*EDIT:*] I took fglrx off the restricted modules list and replaced libGL.so.1.2 in /usr/lib with the old one (solution from [this thread]("http://ubuntuforums.org/showthread.php?t=185033") to fix the fglrx problem).  Same story; I can open one document, but not more than one.

May try to remove and install it again.[*/EDIT*]

---

### Post by wyth on 2006-06-01
Okay, why do I post with questions at all?  Every time I do, I end up finding my own answer, and it's usually something simple and I just want to delete my question.

But if anyone else ran into this issue, here's what worked for me:

As stated above, I used the old libGL.so.1.2 file (replaced the new one in /usr/lib).  Then I scrubbed everything having to do with openoffice from my system, including the hidden files in /home.  Removed all orphaned files.  Even rebooted for good measure.  Then re-installed openoffice (be sure to add openoffice.org-gnome and openoffice.org-gtk packages, or it looks uuuuugly).  

I'm still curious what that issue might have been, but much less so now, since it's working.

---

