---
title: "Bash issues after upgrade to jaunty"
date: 2009-06-02
forum: General Help
---

### Post by xghstst0riesx on 2009-06-02
I performed a clean install of jaunty while retaining my home directory on a separate partition. After doing this gnome-terminal has become unusable. Tab-completion no longer works and only a "$" is shown at the prompt. Thanks!

---

### Post by mb_webguy on 2009-06-02
It sounds like you're either not using the bash shell, or there's a problem with your bash config file.  To test the former, open the terminal and enter the command "echo $SHELL".  If it says "/bin/bash", then you should be using the right shell.  The next step is to check your ~/.bashrc file to see if a) it's there, and b) if it's been changed somehow.

---

### Post by xghstst0riesx on 2009-06-02
SHELL is set to /bin/sh and changing it to /bin/bash had no effect.

As for my .bashrc file I copied over it with one from a newly created user so that's not the problem either.

---

### Post by xghstst0riesx on 2009-06-04
bump ;)

---

### Post by capscrew on 2009-06-04
> **xghstst0riesx said:**
> SHELL is set to /bin/sh and changing it to /bin/bash had no effect.

As for my .bashrc file I copied over it with one from a newly created user so that's not the problem either.

See if you are really using your old home directory.  Maybe you created a new one and that is where you are.

When you try this: ```
cd
```

What directory are you in?  What do you get from:```
pwd
```

---

### Post by xghstst0riesx on 2009-06-04
> **capscrew said:**
> See if you are really using your old home directory.  Maybe you created a new one and that is where you are.

I am using my old home directory. 

One odd thing I noticed that in the "Users and Groups" app the shell was set to "/bin/sh" rather than "/bin/bash". Changing this made no difference however.

---

### Post by xghstst0riesx on 2009-06-07
My problem is still unresolved. Are there any other configuration files in my home directory that would affect the way that the terminal is being displayed other than .bashrc?

I'm attaching an image to clearly illustrate what the issue is.

---

### Post by mdbnsb on 2009-06-25
I'm having a similar issue. .bashrc loads fine if I open gnome terminal, but it doesn't seem to be loading when I log into a console directly. 

echo $SHELL tells me /bin/bash in the console, but .bashrc doesn't load unless I explicitly run 'bash' in the console. 

Goofy.

---

