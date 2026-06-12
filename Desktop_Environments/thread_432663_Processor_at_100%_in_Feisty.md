---
title: "Processor at 100% in Feisty"
date: 2007-05-04
forum: Desktop Environments
---

### Post by patterbt on 2007-05-04
I have a strange problem, that I can't seem to figure out.  

I was messing around a few days ago on my Feisty install, trying to backup some of my DVDs.  So I downloaded and installed a few different video related programs, such as vobcopy, K9copy, and Devede.  

Well I used vobcopy to rip one of my DVDs and then messed around with a few other things.  After a short period of time, my system becomes WAAAAY slow; and I found out that my processor was pegged at (or very near) 100% all of the time.  :confused: When I run a TOP to see what the process is, it just says Nautilus.  So when I kill the Nautilus process, the system returns to normal speeds of operation.  

The problem is that every time I reopen Nautilus to browse files on my system, the processor pegs again and the system becomes basically unusable.  

As an interesting side note, I found that when I logout and relogin as a different user, this problem does not exist for the other users.  Does anyone have any ideas what this might be?? Thanks!

---

### Post by patterbt on 2007-05-04
40 views, and no responses.  Does anyone have _any_ ideas to help me on this one???

---

### Post by walmartshopper67 on 2007-05-04
I'm not sure anyone knows what's going on with Feisty like that - I'm having the same frustrating problem, the performance just dies over the course of a day or two. I'm thinking there must be a memory leak somewhere - because over that same period the memory usage continually climbs to the point where i can have nothing open and still be using 96% of my memory.

---

### Post by hellfire_bg on 2007-05-04
Try this - open your system monitor window and see if you have process called gnome-theme-manager runnig. If you have such process kill it. If not see what other process you have running and which of them takes the most % of CP usage.

---

### Post by patterbt on 2007-05-04
> **hellfire_bg said:**
> Try this - open your system monitor window and see if you have process called gnome-theme-manager runnig. If you have such process kill it. If not see what other process you have running and which of them takes the most % of CP usage.

I _**did**_ already check the problematic process (see my original post), and the one that is hogging the CPU is "Nautilus".  When I use the system monitor to view the processes, nautilus is taking 95-99% of my CPU.  

I can kill the process, but every time I restart the Nautilus file manager (to browse my files); the same problem reoccurs again. 

I am wondering why you brought up the gnome-theme-manager, is there a known bug with this application?  Does the theme-manager have a memory leak?  (Unfortunately, I don't think this is the problem with mine though.)

---

### Post by PurplePenguin on 2007-05-05
There is a nautilus bug that causes it to hit 100% CPU usage.

I forget the details, but I had the problem with Edgy a long time ago and found a simple fix for it... I forget the fix, though, but I found it either in this forum or with the other nautilus bugs.

---

### Post by Ambimom on 2007-05-07
Count me in too!  I have the same issue.  If I reboot, the problem disappears and is fine.  Maybe a bug report?

---

### Post by metalheart on 2007-05-07
Just a guess. Run gconf-editor. Navigate to desktop -> gnome -> thumbnailers and check disable_all.

---

### Post by patterbt on 2007-05-07
> **metalheart said:**
> Just a guess. Run gconf-editor. Navigate to desktop -> gnome -> thumbnailers and check disable_all.

Great, sounds like a good idea.  Thanks for the tip, I will try this when I get home from work tonight and repost to let everyone know if it worked or not.  Thanks again!!

---

### Post by penno on 2007-06-17
same problem here. How annoying. Any luck anyone?

(I've just installed Openoffice - dunno if that could be a problem)

---

### Post by penno on 2007-06-17
Ok, just answered my own question. Pre-problem, I was messing around with font sizes (system / preferences / fonts), and changed the default font sizes for Application & Desktop & Document to size 7 (font type was "sans" if that matters). Then the problem occurred. Set all these back to size 8, and everything's fine again.

---

### Post by jimbo99 on 2007-06-17
Now that you mention the font thing I think I have a vague recollection of it giving me problems some time ago.  Weird as everything in Nautilus is supposed to be configurable.

Also, on the system monitor thing.  If you go to view and choose "Active Processes" and then watch for a while sometimes a process will spike every second or two and that can indicate which one is causing the 100% (or high) cpu utilization.

Gnome is very buggy by the way.  I have reported a serious show stopper bug in the current release but they haven't even acknowledged it.  It is something that could get someone seriously sued.  It has to do with copying large groups of files.   It is an incredibly flaky process.

Also, as much as I love Ubuntu and even gnome, it is riddled with the wrong philosophy.  The developers are still holding on to their ideology from their days as Mac OS6/7/8/9 programmers.  I guess they don't want to admit that OSX is the true winner there.

Anyway, always watch very carefully anything  you copy from one drive to another and never ever take for granted that it was actually copied.

---

