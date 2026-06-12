---
title: "x continues to log-out....please help"
date: 2008-12-12
forum: General Help
---

### Post by fast_fxstbi on 2008-12-12
Hi all, I've a notebook nev@da with proc intel core 2 duro 2.4 video intel i915, wireless ipw3945.

I have ubuntu 7.10 installed. I wasn't able to upgrade to 8.04due to problems of some packages.

Initially, I wans't abel to recognize the integrated wireless but now with the restricted drivers all goes well.. more or less.. I had compiz with rotating cube, bluetooth is ok, audio and so on are ok..

From Xorg.0.log my system is:

Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.4)
Current Operating System: Linux fighter1 2.6.22-16-generic #1 SMP Fri Dec 12 10:28:27 GMT 2008 i686

MY PROBLEM:
the only problem is that... X continues to reboot! and I have serius trouble to work! Pratically, every tot time (sometimes 5min, sometimes 1 min).. X reboot, or better, log ou givin' me the initial splash screen to relogin..

I'm becomin' crazy cause I use it for buisness..

Any suggestion please?

Andrea


P.S. while typin' this post... he logout 3 times!

---

### Post by fast_fxstbi on 2008-12-12
no one has some suggestion? Had do finish a buisness plan and I'm not able..: :(

---

### Post by rswoody2000 on 2008-12-12
Can i just ask, what was the last thing you may have changed before this problem occured? I had a similar problem but it had to do with an effect i added and caused the problem to occur.

---

### Post by fast_fxstbi on 2008-12-12
I don't know... now I'll try to deactivate compiz effect and look if it'll happen again.. and also try to install 8.10..

I have a suspect on nm_manager that help to increase some problems..

---

### Post by rswoody2000 on 2008-12-12
That sounds like a good place to start. Try and remove non essential operations and see if the problem stops occuring. You can then slowly start adding more programs and see if that triggers the problem. Upgrading to 8.10 would also be a good start as i have not had many problems with it except for one effects addon that caused my problem.

Let me know how you get on.

---

### Post by fast_fxstbi on 2008-12-14
I tryed to turn off extra effect... the system is surely a bit more stable but the problem of the log-out continues sometimes..

before I was capturing some video from my camera via Kino and I had 2 log-out...

I don't know what to do...

---

### Post by rswoody2000 on 2008-12-15
You mentioned that you are on an older version of Ubuntu and had trouble updating. Are you still unable to upgrade to 8.10?

---

### Post by fast_fxstbi on 2008-12-15
no man, I reinstalled 8.10 from zero....so I have the 8.10 now

---

### Post by rswoody2000 on 2008-12-16
Interesting one you have there. It read like a virus but seeing as you say you re-installed from scratch then that should elimenate that theory. Could you try the following and see if it stops logging you out..

When the login screen appears dont log in yet, click on the Options button and then click on "Select Session". Then select "Failsafe Gnome" and then you may need to click Ok after that. Once youve done all of this, try to login as usual with your normal username and password.

---

