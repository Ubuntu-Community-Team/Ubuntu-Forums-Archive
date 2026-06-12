---
title: "ls produces unreadble cyan text on green background"
date: 2010-12-12
forum: Desktop Environments
---

### Post by JayKav on 2010-12-12
Ubuntu 10.10

I have an xp disk mounted. When I do an ls, the directory listing is unreadable because it displays light blue text on a green background. 

ls -l produces e.g.

drwxrwxrwx 1 root root  0 2009-05-17 22:55 Apps

I've tried experimenting with LS_COLORS but haven't found anything that works. E.g. I tried the suggestions in:

[http://ubuntuforums.org/showthread.php?t=821721](http://ubuntuforums.org/showthread.php?t=821721)

Is there a way to just disable colouring? White on black or green on black would do just fine.

Thanks,

Jay.

---

### Post by Rodney9 on 2010-12-12
I presume you are using Gnome terminal, if so look here for changing preferences - [http://library.gnome.org/users/gnome-terminal/stable/gnome-terminal-prefs.html.en](http://library.gnome.org/users/gnome-terminal/stable/gnome-terminal-prefs.html.en)

---

### Post by abc14jon on 2012-12-17
Here is a recipe:

To have readable blue (on white/black) directories on /host (a Windows file system) in ls from an Ubuntu terminal (gnome I believe) do:

issue the command:
 dircolors -p > ~/.dircolors
edit ~/.dircolors and change 30;42 to 01;34 and 34;42 also to 01;34
add the line:
  eval $(dircolors ~/.dircolors)
to ~/.bashrc

- Kristjan

---

### Post by overdrank on 2012-12-17
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

