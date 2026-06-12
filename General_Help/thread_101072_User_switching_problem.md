---
title: "User switching problem"
date: 2005-12-09
forum: General Help
---

### Post by amokoura on 2005-12-09
**Info:**
2 users (A and B) want to use Ubuntu at the same time.

**Problem:**
User switching doesn't work.

**Error process:**[LIST=1][*]A: Log in.
[*]A: [System Tools] -> [New Login].
[*]A new login screen appears straighaway.
[*]B: Log in.
[*]B: [System Tools] -> [New Login].
[*]B: "Open Displays" dialog appears.
[*]B: The list shows that user A has already an open display.
[*]B: Choose user A and click "Change to Existing Display".
[*]A blank screen appears where you can write stuff or sometimes it boots to command line and asks for new login.
[/LIST]

I assume it should actually just go to user A's desktop.

---

### Post by amokoura on 2005-12-12
Here is some detailed information about the problem:

The "New Login" dialog shows that user A has already a display at **display 0, virtual terminal 7**. After choosing it the system goes to console mode, **tt1** reading on top. I can change the console from tt1 to tt6 as these are the default virtual consoles. I presume the tt7 would be the existing display I had in use. When I do ctrl+alt+F7 it just shows a blinking cursor where I can write text but it doesn't run any programs or anything.

So the problem is:
**How to get to the right display after switching the user?**

---

