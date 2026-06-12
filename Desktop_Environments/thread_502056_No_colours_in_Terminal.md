---
title: "No colours in Terminal"
date: 2007-07-16
forum: Desktop Environments
---

### Post by cub on 2007-07-16
Somewhere along the way my terminal lost it's ability to use colours for directories, different kind of files etc. I have re-set everything to standard Human theme, played around with the colour settings for Terminal but I can't get it back.

All I can do is change the colour of the font and the background.

I run Feisty and Gnome. Any ideas?

---

### Post by gvoima on 2007-07-16
What do you mean lost? Have you ever had colours in terminal with your current install?

If not, then add --color=auto to your /home/user/.bashrc file in the alias section to the ls command.
e.g.
```
alias ls='ls -hl --color=auto'
```

---

### Post by cub on 2007-07-16
Yes, there was colours after I first had installed. I don't really know when it disappeared or what I might have done to cause it.

I didn't have a .bashrc file in my home directory. There is one in the /root directory (which has the alias line above in it). I only had a .bash_history-file in my home directory. So I copied the one in the root directory, chown and chmod it and voila, the colours are back.

---

