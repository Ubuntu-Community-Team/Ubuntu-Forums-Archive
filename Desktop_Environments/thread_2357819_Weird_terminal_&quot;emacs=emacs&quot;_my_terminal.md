---
title: "Weird terminal &quot;emacs=emacs&quot; my terminal starts with this even in tty mode 16.04"
date: 2017-04-06
forum: Desktop Environments
---

### Post by rolando3 on 2017-04-06
Hi, can't figure out what can cause this today, today my terminal just start as displayed in below image, i have to press "ctrl + X" and then "ctrl + C" before i can use it
.[ATTACH=CONFIG]274458[/ATTACH]

I have reinstall gnome terminal but no luck, even reset terminal profile. this issue is just with my user account, because everything works fine with another use in the same machine.
both users are admins.

---

### Post by steeldriver on 2017-04-06
Probably something that's being started by your interactive shell - check the contents of your `~/.bashrc` file (assuming you are using the bash shell)

---

### Post by rolando3 on 2017-04-07
That was it. at the end of the file there was a additional line which says "emacs=emacs" (can't remember adding declaration like this).

Other one thing am not clear about, could not find the file in my current directory, had to use absolute route to be able to locate this, also "nano" text editor couldn't view or edit this file, was able to do this with "vim".
Want to know if there is limitation for system files with nano? which text editor is best for system administrators?. 

Thanks


> **steeldriver said:**
> Probably something that's being started by your interactive shell - check the contents of your `~/.bashrc` file (assuming you are using the bash shell)

---

