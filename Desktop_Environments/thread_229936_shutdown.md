---
title: "shutdown"
date: 2006-08-05
forum: Desktop Environments
---

### Post by matko on 2006-08-05
hello.

when push shutdown button I can choose in "hibernate, logoff, swith user and lock"

there is no shutdown, i probably need to install that package that contains it.

```
do you know what is name of that package?
``` 

thank you

---

### Post by jordilin on 2006-08-05
No, is very strange. You should be able to shutdown your computer with a specific button that says "shutdown". Restart your computer, and see if that happens again, type:
```
sudo shutdown -r now
```

---

### Post by Touque on 2006-08-17
Yup, I have exactly the same query. No shutdown option when I click on the logoff button.

---

### Post by eXcentra on 2006-08-17
By any chance, are you using xgl? I know that when I use xgl/compiz, I have to logout and then shutdown at the login screen because there is no shutdown button.

---

### Post by shoagun on 2006-08-17
Yeah, I have the same problem.  I've read about it in many other forums.  It's caused by one fot two things:

1.  You're running xgl+compiz, in which case there's no solution (as far as I've read) (I think this migh only apply if you have xgl+compiz set up on a separate session, but I'm not sure)

2.  You have to go to System>Adim>Login Window and click "Show Actions menu"

---

