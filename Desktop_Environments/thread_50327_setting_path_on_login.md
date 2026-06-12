---
title: "setting path on login"
date: 2005-07-19
forum: Desktop Environments
---

### Post by jclemon on 2005-07-19
how do i set my path upon login, not upon launching a shell?

---

### Post by professor_chaos on 2005-07-19
My understanding is that your paths are shell paths, and... If you set a shell path in .bashrc or .bash_profile (if your using bash) then that path is set for all shell use, but the path is set for the shell, not directly related to your "login"

So insert ```
export PATH=$PATH:/some/path/you/wish/to/set
``` into .bashrc and its set. 
You can set as many paths as you want this way.
Hope I understood your question.

---

### Post by jclemon on 2005-07-19
[QUOTE=professor_chaos]My understanding is that your paths are shell paths, and... If you set a shell path in .bashrc or .bash_profile (if your using bash) then that path is set for all shell use, but the path is set for the shell, not directly related to your "login"

So insert ```
export PATH=$PATH:/some/path/you/wish/to/set
``` into .bashrc and its set. 
You can set as many paths as you want this way.
Hope I understood your question.[/QUOTE]
 yeah i've done that but your path only becomes set to this when you launch a terminal. i have an application i can launch in the terminal after my path gets set in this manner, but i have added a launcher for it on the panel and when i try to launch it upon login, it cannot find it in my path (becuase no terminal has been launched). i need a way to set my path upon login and not depend on launching a shell.

---

### Post by jclemon on 2005-07-19
[QUOTE=jclemon]yeah i've done that but your path only becomes set to this when you launch a terminal. i have an application i can launch in the terminal after my path gets set in this manner, but i have added a launcher for it on the panel and when i try to launch it upon login, it cannot find it in my path (becuase no terminal has been launched). i need a way to set my path upon login and not depend on launching a shell.[/QUOTE]
 got it working, you have to use a .gnomerc file, which gets referenced at login

---

### Post by blahbleh on 2005-07-20
where do you put this gnomerc...especially if you want it to be good for all users?

---

