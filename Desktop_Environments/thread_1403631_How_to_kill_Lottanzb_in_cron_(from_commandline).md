---
title: "How to kill Lottanzb in cron (from commandline)"
date: 2010-02-10
forum: Desktop Environments
---

### Post by mister_p_1998 on 2010-02-10
Hi Guys,
Im using Hellanzb for my newsbin downloads, with Lottanzb as the gui front-end. my connection is measured, so I kill all downloads in cron at 18:00. however, I cant kill Lottanzb, it just sits there saying it cant find Hellanzb. in Atop its called /usr/bin/hella, I cant kill it by that name. I can kill it by pid, but thats different every time so I cant put that in the Cron. I'm stumped, any ideas guys?

Steve

---

### Post by mats! on 2010-02-10
It's a nasty one liner, but it should work for you.
```
ps aux | grep hella | grep -v grep | awk '{print $2}' | xargs kill -9
```

Put that in a crontab entry, and it should kill the hella process by it's pid, no matter if it changes.

Hope it helps.

---

### Post by Satoru-san on 2010-02-10
> **mats! said:**
> It's a nasty one liner, but it should work for you.
```
ps aux | grep hella | grep -v grep | awk '{print $2}' | xargs kill -9
```Put that in a crontab entry, and it should kill the hella process by it's pid, no matter if it changes.

Hope it helps.
That doesnt work. This does and its a lot shorter.

```
 killall `ps aux | grep hella`
```
^ Thats a bad way to do it, I fixed mats! one..

```
kill `ps aux | grep hella | grep -v grep | awk '{print $2}'`
```

you could also do:
```
killall `ps aux | grep hella | grep -v grep | awk '{print $11}'`
```

---

### Post by mister_p_1998 on 2010-02-11
I tried them all guys, none of them worked!!
Back to the drawing board!
Steve

---

### Post by mister_p_1998 on 2010-02-12
Aha!
Just realised my mistake!
I want to kill Lottanzb! not Hella! my mistake, when I enter
kill `ps aux | grep hella | grep -v grep | awk '{print $2}'`

It works perfectly, thanks guys
Steve

---

### Post by Satoru-san on 2010-02-12
> **mister_p_1998 said:**
> I want to kill Lottanzb! not Hella! my mistake, when I enter
kill `ps aux | grep hella | grep -v grep | awk '{print $2}'`
Steve
the `` are great.

I dont even know what lottanzb is the other man said hella so I went on that, the command its self works for any application.

If you could please mark your thread as solved by using the thread tools. Thank you. :D

---

### Post by mister_p_1998 on 2010-02-13
Just out of interest..
can you explain in depth what the commands do?
in case I need to do it somewhere else...

Steve

---

### Post by Satoru-san on 2010-02-20
> **mister_p_1998 said:**
> Just out of interest..
can you explain in depth what the commands do?
in case I need to do it somewhere else...

Steve
> **Satoru-san said:**
> That doesnt work. This does and its a lot shorter.

```
 killall `ps aux | grep hella`
```^ Thats a bad way to do it, I fixed mats! one..

```
kill `ps aux | grep hella | grep -v grep | awk '{print $2}'`
```you could also do:
```
killall `ps aux | grep hella | grep -v grep | awk '{print $11}'`
```

Basically anything inside of `` will be executed.  kill and killall will do just that killall is for names kill is for process ids. 

when you pipe | you are sending the output to another application. so | grep hella will search ps aux for hella. 

| grep -v grep will remove grep from the grep results. 

awk is a string searching utility. '{print $2}' is the second word displayed. In this case the process id.

then back to the `` it will execute that stuff then run kill on the result.

PS. sorry for the late response I will send you a pm letting you know I explained this for you.

---

