---
title: "Fusion &amp; Emerald themes"
date: 2007-06-29
forum: Desktop Effects &amp; Customization
---

### Post by detroit/zero on 2007-06-29
Hi,

After digging through posts I wasn't able to find anything that specifically addresses an issue I'm having, so here we are.

I just switched from Beryl to Fusion. I have Emerald hanging out and would like to use my Emerald themes as opposed to the plain-jane theme Fusion has selected for me (which, I think, is the Metacity them I have selected..?).

At any rate. there's plenty of posts on how to accomplish this. They generally say things like
```
compiz --replace emerald --replace
``````
compiz --replace -c emerald --replace
``````
compiz --replace -c emerald --replace &
```and so on.

All of these methods work - all of them - in a terminal window. I can't get my Emerald theme to run at startup by entering those commands in System>Preferences>Sessions; I have to run Emerald in a terminal window. And, here's what I really am trying to learn here (because this happens with a couple of other applications I use such as *Firestarter*), **Emerald will only stay in active as long as that particular terminal window is open.**

What gives? Firstly, why won't those commands execute when they're entered through Sessions? Secondly, how do you keep an application running (like Emerald or Firestarter) once you've closed the terminal window that you executed it in?

Thanks for any help.

---

### Post by Mr Greencastle on 2007-06-29
When you start a process in the terminal, it is 'tied' to that terminal, so when you close the terminal, the process is usually ended.
There are a few ways around this:

1. Try typing 'exit' (without quotes) instead of pressing the X button in your terminal.

2. Try pressing ALT+F2, then typing emerald --replace

Also, for your startup sessions, did you put 'compiz --replace emerald --replace' all in one command?

Try putting them separate:
```
Name: Compiz
Command: compiz --replace

Name: Emerald
Command: emerald --replace
```

Try this and we'll see where we can go from here...

Good luck.

---

### Post by detroit/zero on 2007-06-29
Easy enough. I didn't think of splitting up the commands like that. Simple fix.. Thanks a million! 

I'll take my question on terminal windows and running apps to the beginner board, since that part is off topic here.

Thanks again!

---

### Post by Mr Greencastle on 2007-06-29
No problem!

Mr Green

---

### Post by detroit/zero on 2007-07-06
As a side note, as far as Emerald and Firestarter not staying open when the terminal window closes - I have since learned the difference between **sudo** and **gksudo.**

Just thought I'd add that...

---

