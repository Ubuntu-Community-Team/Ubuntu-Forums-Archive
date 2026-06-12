---
title: "way to log keystrokes?"
date: 2006-05-09
forum: Desktop Environments
---

### Post by dgermann on 2006-05-09
Hi--

I am about to re-install a program that has given me fits, and I would like to have a way to create a log of all I do so I can trouble shoot it later.

Is there a way to make that happen in a command line environment?

Thanks!

---

### Post by ComplexNumber on 2006-05-09
in your home directory, theres a file called .bash-history (i think its preceded by a "." anyway - that means that its a hidden file. to see hidden files, go into nautilus -> preferences -> view hidden files).

---

### Post by dgermann on 2006-05-09
ComplexNumber--

Wow! It's already done for me!

Thanks, ComplexNumber--you made it simple! ;)

---

### Post by ComplexNumber on 2006-05-09
glad to help :)

---

### Post by Clay85 on 2006-05-09
Hey I know something, I know something! You can also open up your Home folder through Places and push CTRL+H!

(Sorry, I'm a bit excited. This is my second day using Ubuntu.)

---

### Post by dgermann on 2006-05-10
Complex Number--

One other thing: is there a way to also capture the responses and particularly the error messages I get in response to the commands I enter? Interspersed with those commands?

It would be great for trouble shooting if I could....

Thanks for your help.

Clay85--

Yeah, ain't it neat! Any other little tidbits you're discovering?

---

### Post by ComplexNumber on 2006-05-10
> One other thing: is there a way to also capture the responses and particularly the error messages I get in response to the commands I enter? Interspersed with those commands?
it *should* be in the same place on ubuntu, but try /var/log/message file. there's virtually everything recorded there.

---

### Post by dgermann on 2006-05-11
ComplexNumber--

Thanks, I'll give that all a look-see as I start this project.

Thanks!

---

### Post by art on 2006-05-11
If you want to log everything you type and get on the terminal, there is a nice program called "screen", just type screen in the terminal, and all you see will be logged to a file screenlog.0 or some other name. Before you start do
```
gedit ~/.screenrc
deflog on
```

Save the file and now you can proceed 
HTH

---

### Post by dgermann on 2006-05-13
Art--

Wonderful suggestion!

I will try it for the next stage of this project. Thanks!

---

