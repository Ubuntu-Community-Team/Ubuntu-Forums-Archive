---
title: "How to change root's font colors"
date: 2005-12-27
forum: General Help
---

### Post by ShirishAg75 on 2005-12-27
Hi all,
        I've been playing around with the .bashrc which is there both as normal user as well as root. This is the way the default entry is in .bashrc which I'm using :-

```
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"'
    ;;
*)
    ;;
esac
``` While looking for where the color schemes code are listed came to /usr/lib/X11/rgb.txt which lists the all the colors to the corresponding code while this in a different format. My main motive is  to change ```
PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"' 
```the prompt colors. How can I do this? Thanx in advance

---

### Post by amohanty on 2005-12-28
Are you using the gnome-terminal or xterm?
How-to for the bash prompt:
[http://www.tldp.org/HOWTO/Bash-Prompt-HOWTO/](http://www.tldp.org/HOWTO/Bash-Prompt-HOWTO/)

HTH
AM

---

### Post by ShirishAg75 on 2005-12-28
[quote=amohanty]Are you using the gnome-terminal or xterm?
How-to for the bash prompt:
[http://www.tldp.org/HOWTO/Bash-Prompt-HOWTO/]("http://www.tldp.org/HOWTO/Bash-Prompt-HOWTO/")

HTH
AM[/quote] using the gnome-terminal.  Also are the .bashrc for the root different from the .bashrc in the user

---

### Post by briancurtin on 2005-12-28
yes, root has a different .bashrc than a regular user. all users have their own .bashrc file

---

### Post by amohanty on 2005-12-28
I am not sure how the bashrc stuff works for gnome-terminal, however if you do a > xterm & you should see any coloring changes you make to bashrc.

root's bashrc is in /root

HTH

---

### Post by ShirishAg75 on 2005-12-28
Hi all,
        Uh oh!,
         I made a mess of things & didn't make a backup of the /root/.bashrc file. My mistake. Is there anyway I can get a clean file again. Here is the offending section :-

```

# set a fancy prompt (non-color, unless we know we "want" color)
#case "$TERM" in
#xterm-color)
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
    ;;
)
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
    ;;
esac

# Comment in the above and uncomment this below for a color prompt
*PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

# If this is an xterm set the title to user@host:dir
*case "$TERM" in
*xterm*|rxvt*)
*    PROMPT_COMMAND='echo -ne "[\031]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"'
*    ;;
*)
*    ;;
*esac

``` 
Something has changed as the prompt is mis-behaving. As far as I can see there are 2 different prompt profiles given or way the prompt will show. The first will not use any colors while the second will use colors. I was using the 2nd profile which is commented the only problem is/was the user also has escape code 33 which is color green for username@hostname. Hence atleast to my untrained eye just changed the color code from 33 to 32 but it seems I deleted something else or something else needs to be changed elsewhere as the prompt came up twice.This is annonying hence commented the whole 2nd profile & just uncommented the 1st profile again. Now the prompt comes right but gives an error of line 27 which has ;; in it. Strange.My only concern is to get let's say 
```
root@shirishag75
``` :- root here being the user & shirishag75 being the host name, this whole path in red while the rest of the present working directory in Blue. which it is showing. Thanx in advance.

---

### Post by amohanty on 2005-12-28
> #**case **"$TERM" in
#xterm-color)
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
    ;;
)
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
    ;;
**esac**

If there is esac (in bold above) it expects a case (also in bold) - which you have commented out alongwith the ***** in the second case term. I would suggest that you read the programming guide or at least the bash prompt guide on tldp.org, it will come quite handy later on if you plan to proceed down this path.

Change the above to:

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
xterm-color)
 PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
    ;;
*)
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
    ;;
esac

Also keep in mind that *** (star character)** is **not** the comment character. To comment a line you need to prepend the line with a **#** So the second section that you think you have commented is also wrong. Replace the * with # for comments.

Again, before messing with root's file:
1. try it on a non-super user so that you can recover from mistakes.
2. read the manual

HTH
AM

---

### Post by d11wtq on 2005-12-28
> **shirishag75]Hi all,
        Uh oh!,
         I made a mess of things & didn't make a backup of the /root/.bashrc file. My mistake. Is there anyway I can get a clean file again. Here is the offending section :-

```

# set a fancy prompt (non-color, unless we know we "want" color)
#case "$TERM" in
#xterm-color)
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01 said:**
> \u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
    ;;
)
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
    ;;
esac

# Comment in the above and uncomment this below for a color prompt
*PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

# If this is an xterm set the title to user@host:dir
*case "$TERM" in
*xterm*|rxvt*)
*    PROMPT_COMMAND='echo -ne "[\031]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"'
*    ;;
*)
*    ;;
*esac

``` 
Something has changed as the prompt is mis-behaving. As far as I can see there are 2 different prompt profiles given or way the prompt will show. The first will not use any colors while the second will use colors. I was using the 2nd profile which is commented the only problem is/was the user also has escape code 33 which is color green for username@hostname. Hence atleast to my untrained eye just changed the color code from 33 to 32 but it seems I deleted something else or something else needs to be changed elsewhere as the prompt came up twice.This is annonying hence commented the whole 2nd profile & just uncommented the 1st profile again. Now the prompt comes right but gives an error of line 27 which has ;; in it. Strange.My only concern is to get let's say 
```
root@shirishag75
``` :- root here being the user & shirishag75 being the host name, this whole path in red while the rest of the present working directory in Blue. which it is showing. Thanx in advance.

Just for note:  There should be a fresh copy in /etc/skel/ :)

/etc/skel is where you put anything you want all new user accounts to have by default (e.g. a public_html directory)

---

### Post by ShirishAg75 on 2005-12-28
Thanx amonthy, that is a good one but needs to be cleaned up further. I tried reading it atleast the first few sections no. of times but wasn't successful. Would e-mail for sure, as atleast for noObs it isn't helpful at all. Wish he would break down the sections a little bit more.

---

### Post by ShirishAg75 on 2005-12-29
Hi all,
       Thanx to all. Was finally able to fix up the issue. Thanx to amohanty as well as d11wtq for helping out. Although was not able to make much sense of the Bash-prompt but there were some good suggestions.

---

### Post by nihilocrat on 2005-12-29
If you want to do it for just the prompt, I did something exactly like this. I took a user's .bashrc and changed the prompt so their username@hostname appears in green. I then copied this .bashrc to /etc/skel/ so it will also apply for future users.

I did the same thing for root, but the prompt's color is red. Here's the important part of my root .bashrc:

```

# Comment in the above and uncomment this below for a color prompt
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;31m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

```

I changed the color at \[\033[01;31m\] right before \u@\h. The '31m' is the part that makes it red, but I don't have a complete understanding of which number equates to which color. As you can see, putting this same string at other places in the line will make it so that text after that string will display in the color specified. Using this will make all the text you type in AFTER your prompt show up as red:

```

# Comment in the above and uncomment this below for a color prompt
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;31m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ \[\033[01;31m\]'

```

As far as I can tell, these settings shouldn't differ from terminal program to terminal program. I am usually remotely logged into my box, so I usually work with the vanilla shell.

---

### Post by ShirishAg75 on 2005-12-29
> **nihilocrat]If you want to do it for just the prompt, I did something exactly like this. I took a user's .bashrc and changed the prompt so their username@hostname appears in green. I then copied this .bashrc to /etc/skel/ so it will also apply for future users.[/quote]
Not a bad idea, might do the same. 


[quote=nihilocrat]
I changed the color at \[\033[01 said:**
>  right before \u@\h. The '31m' is the part that makes it red, but I don't have a complete understanding of which number equates to which color. As you can see, putting this same string at other places in the line will make it so that text after that string will display in the color specified. Using this will make all the text you type in AFTER your prompt show up as red  [/snip]
For knowing what colors are equated to what escape codes do the ```
dircolors -p
``` You'll get the escape codes around 1/3 of the output.

---

