---
title: "Missing Menu Items"
date: 2009-05-11
forum: General Help
---

### Post by Bender2k14 on 2009-05-11
For no apparent reason, I am missing a few menu items that are supposed to be there in Ubuntu 9.04 Jaunty.  I know that I am missing "Software Sources" and "Login Window", both of which are in "System->Administration".

What I really would really like to know is how to reset or rebuild the menu items to the way they are in a new instillation of Jaunty.  Does anyone know how to do this?

---

### Post by BslBryan on 2009-05-11
Hello, Bender2k14. :-)

It's pretty simple.  All you have to do is hover over the System panel menu, do not left-click, but Right-click --> Edit Menus.

I hope I've been of some help. :-)

Best to you, and good luck.

---

### Post by Tipped OuT on 2009-05-11
> **BslBryan said:**
> Hello, Bender2k14. :-)

It's pretty simple.  All you have to do is hover over the System panel menu, do not left-click, but Right-click --> Edit Menus.

I hope I've been of some help. :-)

Best to you, and good luck.
[B]
Noob Translation:[/B]

Right click on the Ubuntu logo on your panel. Click on "Edit Menus". Then the rest is self explanatory.

Not saying you're a noob, its just for in case.

---

### Post by Bender2k14 on 2009-05-11
> **BslBryan said:**
> All you have to do is hover over the System panel menu, do not left-click, but Right-click --> Edit Menus.

I was not clear in that I wanted a way that would automatically do this.  However, following your directions opens up the "Main Menu" settings window which has the "revert" button.  This did not work (that is, "Login Window" and "Software Sources" remained unchecked).  So I checked them manually, but after one second, they automatically unchecked themselves.

So my two new questions are (1) why are my menu items automatically unchecking themselves and (2) how can I get them to stay checked?

---

### Post by kd0afk on 2009-05-18
> **Bender2k14 said:**
> I was not clear in that I wanted a way that would automatically do this.  However, following your directions opens up the "Main Menu" settings window which has the "revert" button.  This did not work (that is, "Login Window" and "Software Sources" remained unchecked).  So I checked them manually, but after one second, they automatically unchecked themselves.

So my two new questions are (1) why are my menu items automatically unchecking themselves and (2) how can I get them to stay checked?
I am having the same problem with the unchecking. What is more, I am missing whole categories on mine here is a screen shot.
[http://img219.imageshack.us/img219/219/screenshot1e.png](http://img219.imageshack.us/img219/219/screenshot1e.png)

---

### Post by Bender2k14 on 2009-05-20
Ok, I figured out my problem.  My user account was not the original account on the system.  When my account was created, I was not given permissions to do everything.  I logged onto the original account and gave myself all rights by going to System->Administration->Users and Groups, click Unlock, enter your sudo password, click the user name that is experiencing the problem that I described above, click Properties, click User Privileges, and finally check the box (or boxes) that allow the stubborn menu item to appear.  I just gave myself all privileges.

Hope this solves someone else's problem.

---

### Post by Dex73 on 2009-05-20
> **kd0afk said:**
> I am having the same problem with the unchecking. What is more, I am missing whole categories on mine here is a screen shot.
[http://img219.imageshack.us/img219/219/screenshot1e.png](http://img219.imageshack.us/img219/219/screenshot1e.png)

A whole category usually disappears when all the applications associated with it are unchecked. May be worth looking into.

---

### Post by hmazuji on 2012-03-10
i am experiencing the same problem, although i am logging in with the same account i created when i installed this o.s.
the first few times i started the o.s., the menu items were all there.
suddenly they disappeared.
this is a linux problem; a known issue, as others are having the same problem.  it's happened to me in ultimate edition, and in debian.  and there's no excuse for it.
it makes me wonder what else is missing that i can't see or that i haven't noticed.

---

### Post by Frogs Hair on 2012-03-10
> **hmazuji said:**
> i am experiencing the same problem, although i am logging in with the same account i created when i installed this o.s.
the first few times i started the o.s., the menu items were all there.
suddenly they disappeared.
this is a linux problem; a known issue, as others are having the same problem.  it's happened to me in ultimate edition, and in debian.  and there's no excuse for it.
it makes me wonder what else is missing that i can't see or that i haven't noticed.

Start a new thread because the old  threads are usually closed . The operating system in this thread is no longer supported .

---

