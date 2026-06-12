---
title: "Compiz only works occasionally."
date: 2006-07-19
forum: Desktop Environments
---

### Post by malachi on 2006-07-19
I'm having trouble with XGL/Compiz on Dapper. I have an ATI Mobility Radeon 9000.

I've followed several tutorials and howto's exactly, but I've never been able to have Compiz run successfully more than three times in a row. I have know clue where to start troubleshooting.

Any help will be appreciated. Very much.

---

### Post by goobers on 2006-07-19
When you say that compiz doesn'y run, does it quit with an error message, or does it just render the desktop normally (i.e. uses metacity)?

---

### Post by malachi on 2006-07-19
It renders the desktop normally, but no window titlebars are present, you can't Alt+Tab or move a window, and everything runs super slow.

---

### Post by goobers on 2006-07-19
Ahh, i've had this problem. Did you adjust any settings for compiz at all? Which method did you use to install it?

---

### Post by misha680 on 2006-07-24
I have the same problem, and interestingly enough, also a Mobility Radeon 9000. Didn't tweak any settings as far as plug-ins go.

Misha

---

### Post by jimmygoon on 2006-07-24
I'm imaging you guys are using compiz-quinn's packages. I would recommend that unless you can keep an eye on compiz.net then I would switch to compiz-vanilla because of the fact that he is changing stuff constantly. We all had this problem until we switched the compiz start script to use her new cgwd rather than the modified gnome-window-decorator.

check it out: [http://www.compiz.net](http://www.compiz.net)

---

### Post by misha680 on 2006-07-24
**Edit**

Okay, got a solution by posting on the compiz forums. Just install an older version of the XGl server:

[http://ubuntu.compiz.net/pool/main/x/xserver-xgl/xserver-xgl_7.0.0-0ubuntu28_i386.deb](http://ubuntu.compiz.net/pool/main/x/xserver-xgl/xserver-xgl_7.0.0-0ubuntu28_i386.deb)

Problem solved.

Misha

---

### Post by malachi on 2006-07-26
Nope, changing to vanilla didn't work. I'm going to try Misha's idea and see if I have any luck.

Thanks, all you guys, for helping me out.

---

### Post by malachi on 2006-07-26
Wow! Thanks Misha, it *did* work! After about a month of searching, you've done it!

Thanks again to all of you who assisted me!

---

