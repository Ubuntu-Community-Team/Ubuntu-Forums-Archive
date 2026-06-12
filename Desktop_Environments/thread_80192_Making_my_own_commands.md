---
title: "Making my own commands?"
date: 2005-10-21
forum: Desktop Environments
---

### Post by arcanistherogue on 2005-10-21
Is it possible to make your own commands for the command line that save time?  For instance, lets say I have a windows game I play through cedega in ~/TransGaming_Drive/Path/to/file/which/is/long/game.exe, can I make it so I can just type "gamename" and it executes the command "cedega /home/john/..../game.exe"?  

Thanks :D

---

### Post by Kyral on 2005-10-21
Very possible and very useful. First open .bashrc and uncomment the block below "Define your own aliases here". Save it

Now open .bash_aliases (You may have to create it).

The syntax is best shown with an example

```

alias cp='cp -i'
alias ln='ln -s'
alias mv='mv -i'
alias rm='rm -i'
alias ..='cd ..'
alias ...='cd ...'
alias cd..='cd ..'
alias cd-='cd -'
alias ls='ls -hF --color=auto'
alias df="df -h"
alias h=history
alias untgz="tar -xvfz"
alias untbz2="tar -xvfj"
alias aptsource='sudo gedit /etc/apt/sources.list'
alias aptUI='sudo apt-get update && sudo apt-get dist-upgrade'
alias aptI='sudo apt-get install'
alias aptR='sudo apt-get remove'
alias aptS='apt-cache search'
alias aptSh='apt-cache show'
alias debI='sudo dpkg -i'
alias sourcebuild='sudo apt-get source -b'
alias depbuild='sudo apt-get build-dep'

```

---

### Post by arcanistherogue on 2005-10-21
wow, that is awesome.  I love how easy it is and how much it is encouraged to customize and tweak linux to your own settings.  

Thanks for the help :D

---

### Post by ubuntumaneh on 2005-10-21
Just an educational tip, since you got very happy with the solution given and your question is very good indeed. A general answer would be "this is what scripting is almost all about". If you spend some time learning a little of bash, python and alikes you are going to see what is simplicity in service of power :)). Look at google things like how to change your bash prompt and so on.

   Have fun

---

### Post by aysiu on 2005-10-21
I make keyboard shortcuts for commands I use often. 
Go to the Configration Editor (I think it's in System Tools). 
Then go to Apps > Metacity. 
There should be two directories there: global keybindings and keybinding commands. 
Define the command in keybinding commands (for example, for command_1 you might call it *cedega /home/john/..../doom.exe*). 
Define the keyboard shortcut in global keybindings (for example, for command_1 you might call it *<Control><Shift>d*).

Then, if you want to play Doom, you just press Control-Shift-D, and it'll start up.

---

### Post by dbott67 on 2005-10-21
[quote=Kyral]Very possible and very useful. First open .bashrc and uncomment the block below "Define your own aliases here". Save it

Now open .bash_aliases (You may have to create it).[/quote]

This is awesome!  Thanks for sharing! :)

-Dave

---

### Post by migueljacq on 2005-10-21
I discovered this when wanting to make dialing my modem easier from the command line. 'web-on' in my .bashrc calls my modem script :-) 'web-off' kills it.
I also mount drives such as the floppy disk 'Aon' and 'Aoff'
Very useful.

---

