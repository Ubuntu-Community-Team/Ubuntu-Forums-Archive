---
title: "Beryl works... Beryl-manager dosent?"
date: 2007-05-24
forum: Desktop Effects &amp; Customization
---

### Post by LollYouSuckZor on 2007-05-24
Okay, Sucessfully installed. Now im stuck in it, lol.
  I typed,


beryl



and im able to scroll my screen around and turn it around in a cube, but how do I get out of this now...

---

### Post by SomethingCronic on 2007-05-24
```
ps -aux | grep beryl
```

on the first line of output on the second column you'll see a number. This is the process ID. Type

```
kill 2323
```

..or whatever the proc id is and it *should* stop.

---

### Post by LollYouSuckZor on 2007-05-24
Okay.. but once I type, Beryl im trapped.  I can flip my screen and what not, but I cant see my typing or what.  I know im able to do things, because when I rebooted I had about several new folders on my desktop. ^^

---

### Post by SomethingCronic on 2007-05-24
Ok, I didn't realise you couldn't see anything.

What video card are you using, also you may want to post your xorg.conf file (/etc/X11/xorg.conf).

---

### Post by LollYouSuckZor on 2007-05-24
What I dont understand, is why dosen't

beryl-manager work.

I use Nvidia.

---

### Post by LollYouSuckZor on 2007-05-24
How can I get this fixed?

beryl in the konsole works fine, but it traps me, I am able to rotate my screen and all, but I cannot escape it, and I cant type.  I use Nvidia Geforce Generic. I was wondering, how can I get Beryl-manager to work so I can start changing some stuff?

---

### Post by eentonig on 2007-05-24
To stop Beryl if it behaves like this

<ctrl><alt><F2> to open a new terminal.
Login and do the commands that SomethingCronic proposed.

But as to how to solve this? I have no clue. Maybe start by disabling ALL the eyecandy in Beryl-Manager before starting Beryl. And see if that still works in it's most basic form. If it does, start activating plugins one-by-one.

---

### Post by woozyking on 2007-05-24
Seriously, Beryl is currently not good for Ubuntu 7.04!!!

I'm not joking, I reinstalled Ubuntu 3 times for it, tried everything whether relevant or not, and eventually stick with "more feisty compatible" compiz. Even thought I know it's just a little bit "more feisty compatible".

Btw I use ATi card.

---

### Post by SomethingCronic on 2007-05-24
If we look at your xorg.conf file we might have a better idea of what is causing the problem. I don't know anything about your system yet except that it is using an nvidia card and running beryl.

try this:

```
cat /etc/X11/xorg.conf
```

and paste all the output into a message here. Then we can start to have a look.

---

### Post by LollYouSuckZor on 2007-05-24
It says that there is no such file or directory..

---

### Post by SomethingCronic on 2007-05-24
Make sure you're typing it in the correct case. Linux is case sensitive i.e you typed 'X11' not 'x11'

---

### Post by Soybean on 2007-05-24
So, what happens if, instead of typing "beryl", you type "beryl-manager"? I mean, you say it's not working, but... what type of not working? ;)

---

