---
title: "Applications Menu won't open"
date: 2009-02-12
forum: Desktop Environments
---

### Post by mjbauer95 on 2009-02-12
My Applications menu won't open.
The System and Places menu work fine but the Applications one doesn't show up.
But other than that if have almost no problems, I'm able to start firefox from the terminal and other programs.

Is there any way I can tell what I'm encountering?

---

### Post by mjbauer95 on 2009-02-13
*bump*

---

### Post by mjbauer95 on 2009-02-14
* bump *

---

### Post by jnewl on 2009-02-15
In case you haven't gotten it working yet, I had the same problem. Here's the solution that worked for me:

1. Type Alt-F2 to get a Run dialog
2. Click "Run in Terminal" checkbox (Don't know if this is necessary, but it worked)
3. Copy and paste into dialog: rm ~/.config/menus/applications.menu
4. Click Run button

---

### Post by mjbauer95 on 2009-03-01
Thanks, that fixed my problem :P

---

### Post by Drigy on 2009-05-08
> 1. Type Alt-F2 to get a Run dialog
2. Click "Run in Terminal" checkbox (Don't know if this is necessary, but it worked)
3. Copy and paste into dialog: rm ~/.config/menus/applications.menu
4. Click Run button
Hi!

That doesn't work for me =/ Applications simply doesn't work. When I try that solution, nothnig happens, not even a terminal opens. 

My problem: As I click on the applications menu, it opens only a very small submenu and there is nothing in it.

Please help and thank you for your reply!

---

### Post by ikonia on 2009-05-08
try doing it manually first of all so you see the output if there is any problems.

One thing to remember is that ~ is a shell varible for home, try specificying the full path instead.

---

### Post by Drigy on 2009-05-08
Thnx, i did it manualy and it worked. This was giving me a lot of headache, so thanks again!

---

