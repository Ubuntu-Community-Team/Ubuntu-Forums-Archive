---
title: "weird keyboard problem"
date: 2009-06-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by studiodude on 2009-06-27
I just talked my wife into ditching Vista in favour of Ubuntu on her Dell Vostro 1000, she has been using open office for years anyway and isnt a massively heavy user, bit of internet and email and preparing her classes for school.  We are English but live in Spain and the version of Vista was in Spanish.  I have installed Ubuntu on a number of machines now and all are working fine with a bit of tweaking, all are bought here and had Spanish versions of Windows on before.  I have never had this problem before, but on her dell the right alt key (Alt Gr) is not working (it was in Vista), this is the key that gives the third option and on a Spanish keyboard gives access to the "@" sign - fairly well used by anyone these days.  I have managed to reassign the third option to the right control key, but am at a loss as to why the key should become unavailable under ubuntu. It hasnt happened on any of my other machines and they all have Spanish keyboards and I did set it up right on install.  Can anyone shed any light on it please?  Thanks as always in advance.

---

### Post by coffeeaddict22 on 2009-06-27
Hi,
I'm desperately monolingual, so haven't had to deal with the identical problem.  However, a couple of suggestions (sorry if you've tried them):

1) check in System/Preferences/Keyboard that you've picked the layout you've got on your other keyboards.  While you're in there, look under layout options/ Alt key behaviour to see if you can set it there.

2) check the key is still working.  In a terminal, type ```
xev
```It'll open an event box, but more importantly in the terminal every time you hit a key it reports what's being sent to the system.  If it's a crumb under the key, nothing should happen.

---

### Post by studiodude on 2009-06-28
Thanks coffeeadict22 - i used the xev command to acertain that the key was indeed working.  This lead me to further explore the options in system>preferences>keyboard and I found that I could change the keyboard model.  I picked a Dell laptop option and it is now sorted - I didnt know it was there before as all my other keyboards have worked out of the box.  Handy command to know though that "xev" and i have changed my other laptops keyboard models to match just in case and to hammer it home that the command exists should I ever come across it again. 

SORTED!!

---

