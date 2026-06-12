---
title: "Keeping the gnome-terminal session active"
date: 2009-07-18
forum: Desktop Environments
---

### Post by shemhamforash on 2009-07-18
Heya all,

I've added a new item to the main gnome menu. I choose for the type "Application in Terminal", and as command let's say running the command "nmap".

What I want to achieve is that when i click on the link, a new instance of gnome-terminal opens, and "nmap" is executed. Just with no arguments yet, so that I get to see all the available options. I have ~100 programs that I want to add to this menu, all just running with the "--help" parameter or the like, and opening the gnome-terminal in the right working directory. Just like in backtrack for example.

The problem:

The new instance of gnome-terminal does open successfully, but closes immediately. I can set the option in gnome-terminal to keep the terminal open after a program exits, but then I'm stuck with a inactive terminal (program exited, and the prompt doesn't return). Is there an option to keep the gnome-terminal session active?

I looked for answers for a long time, and posting here is the last thing there's left for me..

---

### Post by wojox on 2009-07-18
In the terminal create a new profile and in the Title and Command Tab Under command click Run a custom command  and enter nmap.

---

### Post by shemhamforash on 2009-07-18
This means that I have to make a new profile in gnome-terminal for each of the ~100 programs I want to add to my menu?

---

### Post by wojox on 2009-07-18
Yes, that is why I couldn't understand why you just wouldn't open a terminal and type you're app in to start it.

---

### Post by shemhamforash on 2009-07-18
Because I have a lot of perl/python/ruby scripts residing in a specific directories.. Have you ever worked with backtrack? It has the same functionality.

---

### Post by shemhamforash on 2009-07-25
So there's really no alternative for this? That's kinda disappointing..

---

### Post by DaithiF on 2009-07-27
This is linux, theres always a way!  :)

slightly convoluted but:
1. add this to the bottom of your .bashrc file:
if [[ -f ~/.bash-oneoff ]]; then
    source ~/.bash-oneoff
fi

2. create a script called wrapper.sh:
echo "$*" > ~/.bash-oneoff
gnome-terminal
sleep 2
rm ~/.bash-oneoff

3. When creating your menu items, your command would be:
/path/to/wrapper.sh nmap --help

Note: the sleep command in 2 is to make sure that gnome-terminal has had enough time to start, launch bash, and for bash to do its initialisation stuff before we delete the .bash-oneoff file.

hope this helps

---

