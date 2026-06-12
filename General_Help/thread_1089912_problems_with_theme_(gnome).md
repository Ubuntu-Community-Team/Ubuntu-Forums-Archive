---
title: "problems with theme (gnome)"
date: 2009-03-07
forum: General Help
---

### Post by Martinex on 2009-03-07
Hi.
I have problem with gnome's themes.
I using my favorite theme, but after few hours system will switch to watch the screenshot under this post.
When I click system/preferences/appearance system auto log out me and closed all running aplications.Just log out.
After I log in again theme working good, bad problem is repeating.
How can I fix it?

I'm using Linux Ubuntu 8.10 with kernel 2.6.27.13 with all updates.
Gnome in version 2.24.1.

Please help me.

PS: sorry for my English, if anyone doesn't understand something please let me know.

[[IMG]http://img21.imageshack.us/img21/2648/screenshot1j.th.png[/IMG]](http://img21.imageshack.us/my.php?image=screenshot1j.png)

---

### Post by thtrgremlin on 2009-03-07
sorry for not necessarily having a better suggestion, but I am going to guess you are using compiz and that compiz is crashing and then switching to metacity (which has its own theme)

Something to try: open a terminal and run ```
compiz --replace
```This will switch you back to compiz. If it crashes, the output will go to the terminal where you started compiz from. If it crashes while running it that way, please post that output here, unless the output makes enough sense to you to fix it on your own  :)  Let us know. I a, going to bet it will crash again and then we can see what happened.

---

### Post by Martinex on 2009-03-07
without compiz and 3D drivers (nvidia GeForce 4000 64MB) there's problem, too (it's bad).

On enable driver 3D there's problem with font in some apps like amarok and OpenOffice.

---

