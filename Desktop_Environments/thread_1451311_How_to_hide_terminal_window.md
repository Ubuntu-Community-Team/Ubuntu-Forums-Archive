---
title: "How to hide terminal window?"
date: 2010-04-10
forum: Desktop Environments
---

### Post by Kognit on 2010-04-10
Hello

I am wondering if you run an application thrugh the terminal is there any option to hide a terminal window and at the same time the application won't close?

thx for the Help

bye

---

### Post by ackley on 2010-04-10
Why not just run it by hitting alt+f2 & typing in exactly what you put in the terminal?

Save for "sudo" if it's a command like that, but gksu or kdesu would work.

---

### Post by Kognit on 2010-04-10
Thank you for replying!

Yes, i have totally forgot about the "alt+F2" command. It works fine. But sometimes i need a terminal because some commands doesn't work in "alt+F2.

Is there any other way?

thanks for helping!

---

### Post by sisco311 on 2010-04-10
start it in the background:
```
command &
```
then run:
```
disown
```and close the terminal.

You can stop a foregrounded application with Ctrl+z, then start it in the background (foreground) with the bg (fg) command.

---

### Post by Kognit on 2010-04-10
> **sisco311 said:**
> start it in the background:
```
command &
```
then run:
```
disown
```and close the terminal.

You can stop a foregrounded application with Ctrl+z, then start it in the background (foreground) with the bg (fg) command.

THANKS MAN!!
The "command &" and "disown" helped a lot. Thank you again. 

ALT+Z and bg, fg don't find them useful for me. 

Thanks again

---

### Post by sisco311 on 2010-04-10
> **Kognit said:**
> THANKS MAN!!
The "command &" and "disown" helped a lot. Thank you again. 

ALT+Z and bg, fg don't find them useful for me. 

Thanks again

You're welcome!

I always forget to start apps in the background, so I have to stop & background them... :)

---

### Post by Kognit on 2010-04-10
I have another question.

If i want to create a launcher in which a command is run through Terminal how should i write "command &" and "disown"?

---

### Post by sisco311 on 2010-04-10
> **Kognit said:**
> I have another question.

If i want to create a launcher in which a command is run through Terminal how should i write "command &" and "disown"?

If you only want to run a command in bash, you don't have to start a terminal at all:

```
bash -c "command"
```

But, I'm not sure if I understand your question correctly.

---

### Post by Kognit on 2010-04-10
I meant something different. 
Suppose i want to create a launcher where the application would run through terminal (option "Application in Terminal"). So, how to write "command &" and "disown", for example fot the vlc player? I am asking this because i have some libraries for vlc and skype (because of my webcam flip problems) to run and i want to be able to close the terminal after this commands if i create launcher.

Actually i mean how to write in terminal multiple commands.I tried "command1 ; command2", but the catch is that the command2 runs only after command1 is finished, closed. I doesn't open consecutively. Actually it is strange - for example: id i write "gedit ; oowriter", first is opened gedit and after the gedit is closed, oowriter opens. But if i write "oowriter ; gedit", than both applications opens consecutively.

I hope that you understand me :)

---

### Post by hariks0 on 2010-04-10
You can use alltray for minimising the terminal [or any window] in to the system tray.

---

