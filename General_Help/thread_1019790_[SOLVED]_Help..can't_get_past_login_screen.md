---
title: "[SOLVED] Help..can't get past login screen"
date: 2008-12-23
forum: General Help
---

### Post by kallum on 2008-12-23
Hi, I installed ubuntu for the first time and it got past installing fine, I got to the login screen enter my username and password press enter and all I can see is my mouse and the orange/browny coloured screen. What shall I do? I installed this over vista and now I can't go on my pc...it won't let me format it either so I'm kind of stuck. Can anyone help please?

---

### Post by redilyn on 2008-12-23
Thats strange, does the startup sound play??

Maybe you just need to wait longer for the dekstop to load.

If not you could try updating ubuntu and then restarting although I don't know if it will fix your problem.

This is going to involve the terminal. If you do not feel comfortable using a terminal please wait for someone else to reply.

Press CTRL+ALT+F2

This will drop you to a terminal.

Enter your username and press enter

Enter your password and press enter

Type the following 

```

sudo apt-get update

```

Then


```

sudo apt-get upgrade

```

Answer "Yes" if prompted, wait for it to finish then


```

sudo shutdown -r 0

```

Your system will reboot.

Hopefully you will be able to login this time.

---

### Post by kallum on 2008-12-23
I don't know if there is any sound because my speakers arnt working at the moment, I've never used terminal and don't know what it is/does but I'll give it a try..when do I try update?

---

### Post by redilyn on 2008-12-23
Hey,

No problem, the terminal isn't hard to use, just pay close attention to the commands.

If you have a printer, maybe print out everything from my last post after "Press CTRL+ALT+F2" and then just run each command in order.

The update accutally occurs here:

```

sudo apt-get update

```
Updates the list of available software

```

sudo apt-get upgrade

```
Upgrades installed packages

"I've never used terminal and don't know what it is/does"

Terminal is a command line interface - I don't really know how to explain it so I'll just post a passage from the docs

```

The traditional Unix environment is a CLI (command line interface), 
where you type commands to tell the computer what to do. 
That is faster and more powerful, but requires finding out what the commands are.

```

---

### Post by kallum on 2008-12-23
Sorry but I've never does this before, when do I press ctrl alt f2 ? I just reinstalled ubuntu and it got past the orange screen and now gone to all black! :confused:                          edit: I just pressed ctrl alt f2 and entered what you said, I think I am downloading an update, isit a black screen with loads of writing on?

---

### Post by kallum on 2008-12-23
Just finished the update and it's fixed!! Thankyou for helping me!:popcorn:

---

### Post by redilyn on 2008-12-23
Your welcome, sorry I didn't reply earlier I had to run for a bit. 

Glad to hear you got it all figured out.

Happy Holidays :)

P.S. Don't forget to mark this thread as solved - Its under forum tools at the top.

---

