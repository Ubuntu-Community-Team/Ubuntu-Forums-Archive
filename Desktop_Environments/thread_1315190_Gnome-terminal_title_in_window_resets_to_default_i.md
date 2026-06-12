---
title: "Gnome-terminal title in window resets to default in window-list-panel"
date: 2009-11-05
forum: Desktop Environments
---

### Post by frederik.heremans on 2009-11-05
Since I upgraded to 9.10 (3 days ago), there is a problem with my gnome-terminal. I've searched google for other people experiencing this issue, but haven't found any relevant matches yet...

The problem:

- I open 2 gnome-terminals, one for running Maven an another tailing my JBoss-log.
- I set the title of each terminal to keep them apart (using Alt + T, S)
- Titles show up in the window-list as they should.
- When I run a command in the terminal, the title in the window-list-panel resets to the default but the title on the gnome-terminal window itself remains unchanged


Running 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux + The GNOME Panel 2.28.0

---

### Post by frederik.heremans on 2009-11-05
Can someone running 9.10 try setting gnome-terminal title and run any command in it, and watch the window-list-panel?

thanks ;)

---

### Post by chrisgnow on 2009-11-30
I have also experienced the very same problem.  If you find a solution outside this forum I would appreciate it if you would post the answer here.

---

### Post by emil0r on 2010-01-06
A sort of (ish) solution:
Commenting out the following in your .bashrc file in your home directory:

> case "$TERM" in
xterm*|rxvt*)
    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}:${PWD/$HOME~}\007"'
;;                                                                         
*)    
;;                                                                         
esac


removes the part where it helpfully sets where you currently are at. This also means it doesn't remove your own title you set in order to see what the hell you're doing with 10+ different terminals up at once.

Not sure if it's this that's responsible for the change or if it's something else.

---

### Post by &amp;)ky#)^ on 2010-02-08
I, too, am suffering from this problem.  I don't mind it so much on terminals themselves, but it causes quite an annoyance in gedit.  I'm using the embedded terminal plugin from the gedit-plugins package which essentially runs a gnome-terminal inside of gedit.  This window pane bug in gnome-terminal/bashrc causes the title of the gedit window to change to "username@machine: ~" in the window list.  That's not so good if you want to look at the window list to see what text file you have open. :(

---

### Post by cjminton on 2010-02-10
I've been searching for like an hour on how to make it to where when I run a program in the terminal it just uses that for the title.

So like when I run *mutt* from a terminal the title of it changes to mutt. Can someone show me the PROMPT_COMMAND line for that? I'll paypal you a dollar if you want.(lol, lets see how fast I can get a reply now)
 
Thanks.

---

