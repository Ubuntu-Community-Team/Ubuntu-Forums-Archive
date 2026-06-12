---
title: "No window frames on Xubuntu"
date: 2011-09-18
forum: Desktop Environments
---

### Post by joel_gil on 2011-09-18
I installed Xubuntu 11.04 a week ago on my inspiron 14R and it was working ok until today, I turned it on and the windows frames are gone.

I havent installed anything new on the system lately, havent updated any package or anything, theya re jsut gone, even when I restart gdm or reboot, they wont come back.

Any ideaas on this?

---

### Post by Toz on 2011-09-18
Alt-F2, then **xfwm4 --display=:0.0 --replace**

---

### Post by Kaedroho on 2011-12-21
Hi, I had this problem too on Xubuntu 11.10 and that solved it!

Cheers!:)

---

### Post by neu5eeCh on 2011-12-21
> **joel_gil said:**
> I installed Xubuntu 11.04 a week ago on my inspiron 14R and it was working ok until today, I turned it on and the windows frames are gone.

I havent installed anything new on the system lately, havent updated any package or anything, theya re jsut gone, even when I restart gdm or reboot, they wont come back.

Any ideaas on this?

This is a known Bug in Xubuntu 11.04 and I'm blown away to hear that they haven't fixed this in 11.10!?! I'm currently using Xubuntu 11.04 and occasionally have this issue. The problem is finding a way to issue the command -- **xfwm4**. Sometimes, you can bring up a command interface using alt-f2, but still be unable to type anything in the command box. One trick I've had to use is to type xfwm4 in a whatever window was accessible, then copy and paste.

This makes me reconsider upgrading to Xubuntu 11.10. This bug is a serious PITA.

---

### Post by TrevP on 2011-12-21
This bug is a nuisance. As a "work around", I just include xfwm4 in the application autostart tab in the settings and startup section of the settings manager. This ensures that it always starts.

---

### Post by neu5eeCh on 2011-12-21
> **TrevP said:**
> This bug is a nuisance. As a "work around", I just include xfwm4 in the application autostart tab in the settings and startup section of the settings manager. This ensures that it always starts.

I tried that but it never worked for me.

---

### Post by Linuxratty on 2011-12-21
Has anyone sent them a bug report? How can they let something like this slip by?

---

### Post by Toz on 2011-12-21
The session state was probably saved without the window manager running.

Try re-setting your saved sessions cache prior to logging in (Ctrl-Alt-F1):
```
mv ~/.cache/sessions ~/.cache/sessions.bak
```

Note: this will reset your sessions cache to default (applications starting automatically as a result of saving your session state). Will not affect your autostart applications. Should get xfwm4 to start automatically again.

---

### Post by neu5eeCh on 2011-12-21
> **Linuxratty said:**
> Has anyone sent them a bug report? How can they let something like this slip by?

Here it is:

[https://bugs.launchpad.net/null/+bug/794551](https://bugs.launchpad.net/null/+bug/794551)

Which is a duplicate of:

[https://bugs.launchpad.net/ubuntu/+source/xfwm4/+bug/495361](https://bugs.launchpad.net/ubuntu/+source/xfwm4/+bug/495361)

So, they know. Looks as though they might fix it in Precise? They write:

"Should be fixed when Xfwm 4.8.3 reaches precise. We'll evaluate the  possibility to fix that in older releases as well when the fix get some  testing."

---

### Post by vangop on 2011-12-22
The workaround is to logout, switch to VT (ctrl-alt-f1) and ```
% rm -rf .cache/sessions
```
Can you plz mark the thread solved?

---

### Post by crazybasenji on 2011-12-31
I had this same problem on my laptop, with Lucid Xubuntu. The workaround fixed it. Thanks. I'll mark the thread solved. Umm, if I can figure out how.

---

### Post by Toz on 2011-12-31
Only the OP (the person who created the thread) can mark it closed.

---

### Post by crazybasenji on 2011-12-31
Toz -- I thought that might be the case when I couldn't find a "solved" button. Oh, well. I tried. Still new here.

---

