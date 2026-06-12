---
title: "Blackberry Bold - &quot;file system error&quot;"
date: 2009-04-01
forum: General Help
---

### Post by ironchef on 2009-04-01
Plugged my Blackberry Bold into my pc running Jaunty Jackalope for the first time to transfer some music.  When I tried to unmount the phone, nautilus became unresponsive.  The songs appear to have transferred - I can see them when I connect to the pc again, but the phone can no longer read anything in any folders /home/user/  When I tried to take pictures, they can no longer be saved.  Any attempt to access data returns a "file system error".

Has anyone encountered this problem?  I tried a clean swipe of the phone software, but that doesn't seem to affect the folders.

---

### Post by jackflap on 2009-04-01
Maybe plug-in the phone to the PC again (also consider not using Jaunty as it's still only beta), and checking the permissions of the files/folders on the phone.

Perhaps changing the permissions to allow all read/write will fix the problem.

---

### Post by ironchef on 2009-04-01
Thanks.  I'll check permission on the folders.  Do you know what could cause the permission to change?  It had worked fine going back and forth from ubuntu 8.10 and windows xp prior to this.

I had the same issue when plugged into my windows xp box at work this morning.

---

### Post by Prince_Andrei on 2009-06-09
Did you ever figure it out? I have the same error and haven't been able to fix it.

---

### Post by brianslushy on 2009-07-23
I'm having the same issue.   anyone figure out the fix?

---

### Post by chewster on 2009-10-03
This thread is a bit old, but I found it on google, so figured I'd update it with a solution for other Ubuntu/Bold users.

Same thing happened to me.  Did some digging and turns out the solution is to format the internal storage.

On the device, go to options > memory.

You should see a blurb about unformated device memory.  If you scroll to it and hit the ball, it will let you format it.

On my end, I used a windows (I know, I know) computer with desktop manager to back up my device first.  After format, I did a restore and all is well again.

From my reading, this has happened to people doing file transfers on windows machines as well.

Didn't really find a cause to all of this though.

---

