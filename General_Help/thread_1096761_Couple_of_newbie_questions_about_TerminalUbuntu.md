---
title: "Couple of newbie questions about Terminal/Ubuntu"
date: 2009-03-15
forum: General Help
---

### Post by -Gavin- on 2009-03-15
Hi there!

I'm seriosuly considering switching over to Ubuntu for my domestic computer needs and keeping Windows 7 for my Audio Production work.
I'm currently running a triple boot system at the moment, Win7/Win7/Ubuntu!

Anyway, i am trying to learn Linux properly by using Terminal wherever possible but i have two questions!


When i run a program from terminal, say Firefox...

It opens but i can't run any more terminal commands after that, i need to open a new tab... How can i go back to my gavin@gavin-laptop:~$ and enter in new commands without opening a new tab?


I also wonder, I'm hooking my father up with Linux on his new laptop (since all he uses it for is word processing, email and internet)...

I'm in Finland, he is in Scotland, We both have 1mb net connections so i presume VNC is out of the question.

Is there any way i can dial into his system and install all the packages like mp3 support, thunderbird and deal with his system updates remotely by commandline?



I have googled but can't find anything and thank you for your help! 

I really am getting into this system

---

### Post by .nedberg on 2009-03-15
Start programs with:

```

program &

```
to return to the terminal


Remote management? I use ssh! It just like the terminal. Have a look at openssh-server!

---

### Post by Dirjel on 2009-03-15
I just asked this question not too long ago.  Here are the responses I got!
> **The Cog said:**
> I think I know what you mean. In your terminal, press Ctrl-Z, which freezes the process and makes the command terminal active agan. Then enter the command **bg** which puts the frozen process into the background, just as though it had been launched with **&**. You can see what processes are running in the background with the command **jobs**. You can even make it so they don't get killed when the terminal closes by using the command **disown**, which is described in **man bash**.

> **SteveDee said:**
> You can suspend a job with <crtl>Z

To cancel a running job you need the job number by typing; jobs

You can then kill a specific job; kill %1  {assuming its job number 1}
Very helpful.  Also, someone recommended I download a program called "screen."  Apparently, it just lets you open new tabs in terminals, though, so I don't think that's what you want.

---

### Post by -Gavin- on 2009-03-15
Thank you guys very much!


So for remote management, i can access his sudo apt-get command if he gives me the password and run stuff like mp3 codecs etc so he can listen to his music?

---

### Post by white3454 on 2009-03-15
For SSH, you will need a user created on the remote box (your fathers user or create a new user for yourself) and make sure that user is in the admin user group or 'sudoers'

[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)


Here is the documentation for SSH: [https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

Good Luck!

---

