---
title: "Really annoyed with installing games without using the add/remove tool in ubuntu!"
date: 2007-04-25
forum: Gaming &amp; Leisure
---

### Post by shtewe on 2007-04-25
Ubuntu is great and free but the only thing that annoys me is installing programs and games.  Why don't they make all the programs you can get and games (only the popular ones and good ones) in the add/remove thingy?  That program is very nifty and sooo simple to install stuff but installing stuff that is not in the add/remove thingy it is quite annoying with all these different file types like .run, .deb and others.  Why not make it easy for the population?  Also running the terminal to install games is a pretty old fashioned way which ubuntu should try and get away from but it is good if you have a problem.

---

### Post by Perfect Storm on 2007-04-25
It takes time to learn something new ;)

> Why not make it easy for the population? 

diffrent reasons, it needed to be tested through and accepted before it can access the the official repo. Another thing is the license issue.

---

### Post by shtewe on 2007-04-25
Ok thanks for that reply i didn't know that but what happens if the game is free, does it go into the offical repo? or does it need to be open source?

---

### Post by eentonig on 2007-04-25
> **shtewe said:**
> Ok thanks for that reply i didn't know that but what happens if the game is free, does it go into the offical repo? or does it need to be open source?

99.9% (and definitely for games) it will have to be open source. So people can maintain it in case of bugs or errors.

---

### Post by tommcd on 2007-04-25
Many games can simply be downloaded and run from your home folder. I run Nexuiz, Action Cube, Alien Arena, and Sauerbraten that way. For sauerbraten, there is 1 dependency you need. It is libsdl...whatever. When you run it from the CLI, it will tell you the dependency that is needed. Just search in synaptic and install it. Easy.
This way you can download a new version of the game as soon as it's available, without waiting for it to show up in the ubuntu repos. Also, if you need to reinstall ubuntu, the game is still there in /home. No need to reinstall it.

---

### Post by shtewe on 2007-04-25
how do u just put games in there home folder?  doesn't all games come with an installer like .run and stuff?

---

### Post by bastiegast on 2007-04-25
I've said it before, but ive occasionally found it easier to download the windows build of a game and run it through wine by just double clicking on the exe than ectracting some archive and hope it runs and I don't have to install any depencies.

---

### Post by Perfect Storm on 2007-04-25
So why not use windows if you do it that way?


Also if the games/applications use share libary (dynamic binaries), these games/applications uses less horsepower to run.


> **shtewe said:**
> how do u just put games in there home folder?  doesn't all games come with an installer like .run and stuff?

Well usually .run/.sh files gives you the option(s) where to install it. What tommcd mean is that if you have seperated /home from the rest of your partitions you can re/install Ubuntu/Linux without affecting /home.

---

### Post by bastiegast on 2007-04-25
> **Artificial Intelligence said:**
> So why not use windows if you do it that way?


Also if the games/applications use share libary (dynamic binaries), these games/applications uses less horsepower to run.




Well usually .run/.sh files gives you the option(s) where to install it. What tommcd mean is that if you have seperated /home from the rest of your partitions you can re/install Ubuntu/Linux without affecting /home.

Why not use windows? I think you can answer that question yourself. I just do that stuff sometimes because I'm lazy, of course I know how to use a terminal en install depencies. And if the game requires all performance I can squeeze out of my computer I wouldn't use wine of course. But still I think it's "funny" how sometimes it is easier to run the windows version of a game in linux than running the native linux version.

---

### Post by tommcd on 2007-04-26
> **shtewe said:**
> how do u just put games in there home folder?  doesn't all games come with an installer like .run and stuff?

It depends on the game. For Nexuiz, just download, extract to a folder, cd into that folder, and run ./nexuiz-linux-sdl.sh, or possibly ./nexuiz-linux-glx.sh. See which one works best for you (for me it's nexuiz-linux-sdl.sh). You can create a launcher for it on your desktop.
For Sauerbraten, extract it to a folder, cd into that folder, then "sudo chmod +x sauerbraten_unix". Then run ./sauerbraten_unix. You will need 1 dependency from synaptic, libsdl....something. It will tell you the name of it when you run it. You will need to check the documentation for each game you want. 
True, some games need to compiled from source code, or installed from a .deb, or something. But many games come ready to run.

---

### Post by ZeroPain on 2007-04-26
>  shtewe  	Ubuntu is great and free but the only thing that annoys me is installing programs and games. Why don't they make all the programs you can get and games (only the popular ones and good ones) in the add/remove thingy? That program is very nifty and sooo simple to install stuff but installing stuff that is not in the add/remove thingy it is quite annoying with all these different file types like .run, .deb and others. Why not make it easy for the population? Also running the terminal to install games is a pretty old fashioned way which ubuntu should try and get away from but it is good if you have a problem.

I kind of like having to figure out how to run things, it helps you learn how to be sufficient.

---

### Post by tommcd on 2007-04-27
Yeah, me too. Personally, I never have used the add/remove programs thing, except just recently to install multimedia codecs as per the new fiesty way:
[http://ubuntuforums.org/showthread.php?t=413626](http://ubuntuforums.org/showthread.php?t=413626)
I use synaptic or command line. 
Learning the command line definitely pays off. It is a huge help if you want to try other distros, or learn to solve problems. It is not that hard once you get used to using it, and it is often faster too.

---

