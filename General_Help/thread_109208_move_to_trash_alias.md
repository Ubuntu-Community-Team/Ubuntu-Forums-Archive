---
title: "move to trash alias"
date: 2005-12-28
forum: General Help
---

### Post by myha on 2005-12-28
Hello,

can someone please tell me if there is any way to add alias which would move selected file to trash...
smth like alias rm='mv selected_filename ~/.Trash/'

br, Miha

---

### Post by Nate53085 on 2005-12-28
would

alia rm='mv $1 ~/.Trash/  

work?

you may need to put 'mv $1 ~/.Trash' in a bash script, and then alias rm to that bash script

---

### Post by briancurtin on 2005-12-28
or just put the alias line straight in your .bashrc, rather than go one step away and one step back to it

---

### Post by Nate53085 on 2005-12-28
yeah, good call

---

### Post by myha on 2005-12-28
hi,

I have putted the alias in my ~/.bashrc:
alias rm='sudo mv $1 ~/.Trash/ '

but I get the error
mihap@lx-mihap:~$ rm test123
mv: cannot overwrite non-directory `test123' with directory `/home/mihap/.Trash/'

---

