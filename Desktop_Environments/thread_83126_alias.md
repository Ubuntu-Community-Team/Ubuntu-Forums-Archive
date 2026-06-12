---
title: "alias?"
date: 2005-10-27
forum: Desktop Environments
---

### Post by Sunnz on 2005-10-27
I was wondering why the ll command worked in sudo but not as a regular user, under some googling, I found out su has the alias setup. I have done the same to my regular account, but it forgets it as soon as I close the terminal, what's the deal?

---

### Post by cwaldbieser on 2005-10-28
[QUOTE=Sunnz]I was wondering why the ll command worked in sudo but not as a regular user, under some googling, I found out su has the alias setup. I have done the same to my regular account, but it forgets it as soon as I close the terminal, what's the deal?[/QUOTE]
The "alias" command as well as the "function" command and any assignment of shell variables is local to your current bash session.  If you want to make it available in every session, put the commands in you ~/.bashrc file.  You will need to export shell variables to make them available to sub shells.

---

### Post by Emerzen on 2005-10-28
You can also uncomment the following lines in ~/.bashrc.  

# Define your own aliases here ...
if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

Then create a text file in your home directory w/ the following title **.bash_aliases**.  Put your aliases in this file.  One note, if the command requires sudo priveleges, put the sudo in the alias command.

---

### Post by Sunnz on 2005-10-28
Thanks!

---

