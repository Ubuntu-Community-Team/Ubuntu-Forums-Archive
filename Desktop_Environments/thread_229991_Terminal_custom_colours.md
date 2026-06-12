---
title: "Terminal custom colours"
date: 2006-08-05
forum: Desktop Environments
---

### Post by evergreen on 2006-08-05
Hi I have just come back to Ubuntu (Gnome) after a play about on Mepis(KDE) and have noticed something with the text colour of the Terminal or Konsole in KDE which I find very useful. I will do my best to explain. 

in Terminal under Gnome it's like this just one colour

[COLOR="Red"]merkelt@home:~$text colour example[/COLOR]

In Konsole when you open it will look something like this

[COLOR="Red"]merkelt@home:~$[/COLOR] [COLOR="Lime"]text colour example[/COLOR]


Is there a way to change Terminal to behave like this. I find having  two colours helps me find my way around the Terminal and stops me getting lost in text;)  Hope this makes sense to someone thanks.

ps... I tryed installing Konsole thinking that it would just give me this behaver but it didn't any ideas would be great.

---

### Post by moma on 2006-08-05
1) This is how to change the appearance (form and color) of bash prompt $.
[http://www.tldp.org/HOWTO/Bash-Prompt-HOWTO/x329.html]("http://www.tldp.org/HOWTO/Bash-Prompt-HOWTO/x329.html")

Edit your $HOME/.bashrc and put the line there.
PS1="\[\033[1;34m\][\$(date +%H%M)][\u@\h:\w]$\[\033[0m\] "

2) And change the textcolor of a terminal window.

echo -e "\033[01;37m" - this is white
echo -e "\033[01;36m" - this is light cyan
echo -e "\033[01;35m" - this is light magenta
echo -e "\033[01;34m" - this is light blue
echo -e "\033[01;33m" - this is yellow
echo -e "\033[01;32m" - this is light green
echo -e "\033[01;31m" - this is light red
echo -e "\033[01;30m" - this is dark gray

echo -e "\033[22;37m" - this is gray
echo -e "\033[22;36m" - this is cyan
echo -e "\033[22;35m" - this is magenta
echo -e "\033[22;34m" - this is blue
echo -e "\033[22;33m" - this is brown
echo -e "\033[22;32m" - this is green
echo -e "\033[22;31m" - this is red
echo -e "\033[22;30m" - this is black

3)  Check also gnome-terminal's menu selection Edit -> Current Profile....  
And choose [Colors] tab-page.

---

### Post by evergreen on 2006-08-05
wow thanks for the fast reply moma I have to go out now. I will try what you have suggested when I get back home and let you know how I get on. Thanks mate :D

---

### Post by moma on 2006-08-05
Be back $HOME at 9 o'clock boy !

(just kiddin')

---

### Post by evergreen on 2006-08-05
> **moma said:**
> 1) This is how to change the appearance (form and color) of bash prompt $.
[http://www.tldp.org/HOWTO/Bash-Prompt-HOWTO/x329.html]("http://www.tldp.org/HOWTO/Bash-Prompt-HOWTO/x329.html")

Edit your $HOME/.bashrc and put the line there.
PS1="\[\033[1;34m\][\$(date +%H%M)][\u@\h:\w]$\[\033[0m\] "

2) And change the textcolor of a terminal window.

echo -e "\033[01;37m" - this is white
echo -e "\033[01;36m" - this is light cyan
echo -e "\033[01;35m" - this is light magenta
echo -e "\033[01;34m" - this is light blue
echo -e "\033[01;33m" - this is yellow
echo -e "\033[01;32m" - this is light green
echo -e "\033[01;31m" - this is light red
echo -e "\033[01;30m" - this is dark gray

echo -e "\033[22;37m" - this is gray
echo -e "\033[22;36m" - this is cyan
echo -e "\033[22;35m" - this is magenta
echo -e "\033[22;34m" - this is blue
echo -e "\033[22;33m" - this is brown
echo -e "\033[22;32m" - this is green
echo -e "\033[22;31m" - this is red
echo -e "\033[22;30m" - this is black

3)  Check also gnome-terminal's menu selection Edit -> Current Profile....  
And choose [Colors] tab-page.

Well moma what can I say This is perfect! Just tryed out what you surgested and It works great :cool: 

now I can get back to learning the shell thanks again.

---

### Post by evergreen on 2006-08-05
> **moma said:**
> Be back $HOME at 9 o'clock boy !

(just kiddin')

lol, just had to go to the shops for some milk. Coffee need my coffee

---

### Post by pavel_kbc on 2006-12-25
moma, how do i make color like gentoo. everywhere . apt-get update , install , upgrede . find etc.

---

### Post by revertex on 2006-12-29
> **pavel_kbc said:**
> moma, how do i make color like gentoo. everywhere . apt-get update , install , upgrede . find etc.

edit your /etc/bash.bashrc, coment this line 

```
#PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
```

and add something like this after:

```
##########################################################
##  colored prompt 
##########################################################

if ${use_color} ; then
    if [[ ${EUID} == 0 ]] ; then
        PS1='\[\e[1;32m\][\[\e[1;33m\]\d\[\e[1;32m\], \[\e[1;33m\]\t\[\e[1;32m\]] \n\[\e[1;34m\][\[\e[1;31m\]\h\[\e[1;34m\]] \n\[\e[1;33m\][\[\e[1;32m\]\w\[\e[1;33m\]] \[\e[1;31m\]->> \[\e[1;32m\]\$ \[\e[0m\]'
    else
        PS1='\[\e[1;32m\][\[\e[1;33m\]\d\[\e[1;32m\], \[\e[1;33m\]\t\[\e[1;32m\]] \n\[\e[1;32m\](\[\e[1;37m\]\u\[\e[1;33m\]@\[\e[1;37m\]\h\[\e[1;32m\]) \n\[\e[1;33m\][\[\e[1;32m\]\w\[\e[1;33m\]] \[\e[1;34m\]->> \[\e[1;32m\]\$ \[\e[0m\]'
    fi
    alias ls='ls --color=auto'
else
    if [[ ${EUID} == 0 ]] ; then
        # show root@ when we don't have colors
        PS1='\u@\h \W \$ '
    else
        PS1='\u@\h \w \$ '
    fi
fi
#########################################################
```

this is from my old gentoo /etc folder, edit PS1 to your taste.

it seems there is a bug in Edgy, it don't source /etc/profile, a dirty workaround is add this line to your ~/.bashrc and /root/.bashrc

```
source /etc/profile
```

---

### Post by pavel_kbc on 2006-12-30
coooooool . thanks dude

---

### Post by haricharan on 2007-03-20
that certainly was helpful...thanks moma..:)

---

### Post by ssaamon on 2007-10-22
thats awesome!

does anyone know how to restore the restore the previous font settings after changing them, without exiting the terminal?

thanks :)

---

### Post by syxbit on 2007-12-31
you can type
source ~/.bashrc
that works

is there a way to make the background of the terminal black and the text white with a line in your .bashrc

i know you can edit the profile, but since i backup my .bashrc, and restore it often, it would automate it

---

