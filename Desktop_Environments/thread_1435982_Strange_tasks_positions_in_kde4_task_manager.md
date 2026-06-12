---
title: "Strange tasks positions in kde4 task manager"
date: 2010-03-22
forum: Desktop Environments
---

### Post by Dmitry Vyal on 2010-03-22
Hello, I installed kubuntu-desktop on my ubuntu-9.10.

Now I have some issues with task manager. Then many tasks are shown in it, their buttons become small and crowded in the upper side of the bar. In the task manager settings I have a maximum rows number of 1. After I close most of windows, the remaining buttons are still odd. They're thin and positioned in two semi-filled rows.

I remember, I had similar problem with kde4 in gentoo. Can something be done with it?

---

### Post by cmreigrut on 2010-05-05
I'm seeing something similar, in that I'm ending up with phantom tasks that are either duplicates of existing tasks, or are tasks that have been closed, but still show up in Task Manager.  Also, I've been on Karmic since it came out, and I've only just started seeing these in the last month or two.  

I haven't upgraded to Lucid yet, and I'm hoping that will solve things for me.

---

### Post by mylh on 2011-10-03
I've experienced the same kind of problems lately. task manager ignores maximum rows and force rows setting

---

### Post by csbac on 2011-10-11
Hi! Bump. Same problem, since 4.7.1 (was 4.6.y before, is 4.7.2 now). Created completely new kde configuration (removed .kde and .kde4), still same thing.  Before I logged out last time, I had one virtual desktop with one application, its "icon" alone in the third or fourth row.  My system is opensuse 11.4 x64, so, obviously, it's a kde problem, not an ubuntu-only problem.

---

### Post by jpelorat on 2011-10-15
Also happening with Kubuntu 11.10's task manager.

---

### Post by Nippondanji on 2011-10-18
I'm facing a similar problem on 11.10 too. Is there a work around?

Thanks.

---

### Post by Nippondanji on 2011-10-18
I've found that the task manager gets weird when a window is opened on non-current desktop. Such a situation occur when specifying a desktop on window rules for example. You can repeat the problem in the steps below.

1. Configure more than one desktop in the pager or "System Settings" > "Workspace Behavior" > "Virtual Desktops".

2. Configure a window rule in "System Settings" > "Window Behavior" > "Window Rules". For example, let Firefox forced to open on Desktop 2.

3. Switch to the other desktop which is not specified in step 2.

4. Open new windows. (For example, run Firefox several times)

---

### Post by Nippondanji on 2011-10-18
I've found a workaround which does not need logging out.

It's simple :)

Once remove the Task Manager widget, then add a new Task Manager widget to your panel back. Adjust Task Manager options, because options will be cleared after replacing the Task Manager widget.

That's it! Now you can see the problem is fixed.

Thanks.

---

