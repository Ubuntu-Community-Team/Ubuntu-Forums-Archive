---
title: "Xfce Terminal starting directory is one-up"
date: 2007-04-23
forum: Desktop Environments
---

### Post by samopal on 2007-04-23
hi community, :KS  

I wonder if it feature, or bug, but probably it is not wanted behavior at least. 
I like xfce Terminal, its easy and pretty well customizable. But 1 thing is negative - it always starts not in directory where it was launched, but one-up!! 

example> in thunar, i'm in folder /etc/rc.local, i right-click into window in this folder, choose open terminal here and terminal starts in /etc 

if i try to run Terminal without specifiyng starting directory, it will start in /home, but it should start /home/myName, as far as I know

---

### Post by mojoman on 2007-04-23
It had a look how my xfce terminal behaves and the terminal opens in the right folder, i.e. it behaves different from yours but I have no idea why. So, it doesn't seem like a bug.

/mojoman

---

### Post by samopal on 2007-04-29
it seems that this behavior is in more applications - for example when i open standard tty on "alt + ctrl + F3", and sign in to my account, i'm not in my account's home, but only in /home/ 

i tried to run xterm too, but there is this same problem...

---

### Post by Ptero-4 on 2007-04-29
Looks like preferences breakage. Try tossing your ~/.bashrc and ~/.login files.

---

### Post by samopal on 2007-04-30
> **Ptero-4 said:**
> Looks like preferences breakage. Try tossing your ~/.bashrc and ~/.login files.
but i don't have .login file... don't know where to find it. 
~/$ find . | grep login 
returns nothing, i'm using xubuntu, is it something for gnome/kde env.?

---

### Post by samopal on 2007-05-01
[COLOR="Red"][SIZE="3"]SOLVED> [/SIZE][/COLOR]

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ]; then 
    . /etc/bash_completion 
fi

this was problem, i commented it all and my bash shell works like a charm :KS  
thx, for hints -> i'm making a note to my diary: "don't be lazy and wait for others answers and try a little bit harder to solve it yourself!!"

---

