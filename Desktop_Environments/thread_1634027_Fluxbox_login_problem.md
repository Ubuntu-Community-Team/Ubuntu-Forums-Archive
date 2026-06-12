---
title: "Fluxbox login problem"
date: 2010-11-29
forum: Desktop Environments
---

### Post by lawlonslawt on 2010-11-29
First post on these forums, so hi all. :D

Sorry if this is somehow a duplicate thread. I searched and found nothing. The title may also be misleading as I couldn't think of an appropriate one. My situation is harmless, but annoying as hell. 

When I set my desktop background using fbsetbg (the app is feh), the wallpaper stays for the entire session, but disappears when restart or logout. Upon logging in after that, the background turns into the background at the Xubuntu login screen---that pretty, blue skyish thing. 

I've tried commands such as sudo fbsetbg -l, same thing with no sudo, sudo fbsetbg -f, and so on. No success. Any ideas?

By the by, if I seem nooby, I am--for the second time. I recently got back into it, so I apologize for any beginner mistakes on my part.

---

### Post by Rodney9 on 2010-11-30
This may work - [http://old.fluxbox.org/docbook/en/html/chap-bg.html]("http://old.fluxbox.org/docbook/en/html/chap-bg.html")

---

### Post by lawlonslawt on 2010-11-30
I was about to edit my post to say that I've messed with the fluxbox init file, as well as aforementioned attempts. I've used that exact page for advice, and it hasn't worked.

Fixed: I added fbsetbg -l to my fluxbox startup file and it worked. I already tried this before a few times and it didn't work, but it did now, so I'm happy.

---

