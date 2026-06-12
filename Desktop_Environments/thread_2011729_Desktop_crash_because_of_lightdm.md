---
title: "Desktop crash because of lightdm?"
date: 2012-06-27
forum: Desktop Environments
---

### Post by ryanvade on 2012-06-27
Hello.

I  am having a desktop crash problem.  I have no idea what  is happening. i am just sitting here using my conputer and then the  status bar disapears, unity dash disappears, and none of the keyboard  commands work (like ctrl +alt + backspace to logout) The only thing that  works is to ctrl + alt + F1 to login and sudo service lightdm stop and  then sudo service lightdm start. 
the problem is that i keep getting error messages after starting lightdm like this:

[5479.121186] Bug: Bad rss-counter mm:FFFF880056547680 idx: 1 val: -2
[5479.121230] Bug: Bad rss-counter mm:FFFF880056547680 idx: 2 val: 2
[5479.230921] Bug: Bad rss-counter mm:FFFF88005d8dF480 idx: 1 val: -1
[5479.230975] Bug: Bad rss-counter mm:FFFF88005d8dF480 idx: 1 val: -1

There  is 6 lines of this. It's apparently a linux bug, but I haven't found a  good solution to it. I hope the problems aren't linked, but i have no  idea.  runnig htop in tty1 show that the system isn't overly extended.


I found a possible solution but I don't know how to use it/ how to perform it. 

```
Subject[PATCH] mm: correctly synchronize rss-counters at exit/execFromKonstantin Khlebnikov <>DateSat, 09 Jun 2012 13:43:32 +0400
do_exit() and exec_mmap() call sync_mm_rss() before mm_release()
does put_user(clear_child_tid) which can update task->rss_stat
and thus make mm->rss_stat inconsistent. This triggers the "BUG:"
printk in check_mm().

Let's fix this bug in the safest way, and optimize/cleanup this later.

Reported-by: Markus Trippelsdorf <markus@trippelsdorf.de>
Cc: Oleg Nesterov <oleg@redhat.com>
Signed-off-by: Konstantin Khlebnikov <khlebnikov@openvz.org>
---
 fs/exec.c     |    2 +-
 kernel/exit.c |    1 +
 2 files changed, 2 insertions(+), 1 deletion(-)
diff --git a/fs/exec.c b/fs/exec.c
index a79786a..da27b91 100644
--- a/fs/exec.c
+++ b/fs/exec.c
@@ -819,10 +819,10 @@ static int exec_mmap(struct mm_struct *mm)
     /* Notify parent that we're no longer interested in the old VM */
     tsk = current;
     old_mm = current->mm;
-    sync_mm_rss(old_mm);
     mm_release(tsk, old_mm);
 
     if (old_mm) {
+        sync_mm_rss(old_mm);
         /*
          * Make sure that if there is a core dump in progress
          * for the old mm, we get out and die instead of going
diff --git a/kernel/exit.c b/kernel/exit.c
index 34867cc..c0277d3 100644
--- a/kernel/exit.c
+++ b/kernel/exit.c
@@ -643,6 +643,7 @@ static void exit_mm(struct task_struct * tsk)
     mm_release(tsk, mm);
     if (!mm)
         return;
+    sync_mm_rss(mm);
     /*
      * Serialize with any possible pending coredump.
      * We must hold mmap_sem around checking core_state
```

---

