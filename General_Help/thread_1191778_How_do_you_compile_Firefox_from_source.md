---
title: "How do you compile Firefox from source?"
date: 2009-06-18
forum: General Help
---

### Post by t4thfavor on 2009-06-18
Ouch! Thats just how you learn. I would recommend Google. It helps me find things everyday. 

He said 3.5 beta, and we only have 3.0.xx installed by default.


Also, where do you get the source, I would like to try that as well.

I'm getting it from here
[ftp://ftp.mozilla.org/pub/firefox/nightly/3.5b4-candidates/build1/source/](ftp://ftp.mozilla.org/pub/firefox/nightly/3.5b4-candidates/build1/source/)

---

### Post by t4thfavor on 2009-06-18
Do what this page says, and you should be good to go, I am compiling now.
[https://developer.mozilla.org/en/Linux_Build_Prerequisites](https://developer.mozilla.org/en/Linux_Build_Prerequisites)

The main page also has good build info

[https://developer.mozilla.org/en/Build_Documentation](https://developer.mozilla.org/en/Build_Documentation)


EDIT:
Still building btw, its not the fastest PC around, but it does have 4GB ram in it.

EDIT2:
Compile completed, sudo make install worked as well, but I have no idea how to run it after that... So I'm at a loss. Hopefully I was of some help.

---

### Post by robert shearer on 2009-06-18
> Compile completed, sudo make install worked as well, but I have no idea how to run it after that... So I'm at a loss. Hopefully I was of some help.

Try Alt+F2 and type in firefox3-5

---

### Post by t4thfavor on 2009-06-19
Nope, doesn't do anything. It's no big deal, I just like to compil things.

---

### Post by t4thfavor on 2009-06-29
OK, it miraculously worked after I rebooted my PC I dont do that very often.

Now I need info on how to uninstall it as the standard sudo make uninstall says no rule to make target uninstall.

---

### Post by oldos2er on 2009-06-29
You need to run **sudo make uninstall** from the same directory where you ran **sudo make install**.

---

