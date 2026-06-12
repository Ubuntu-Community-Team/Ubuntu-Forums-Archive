---
title: "how to restart gnome?"
date: 2006-05-10
forum: Desktop Environments
---

### Post by notepad on 2006-05-10
ive recently reinstalled ubuntu and im having this bizarre problem occassionally where everything important on the screen (contents of windows and menus etc) all turns to crap. in hoping to find a simple short term solution, i thought id try restarting gnome and wait to see if this problem occurs again. so there i am pressing ctrl alt backspace and behold i find myself at tty1 with a login prompt. not quite what i expected. so now my question is:

according to this:
[http://www.cs.cornell.edu/~djm/ubuntu/#nvidia-driver](http://www.cs.cornell.edu/~djm/ubuntu/#nvidia-driver)   
at point number 4 (press ctrl alt backspace to restart gnome)
ctrl alt backspace should restart gnome

however according to posts in this thread:
[http://www.ubuntuforums.org/archive/index.php/t-35774.html](http://www.ubuntuforums.org/archive/index.php/t-35774.html)
ctrl alt backspace DOES NOT restart gnome. 


which of these sources is true? i would have previously bet money on ctrl alt backspace restarting gnome but now im not sure.

id even appreciate folks doing it on their system and letting me know what it does because im sure it used to work for me. and since using a terminal when my little problem occurs is not an option, how should i restart gnome until i can find the cause and solution for the real problem?

---

### Post by ajgreeny on 2006-05-10
I'm not sure why you only end up at a tty prompt, but from there try logging in and then enter "startx" and see what happens; it should start gdm and then go to the gui of your choice.  Perhaps someone else will give you some clues as to why this does not happen by default.

---

### Post by Cirrocco on 2006-05-10
my understanding on the matter: no it doesn't restart gnome

ctrl+alt+backspace
once at a command prompt you have to:

```
sudo /etc/init.d/gdm stop
```
to stop gnome and then to start it again:
```
sudo /etc/init.d/gdm start
```

---

### Post by red_shrike on 2006-05-10
true, true.... consider $ sudo /etc/init.d/gdm restart

---

### Post by notepad on 2006-05-10
[QUOTE=ajgreeny]I'm not sure why you only end up at a tty prompt, but from there try logging in and then enter "startx" and see what happens; it should start gdm and then go to the gui of your choice.  Perhaps someone else will give you some clues as to why this does not happen by default.[/QUOTE]

thanks ajgreeny thats what ive done to get back to x but then when i log out from the menu it chucks me back to tty1. then if i type in gdm as root it says gdm is already running so clearly ctrl alt backspace DOES NOT kill gdm. pressing ctrl alt f7 doesnt do anything. something is wrong.

am i to understand that when you hit ctrl alt backspace that your gnome restarts? im sure mine used to so now im perplexed as to why it isnt anymore.

---

### Post by Dr. Nick on 2006-05-11
[quote=notepad]thanks ajgreeny thats what ive done to get back to x but then when i log out from the menu it chucks me back to tty1. then if i type in gdm as root it says gdm is already running so clearly ctrl alt backspace DOES NOT kill gdm. pressing ctrl alt f7 doesnt do anything. something is wrong.

am i to understand that when you hit ctrl alt backspace that your gnome restarts? im sure mine used to so now im perplexed as to why it isnt anymore.[/quote]

ctrl+alt+backspace restarts Xorg I believe, This in effect restarts gnome as your entire GUI is resterted, now it wont kill gdm i sibt think. What is the "crap" you get, I wouldnt think it to be a gnome problem, but instead a Xorg problem, like drivers,color depth etc

---

### Post by red_shrike on 2006-05-12
Have you tried lowering bit-depth or resolution slightly? Maybe frequency? You can try killing everything by typing $ sudo kill -9 -1 right before stoping gnome so...
$ sudo /etc/init.d/gdm stop
$sudo kill -9 -1
$sudo /etc/init.d/gdm start

or $ ps -C xorg
     $ kill {xorg id ps gives you}

---

### Post by notepad on 2006-05-14
well it seems to be my kernel. when i boot kernel 2.6.12-10, ctrl alt backspace gives me tty1 but when i boot kernel 2.6.12-9 my ctrl alt backspace gives me my themed greeter (gdm?). i guess this answers 2 questions that i had

1. what is ctrl alt backspace supposed to do? 
answer: it restarts gnome (if your kernel isnt #$*&%)

2. what causes the problem ive described?
answer: the kernel that im using. cant wait for them to fix it.

---

