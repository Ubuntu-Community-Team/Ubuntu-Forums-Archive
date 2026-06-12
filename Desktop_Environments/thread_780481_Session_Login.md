---
title: "Session Login"
date: 2008-05-03
forum: Desktop Environments
---

### Post by Jack3760 on 2008-05-03
Before I upgraded to 8.04 on booting up I would get a Options  screen that would prompt me to select a session. Among others were Gnome and KDE4. I would select one or the other and then enter my user name and password and either KDE4 or Gnome would appear on my desktop. 
Since the upgrade I no longer get the Options portion of the login screen. I only get Gnome.
What steps do I need to do the get back to KDE4?

---

### Post by Xiong Chiamiov on 2008-05-04
Which login screen are you getting, the gdm one or the kdm one?  Do you not have the little box or whatever it is that allows you to select a session, or is it just that you aren't prompted every time?

---

### Post by Jack3760 on 2008-05-05
I do not get the second litle box that requests the session I want to use. All I am seeing is a large bos looking for User and then Password.
Under Gutsy after installing KDE4 I was asked which session I wanted. Switching between the two allowed me to learn a bit more about each. 
I am a really new U(K)buntu user. 
Thanks

---

### Post by Xiong Chiamiov on 2008-05-05
Which does your login screen look more like, [this]("http://bp3.blogger.com/_crimgO_xQv0/RzWzsV_XuyI/AAAAAAAAAiA/P-83-uuL-i8/s1600-h/Gutsy-Login.jpg") or [this]("http://canllaith.org/wp-content/images/Gutsy/kdm.jpg") or [this]("http://www.thelins.se/images/Kde4a2-thumb-login.png")?

---

### Post by Jack3760 on 2008-05-08
I get none of the login screens shown. 
The fist one is the closest to what I have.
Not much help I guess.
It starts out with what looks like a Kubuntu screen and then when I log in it automatically comes up Gnome. 
I just want what I had before. The ability to chose.

Thanks

---

### Post by Xiong Chiamiov on 2008-05-09
Do you have the options in the bottom left, like there?

If not, you can try reinstalling gdm
```

sudo apt-get reinstall gdm --purge

```
(I think that's correct, just off the top of my head)

---

