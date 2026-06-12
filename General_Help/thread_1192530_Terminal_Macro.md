---
title: "Terminal Macro"
date: 2009-06-20
forum: General Help
---

### Post by Shockwave612 on 2009-06-20
Hi, I need some help with creating a macro for the terminal, if it is even possible.

Could anybody explain how I could type a command, then the terminal cd's to a certain directory the ./'s a program?

Cheers in advance.

---

### Post by Shockwave612 on 2009-06-20
Anyone?

---

### Post by geirha on 2009-06-20
You can make an alias
```
alias gogogo='cd /path/to/dir; ./prog'
```
Put that at the bottom of ~/.bashrc, then next time you open a terminal, you can type "gogogo" to run ./prog from /path/to/dir/.

If the program doesn't require you to be in a specific directory, you can call it directly
```
alias gogogo2='/path/to/dir/prog'
```

---

### Post by paperplate9 on 2009-06-20
An alias like explained above is easiest, however I think it requires you to be inside a shell in order to execute it. Otherwise you can just write a script.

```

cat > ~/doit <<EOF
#!/bin/bash
olddir="${PWD}"
cd /the/directory
nohup ./theprogram &
cd "${olddir}"
EOF
chmod 755 ~/doit

```then just run ~/doit if in a shell or doit from the 'run command' (alt+f2) but make sure you hit run in terminal if this is a non-gui app

---

### Post by Shockwave612 on 2009-06-20
Yay, the 2nd one returned an error but the first worked perfectly thank you Geirha!

---

### Post by paperplate9 on 2009-06-20
> **Shockwave612 said:**
> Yay, the 2nd one returned an error but the first worked perfectly thank you Geirha!

What error?

---

### Post by Oscar Garza on 2010-01-23
I was also wondering this, since creating an alias in .bashrc is useless in another shell.

Is there another replacement for terminal that will allow me to create macros that will send the text to the current prompt?

Say I want to create a macro for when I am browsing my phone's shell, where I can't create aliases.

EDIT: nvm, found Autokey and it does what I want. [http://autokey.sourceforge.net/](http://autokey.sourceforge.net/)

---

### Post by falconindy on 2010-01-23
> **Oscar Garza said:**
> I was also wondering this, since creating an alias in .bashrc is useless in another bash.

Is there another replacement for terminal that will allow me to create macros that will send the text to the current prompt?

Say I want to create a macro for when I am browsing my phone's shell, where I can't create aliases.

I think you're slightly confused. Changes made in .bashrc aren't in effect until .bashrc is re-sourced. That means opening a new terminal or running the command 'source ~/.bashrc' to grab the new changes.

---

