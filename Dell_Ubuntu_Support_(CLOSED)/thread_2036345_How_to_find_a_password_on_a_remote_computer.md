---
title: "How to find a password on a remote computer?"
date: 2012-08-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by joco1500 on 2012-08-01
Hello.
I have downloaded Ubuntu on my laptop and have loved it. Then i decided to dust off my old desktop and install it there. 

But theres my problem. 
its been so long since i used it i forgot my password.

is there a way to ssh into it and retrieve the password or do i have to go on another route.

i am running windows 7 on my desktop and ubuntu 12.04 on my laptop.
 anything would help.

---

### Post by drmrgd on 2012-08-01
No, you won't be able to ssh into the Windows box if you don't have a password.  Even more problematic is the fact that a ssh service is probably not running on that box by default anyway.

You'll have to use a password recovery utility to recover your Windows password unfortunately.  It doesn't appear (from a quick Google search that is) to be all that easy in Windows.  It's much easier to recover in Ubuntu!

---

### Post by joco1500 on 2012-08-01
ok thanks man

---

### Post by Scott Harrison on 2012-08-02
Konboot is the tool for you: [http://www.piotrbania.com/all/kon-boot/](http://www.piotrbania.com/all/kon-boot/)

Give that a crack and laugh at the epic flaws in Windows security.

---

### Post by thnewguy on 2012-08-03
Assuming you have physical access to the Windows box you can either
A) install Ubuntu over Windows without requiring a password
B) Boot from the Ubuntu CD, download the chntpw command and use it to reset your Windows password.

---

### Post by gerrman97 on 2012-10-22
kon-boot is great. i broke into my computer several times because of forgotten password. PM me and maybe i can give you a link.

---

