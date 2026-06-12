---
title: "beryl &amp; KDE pager problem"
date: 2007-03-19
forum: Desktop Effects &amp; Customization
---

### Post by vidak on 2007-03-19
I've installed beryl, and got the following problem:  KDE's pager applet don't work. 
It seems that beryl uses two things: desktops, which is quite different from pager's desktop-interpretation, and virtual desktop, which is the well-known desktop concept. So it follows that the solution would be to set the number of desktops in beryl to one, and set virtual desktops in 6x1 (horizontal x vertical) layout. In this case, kpager recognizes the number of desktops and the layout correctly. Using the applet, it is possible to switch between the desktops, and the actual desktop is selected in the applet. BUT the actually running programs aren't displayed correctly. The programs running on the actual [virtual] desktop (viewport?) are displayed on pager like it would be on Desktop1, and the others are forgotten. 
Did anyone find a solution of this bug? The case is quite annoying because when at work, I usually use about eight desktops each fulled with windows and terminals, and pager is a crucial tool to know which one is where...

Thanks for your help...

---

### Post by Arby on 2007-03-20
I have the same problem. I'm told it is a difference in how beryl/compiz defines desktops/workspaces compared to how kwin does it. There is an alternative pager applet on [kde-look.org]("http://www.kde-look.org/content/show.php/kicker-compiz?content=46021") that is apparently compiz/beryl compatible. I haven't tried it myself yet so I can't say how well it works. I've heard mixed reviews so far. Anyway, might be worth a try.

---

### Post by vidak on 2007-03-20
Well, it gets better, it worths to give a try. Now some smaller thing: that applet grows HUGE on the kicker. This can be solved by introducing vertical desktops, but doing so one has to switch from the Cube to the Plane to have those additional desktops work right...

---

### Post by fandelau on 2007-03-24
Something that I have realized is that the number of desktops has to be managed by Beryl. It gets messed up if you try it with kwin (IE right click on the pager and select "configure desktop") I have the compiz pager and it works just as expected when managed with beryl.
My 2 cents.
Cheers!

Ramon

---

### Post by hikaricore on 2007-03-24
I've found that if I have 4 desktops setup in the kde pager, and I set the number of desktops
under General Options in Beryl Settings Manager to 4, the problem goes away for me.

This might not work for everyone.

---

### Post by Ateo on 2007-05-17
> **Arby said:**
> I have the same problem. I'm told it is a difference in how beryl/compiz defines desktops/workspaces compared to how kwin does it. There is an alternative pager applet on [kde-look.org]("http://www.kde-look.org/content/show.php/kicker-compiz?content=46021") that is apparently compiz/beryl compatible. I haven't tried it myself yet so I can't say how well it works. I've heard mixed reviews so far. Anyway, might be worth a try.

This works wonderful. The pager even looks nicer (very subtle).

> **hikaricore said:**
> I've found that if I have 4 desktops setup in the kde pager, and I set the number of desktops
under General Options in Beryl Settings Manager to 4, the problem goes away for me.

This might not work for everyone.

Unfortunately, no workie. Either way, that pager at kde-look.org is nice.

---

### Post by rmtatum on 2007-09-05
I have the pager from kde-look.org installed and running.  It seems to have disabled Rotate Cube.

---

