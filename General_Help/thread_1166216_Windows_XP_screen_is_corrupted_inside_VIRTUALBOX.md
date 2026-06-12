---
title: "Windows XP screen is corrupted inside VIRTUALBOX"
date: 2009-05-21
forum: General Help
---

### Post by aninona on 2009-05-21
#########################
the solution is in my last reply in this thread.
direct link:
[http://ubuntuforums.org/showpost.php?p=7331390&postcount=12](http://ubuntuforums.org/showpost.php?p=7331390&postcount=12)
#########################
Hello everyone.

I've installed WIN XP PRO using VIRTUALBOX inside UBUNTU Jaunty a month ago.
Everything was alright, but recently few minutes after I run windows the screen is corrupted:
[http://img259.imageshack.us/img259/3204/screenshotwinxpprorunni.png](http://img259.imageshack.us/img259/3204/screenshotwinxpprorunni.png)

And I have to shut it down.

How should I fix the problem?

Thanks!:)
[sorry for grammar mistakes if any]

---

### Post by Legace on 2009-05-21
Make sure you've allocated enough video memory for the virtual XP.

Also, see if Windows safe mode works (press F8 when you're booting Windows)..

---

### Post by aninona on 2009-05-21
> **Legace said:**
> Make sure you've allocated enough video memory for the virtual XP.

Also, see if Windows safe mode works (press F8 when you're booting Windows)..

12 MB are allocated. What size should it be?

Thanks!!

---

### Post by Legace on 2009-05-21
> **aninona said:**
> 12 MB are allocated. What size should it be?

Thanks!!

First try to boot into safe mode in Windows..
And I suggest it to be about 32MB.

---

### Post by aninona on 2009-05-21
> **Legace said:**
> First try to boot into safe mode in Windows..
And I suggest it to be about 32MB.

Hello Legace. Windows does not crash when it is in safe mode.
Allocating 32 MB does not solve the problem.
Anything else?

Thanks!![img]http://ubuntuforums.org/images/smilies/icon_biggrin.gif[/img]

---

### Post by aninona on 2009-05-22
somebody???

---

### Post by Kareeser on 2009-05-22
Have you tried installing the guest additions?

---

### Post by aninona on 2009-05-22
> **Kareeser said:**
> Have you tried installing the guest additions?

Yes I have.

Any idea? :)

---

### Post by aninona on 2009-05-22
bump[-o<

---

### Post by aninona on 2009-05-23
[SIZE="6"]Will reinstalling windows solve the problem?[/SIZE]

Thank you all![img]http://ubuntuforums.org/images/smilies/icon_biggrin.gif[/img]

---

### Post by hyperdude111 on 2009-05-23
> **aninona said:**
> [SIZE="6"]Will reinstalling windows solve the problem?[/SIZE]

Thank you all![img]http://ubuntuforums.org/images/smilies/icon_biggrin.gif[/img]

Yes, but this problem might be caused by running applications that are unstable in Virtualbox such as divx. 

You may encounter th problem again until you define the cause of the problem

---

### Post by aninona on 2009-05-23
> **hyperdude111 said:**
> Yes, but this problem might be caused by running applications that are unstable in Virtualbox such as divx. 

You may encounter th problem again until you define the cause of the problem

I think I've found the [SIZE="7"]solution:[/SIZE]

right click on desktop
properties
last tab[my windows is not in English, so I don't know how to say that]
advanced
forth tab-troubleshoot
change the ruler of 'hardware acceleration' from full to one of the others.[the first one slows the cursor so don't choose it]

Have fun!

Thanks you all!!! UBUNTUFORUMS are the BEST!![img]http://ubuntuforums.org/images/smilies/smiley-faces-80.gif[/img]

---

