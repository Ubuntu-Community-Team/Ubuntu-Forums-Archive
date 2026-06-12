---
title: "compiz help"
date: 2008-04-22
forum: Desktop Environments
---

### Post by lledurt on 2008-04-22
Thanks for your help in advance.

I am having trouble enabling visual effects on 7.04

Every time I change it to anythign other than none I get a window "Desktop Effects could not be enabled"

I have 3 monitors so I had to modify my xorg.conf manually(Xinerama).
I have the same problem on my 2 monitor machine (twinview)

I am using the nvidia driver.  I am guessing it is one of my options that I have enabled in the xorg.conf file.

I have heard barrel does not work with Xinerama, but I thought compiz does?

Attached is my xorg.conf file

I tried to attach my output of dpkg -l but the file was too large.

Thanks for your help in advance

P.J.

---

### Post by caveman59330 on 2009-05-02
hey check out this website it has a handy tool to check and see if your computer can handle compiz fusion. It will tell you what driver you are using and some other stuff to help you troubleshoot the problem.

link
[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

here is the just of it 
use this in terminal to download script to home directory

You can use this command to download it to your home directory:                  [COLOR=#121212]wget [http://blogage.de/files/9124/download](http://blogage.de/files/9124/download) -O compiz-check[/COLOR]
                 Afterwards, you have to make it executable:                  [COLOR=#121212]chmod +x compiz-check[/COLOR]
                 And finally run it like this:                  [COLOR=#121212]./compiz-check

[/COLOR]

---

### Post by overdrank on 2009-05-02
> **caveman59330 said:**
> 
link
[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)



Did you notice the thread is over a year old. :)

---

### Post by lledurt on 2009-05-08
Thanks Guys,
I gave up on it a while ago, but I will give it a try next week and report my success back.
P.J.

---

### Post by Kareeser on 2009-05-08
Unfortunately, Xinerama will not work with Compiz. Use TwinView instead, that works better, in my experience, plus, you will be able to use Compiz.

---

