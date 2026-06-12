---
title: "issue with a script on terminal"
date: 2009-05-16
forum: General Help
---

### Post by Intrepid Ibex on 2009-05-16
Hi,

I got tired of always typing manually: 

```
sudo apt-g(tab) au(tab)r(tab) && sudo apti(tab) au(tab)
```


So I decided to create this script:

```
sudo apt-get autoremove && sudo aptitude autoclean
```


The problem is that when I run that on terminal, the script just completes and the terminal shuts down as soon as the script has been completed. Therefore I don't get to see what the commands removed :/.

So is there a command to stop this from happening or something?

Also what is the difference with that and a bash script with those commands?

Thanks for all ):P

---

### Post by mb_webguy on 2009-05-17
Last things first...
> **Intrepid Ibex said:**
> Also what is the difference with that and a bash script with those commands?

I'm not sure what you're asking here... You said earlier in the post that you wrote a script, and here you're asking what the difference is between this (a script) and that (a script).

If you're running this from the terminal, you don't really need to make a script -- you can make an alias instead.  You can make an alias for the current session using something like the following command.```
alias aptoff='sudo apt-get autoremove && sudo aptitude autoclean'
```You can replace "aptoff" with whatever you want to call the alias.  Now, whenever you type "aptoff" (or whatever you named the alias), it will run those commands.

If you want the alias to be persistent, you'll need to add it to your .bashrc file.  Open the file with "nano ~/.bashrc", and add the previous command to the end of the file.

If you want to have a launcher that will open a terminal and run these commands and also remain open afterwards so you can see the output, you would use the following command in the launcher.```
gnome-terminal -x bash -c "sudo apt-get autoremove && sudo aptitude autoclean;read -n1"
```The "read -n1" part means the bash shell will wait for you to hit a key before closing.  You can use the mouse to scroll through the output, and when you're done you can press any key to close the window.

---

### Post by Intrepid Ibex on 2009-05-17
Well I was just wondering what the:```
#! /bin/bash
```on the beginning of scripts mean :/.

But thanks for your help.

---

### Post by Cheesemill on 2009-05-17
The #! is called a Shebang.

Check here for more info:
[http://en.wikipedia.org/wiki/Shebang_(Unix](http://en.wikipedia.org/wiki/Shebang_(Unix))

Cheesemill

---

