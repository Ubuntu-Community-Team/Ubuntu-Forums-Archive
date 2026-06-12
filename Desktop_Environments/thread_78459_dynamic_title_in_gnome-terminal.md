---
title: "dynamic title in gnome-terminal"
date: 2005-10-18
forum: Desktop Environments
---

### Post by tasuki on 2005-10-18
Hello people,

I have this weird problem: the dynamic title of gnome-terminal is set by some applications (such as vim), but not by terminal itself. I do not know whether I am clear, so I will show an example:

It used to have a title like "vita@doma:/home/vita/games" which changed according to my actual directory (and on my sister's comp it still works this way, it even sets the title on my gnome-terminal when I ssh there - spooky).

Now I wonder which program is responsible for setting the title? I think it is not mistake of my gnome-terminal (well, I tried using ~/.gconf/apps/gnome-terminal/ from system where it works ok and nothing changed here).

Hmmm, it is probably still not very clear... but I am afraid I can't describe it any better...

Thank you for possible reply,
Vit

---

### Post by dccarson on 2005-12-02
[QUOTE=tasuki]Hello people,

I have this weird problem: the dynamic title of gnome-terminal is set by some applications (such as vim), but not by terminal itself. I do not know whether I am clear, so I will show an example:

It used to have a title like "vita@doma:/home/vita/games" which changed according to my actual directory (and on my sister's comp it still works this way, it even sets the title on my gnome-terminal when I ssh there - spooky).

Now I wonder which program is responsible for setting the title? I think it is not mistake of my gnome-terminal (well, I tried using ~/.gconf/apps/gnome-terminal/ from system where it works ok and nothing changed here).

Hmmm, it is probably still not very clear... but I am afraid I can't describe it any better...

Thank you for possible reply,
Vit[/QUOTE]


Alas, I don't have the answer, but since no one has responded to your query, I'll commiserate.

FIrst off, I use bash as my shell and my PS1 prompt is '($?)[\u@\h \W] '.

OK, so I was using Fedora Core 3 before yesterday, but Gnome Terminal was acting as I expected it to, namely:
[LIST=1]
[*] title is set to my PS1 prompt (or something similar)
[*] title changes when I ssh (new host shows up properly)
[*] title changes back when I logout of ssh session (previous host restored)
[/LIST]
Now, with Breezy and a newer version of Gnome, I'm surprised by the behavior, namely:
[LIST=1]
[*] title is not set initially -- it is Terminal
[*] title changes when I ssh -- still OK
[*] title does NOT change back when I logout
[/LIST]

---

### Post by 23meg on 2005-12-02
See if changing the "Dynamically set title" option in the "Title and Command" tab of your Gnome terminal profile settings does what you want.

---

### Post by dccarson on 2005-12-02
[QUOTE=23meg]See if changing the "Dynamically set title" option in the "Title and Command" tab of your Gnome terminal profile settings does what you want.[/QUOTE]

It is set to "Replaces initial title" -- same as I had it in FC3.

---

### Post by hw-tph on 2005-12-02
Try setting "run command as a login shell" in your Gnome Terminal profile.


H&#229;kan

---

### Post by ned.b on 2006-01-14
gnome-terminal --title=your_desired_title  

 - does not work I wonder if the title feature is bugged in Breezy?

---

### Post by thejackos on 2007-08-29
I had this problem too. The difference is in the system-wide bash initialization file. On RH-based systems there is a file /etc/bashrc which sets up PROMPT_COMMAND to set the title for xterms (when $TERM==xterm). Where-as Ubuntu uses /etc/bash.bashrc, which has the equivalent section commented out. Either modify the system wide configuration to do what you want, or you can set up PROMPT_COMMAND in your own ~/.bashrc file.

It is a good thing to test for PS1 to see if the shell is interactive, and an even better to check for TERM being xterm to make sure you don't get escape character garbage on your screen should you ever log in from a different terminal type. :-)

---

### Post by thejackos on 2007-08-30
> **thejackos said:**
> 
It is a good thing to test for PS1 to see if the shell is interactive, and an even better to check for TERM being xterm to make sure you don't get escape character garbage on your screen should you ever log in from a different terminal type. :-)

More strictly speaking checks for xterm* (and if you like other names that terminals that understand the escape sequences set the TERM environment variable to), see the commented out part of the system configuration, or one from a system that "works".

---

### Post by arijarot on 2008-05-04
A quick solution to this problem is to make sure that /etc/bash.bashrc file has a line uncommented. That is,

```
sudo gedit /etc/bash.bashrc
```

Then, look for ```
PROMPT_COMMAND='echo -ne "\033]0;{USER}@${HOSTNAME}: ${PWD}\007"'
```

Make sure that there ISN'T any # before it. If there is, delete the #. This should solve the problem.

---

