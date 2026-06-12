---
title: "Adding to PATH"
date: 2006-02-04
forum: Desktop Environments
---

### Post by benmoreassynt on 2006-02-04
Hi,

I am trying to alter my path.

At the moment echo $PATH results in 

/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games

I want to add:
/opt/lampp/usr
to $PATH

As far as I can see, all I should need to do is edit the file /etc/profile, changing the line
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
to read 
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games:/opt/lampp/bin"

However, when I do this, after logging out or a complete reboot, /opt/lampp/usr is still not added to the path.

I am at a loss to see what I am doing wrong.

Thanks
Ben

---

### Post by taurus on 2006-02-04
Try this then

pico ~/.bashrc

Then add these two lines to it

PATH=$PATH:/opt/lampp/usr
export PATH

After you've saved it, run this at the prompt,

source ~/.bashrc

---

### Post by benmoreassynt on 2006-02-05
Thanks. Much appreciated

ben

---

### Post by bernardfrancois on 2006-03-01
Can anyone explain this behaviour? Normally it should be possible to use /etc/profile. This is what **man bash** says:

```

FILES
       /bin/bash
              The bash executable
       /etc/profile
              The systemwide initialization file, executed for login shells
       /etc/bash.bashrc
              The systemwide per-interactive-shell startup file
       /etc/bash_logout
              The  systemwide  login shell cleanup file, executed when a login
              shell exits
       ~/.bash_profile
              The personal initialization file, executed for login shells
       ~/.bashrc
              The individual per-interactive-shell startup file
       ~/.bash_logout
              The individual login shell cleanup file, executed when  a  login
              shell exits
       ~/.inputrc
              Individual readline initialization file

```

Somewhere else in the forums I read that /etc/profile doesn't work when using gnome... (probably the PATH variable gets overridden by gnome I guess?)...

---

### Post by engla on 2006-03-01
I saw that for dapper they completed a spec called "One true $PATH". They realized that there were lots of different ways to set the path in Breezy, all for different environments (gnome, bash, zsh etc). 

So for dapper I think they cleaned this up and it's going to be more correctly done there.

---

### Post by cwaldbieser on 2006-03-01
[QUOTE=bernardfrancois]Can anyone explain this behaviour? Normally it should be possible to use /etc/profile. This is what **man bash** says:

```

FILES
       /bin/bash
              The bash executable
       /etc/profile
              The systemwide initialization file, executed for login shells
       /etc/bash.bashrc
              The systemwide per-interactive-shell startup file
       /etc/bash_logout
              The  systemwide  login shell cleanup file, executed when a login
              shell exits
       ~/.bash_profile
              The personal initialization file, executed for login shells
       ~/.bashrc
              The individual per-interactive-shell startup file
       ~/.bash_logout
              The individual login shell cleanup file, executed when  a  login
              shell exits
       ~/.inputrc
              Individual readline initialization file

```

Somewhere else in the forums I read that /etc/profile doesn't work when using gnome... (probably the PATH variable gets overridden by gnome I guess?)...[/QUOTE]

/etc/profile only works for a login shell.  That is usually a shell you log into from the console.  A shell you open in gnome-terminal, konsole, eterm, etc. is typically not a login shell.

---

### Post by bernardfrancois on 2006-03-02
When you start your computer, Ubuntu will log you in automatically and start X. At that moment, /etc/profile should be executed (at least, thats how I *think* it works). All other shells started later on are sub-processes of that login shell and inherit the environement.

---

### Post by thegnu on 2007-10-09
> **bernardfrancois said:**
> When you start your computer, Ubuntu will log you in automatically and start X. At that moment, /etc/profile should be executed (at least, thats how I *think* it works). All other shells started later on are sub-processes of that login shell and inherit the environement.
This is not how I understand it at all.  GDM starts as a system daemon, as does everything in /etc/init.d

I could be wrong, though.

---

