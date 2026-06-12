---
title: "How to edit /etc/inittab"
date: 2009-06-10
forum: General Help
---

### Post by rbueno on 2009-06-10
Hi guys!,
need help here..

i have installed server edition with gnome..
i have to edit the inittab in order my gui login appears every time i booted up server.
problem is how to edit /etc/inittab in terminal
i'm using **vi /etc/inittab** but i can't save any changes..
i can't open any text editor because its fully terminal command only..

best regards,

---

### Post by michy99 on 2009-06-10
```
sudo vi /etc/inittab
```
This gives you root privileges to save.

---

### Post by rbueno on 2009-06-10
yes,
i've used sudo vi but how to save?
what key i need to press?
Ctrl+s did'nt worked

---

### Post by michy99 on 2009-06-10
Sorry, I've never used vi. I use nano instead. In nano you save with Ctrl+O and exit with Ctrl+x.

---

### Post by rbueno on 2009-06-10
you mean vi /etc/inittab = nano /etc/inittab?? am i correct?

---

### Post by Sarai the Geek on 2009-06-10
Have you tried gedit? It's a gui-based text editor that I find is a little more straightforward to use for stuff like config files.

```
gksudo gedit /etc/inittab
```

---

### Post by michy99 on 2009-06-10
> **rbueno said:**
> you mean vi /etc/inittab = nano /etc/inittab?? am i correct?

Yes, nano is just another command-line text editor that some people prefer to vi. (I hope we don't get a war started here.)

---

### Post by rbueno on 2009-06-10
nah!!
i've said earlier that i can't open any text editor because i'm installing gnome on ubuntu server

---

### Post by rbueno on 2009-06-10
thanks mitchy
bdw this is not a war zone^_^
that just the way i am..:lolflag:

---

### Post by michy99 on 2009-06-10
> **rbueno said:**
> thanks mitchy
bdw this is not a war zone^_^
that just the way i am..:lolflag:

LOL..I was referring to the vi vs. nano war, which has been known to get pretty heated.

---

### Post by rbueno on 2009-06-10
ok!!! ok!!!
hehe!!
nano is more easier to used than vi!
is there any bugs working on vi?
i found a hard time to type text because it needs replace and insert command and i don't know how to save any changes

---

### Post by Sarai the Geek on 2009-06-10
> **rbueno said:**
> nah!!
i've said earlier that i can't open any text editor because i'm installing gnome on ubuntu server

Whoops, sorry, I missed that bit!

---

### Post by andersbk on 2009-09-07
> **rbueno said:**
> ok!!! ok!!!
hehe!!
nano is more easier to used than vi!
is there any bugs working on vi?
i found a hard time to type text because it needs replace and insert command and i don't know how to save any changes

Learning to use vi (or vim) is worth your time. There may be a time you need to work on a computer or server that does not have a gui, or does not have a "simple" text editor like nano.

Here's a good starting point.

[http://thomer.com/vi/vi.html](http://thomer.com/vi/vi.html)

PS. When I first started my job right out of school a mentor of mine said..."You just need to be good enough with 'vi' so you don't look like an idiot." :D

good luck editing!
.eom.

---

