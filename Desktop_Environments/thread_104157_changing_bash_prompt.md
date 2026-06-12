---
title: "changing bash prompt?"
date: 2005-12-15
forum: Desktop Environments
---

### Post by [censored] on 2005-12-15
Hi.

Does anybody know how I can re configure things, so that when I open the gnome-terminal, it doesn't show the full path at the prompt? I only want it to show the current working directory.

Cheers.

---

### Post by psusi on 2005-12-15
I can't recall the exact details, but it will involve changing the PS1, PS2, PS3, and PS4 environment variables.  You will want to set them in your .profile so it is done automatically for all your shells.  

Maybe someone else remembers the specifics... otherwise, try running info bash and read the documentation.

---

### Post by soulestream on 2005-12-15
[http://www.linuxselfhelp.com/howtos/Bash-Prompt/Bash-Prompt-HOWTO-2.html](http://www.linuxselfhelp.com/howtos/Bash-Prompt/Bash-Prompt-HOWTO-2.html)

[http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Bash-Prompt-HOWTO.html](http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Bash-Prompt-HOWTO.html)

should get you started

soule

---

### Post by tburns on 2005-12-15
[QUOTE='[censored]']Hi.

Does anybody know how I can re configure things, so that when I open the gnome-terminal, it doesn't show the full path at the prompt? I only want it to show the current working directory.

Cheers.[/QUOTE]


I think it is the PS1 value in .bash_profile or .profile. \w gives current working directory. see:
[http://docs.cs.byu.edu/docs/bash/3.php#5](http://docs.cs.byu.edu/docs/bash/3.php#5)

---

### Post by amohanty on 2005-12-15
[http://www.tldp.org/HOWTO/Bash-Prompt-HOWTO/](http://www.tldp.org/HOWTO/Bash-Prompt-HOWTO/)

---

### Post by [censored] on 2005-12-16
thanks guys. Unfortunately the pages you've all cited show me a "\w" environment variable that's supposed to show the current working directory. Just doesn't seem to work on my shell.

---

### Post by amohanty on 2005-12-16
can you post the line that goes:

export PS1...

---

### Post by bigmista on 2005-12-23
I'm new here and new to linux. Could someone please tell me where to find the .profile file to edit?

---

### Post by briancurtin on 2005-12-23
[QUOTE=bigmista]I'm new here and new to linux. Could someone please tell me where to find the .profile file to edit?[/QUOTE]
files prefixed with a dot are hidden files, and wouldnt be shown in nautilus unless you specify to show hidden files

you can do:
```
vi .profile
```
to view/edit edit the .profile file

---

### Post by Madpilot on 2005-12-23
Bash prompts can be edited in .bashrc in your user directory.

It's an arcane language, though! :p

---

