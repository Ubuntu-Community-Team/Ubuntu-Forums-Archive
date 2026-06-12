---
title: "Login looping"
date: 2008-10-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Fr33d0m on 2008-10-18
My new M1330 (running Hardy) was working well enough until this afternoon when I tried to log in.  It behaves as if something is submitting the login form every couple seconds.  I can't get my password typed in.  Once I start typing my password it posts the form and says that the password must be typed in the correct case.  I've turned off tap on the touchpad and I'm not hitting Enter.

I can log in to a different profile, but if I try to sudo or use the password from the other admin account, I get similar behavior.

The only thing that I am aware of that changed is that I loaded TinyXP into Vbox this morrning.  I also fooled around with tf-tool --acquire trying to get the finger print reader to work.

---

### Post by Fr33d0m on 2008-10-19
renamed ~/thinkfinger.bir to thinkfinger.bad and I can now log in.

---

