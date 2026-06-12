---
title: "how can i set password confirmation when leaving lock screen"
date: 2008-09-29
forum: Desktop Environments
---

### Post by --Meteor on 2008-09-29
Hello everyone,I am a beginner with ubuntu and now I am using ubuntu 8.04. the problem how can I set password confirmation when leaving lock screen confuses me. If anyone know that ,please give me a hand! Thank you!:K:confused:

---

### Post by Rhubarb on 2008-09-29
> **--Meteor said:**
> Hello everyone,I am a beginner with ubuntu and now I am using ubuntu 8.04. the problem how can I set password confirmation when leaving lock screen confuses me. If anyone know that ,please give me a hand! Thank you!:K:confused:
I'm a bit confused myself with regards to your question.
I'll try anyway, after locking your screen, and you want to unlock it, simply type in your password, and press enter.  It's quite easy.

Locking your computer is a very good thing to do if you leave you computer alone for lunch break at work in an office job.

---

### Post by --Meteor on 2008-09-29
> **Rhubarb said:**
> I'm a bit confused myself with regards to your question.
I'll try anyway, after locking your screen, and you want to unlock it, simply type in your password, and press enter.  It's quite easy.

Locking your computer is a very good thing to do if you leave you computer alone for lunch break at work in an office job.

I am sorry for my confused words. I mean that, when I unlock it, it doesn't ask me for typing in my password. How can I make it have the password confirmation.Thank you for your help!

---

### Post by Rhubarb on 2008-09-29
I haven't come across this before, it's always just worked.
One thing you could try:

Press Alt + F2, type in: **gconf-editor**
Navigate to: apps --> gnome-power-manager --> lock

Then check to see if you get what I get there.
This might just work for you.

This thread might be of assistance too: [http://linux.derkeiler.com/Mailing-Lists/SuSE/2008-07/msg02024.html](http://linux.derkeiler.com/Mailing-Lists/SuSE/2008-07/msg02024.html)

---

### Post by binbash on 2008-09-29
You can do it via ubuntu-tweak

---

### Post by --Meteor on 2008-10-02
Thank you.I think there is still a long way for me to use ubuntu proficiently!

---

### Post by --Meteor on 2008-10-02
Now the problem is solved.The screen will not be locked for the root user!But I am root!Thank you!

---

### Post by Rhubarb on 2008-10-04
Good to know --Meteor :D
I'm not sure how exactly it came to be for you, but it's good that it's all fixed now ;)

---

### Post by ubuchignome on 2010-04-17
You want the screen to lock after a period of time of being idle? And you want to have to enter a password to unlock, is that what you are wanting to do. If so go to: System, preferences, screensaver and check the Lock screen when screen saver is active button. I hope this helps.

Have a good day!

---

