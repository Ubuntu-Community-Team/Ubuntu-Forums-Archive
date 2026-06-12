---
title: "Gnome terminal problems"
date: 2009-02-15
forum: General Help
---

### Post by kogger on 2009-02-15
I had another topic about this problem, although I think I may have isolated the problem a little more.

My original problem was trying to launch a custom script with an application launcher (using gnome-terminal -e "command"). It would work with commands like "man" for some reason, but anything else would either get a child process error (if I tried to use the java or javac command, for example), or the window would immediately close (even if I appended "read" to the end of my script).

I've also tried launching a command window through jEdit, so basically what I've found is that trying to execute a command through a terminal window, unless you physically type the command into the terminal, doesn't work unless it's a man command.

Is this a bug, or is there actually a way to fix this?

---

### Post by ridetheteapot on 2009-02-15
I think that the "launch in terminal" is fairly new to the launcher creator, but i could be wrong....
An easy way to have the same functionality before the option existed is to make a command like this
gnome-terminal -e 'man sed'
those are regular ticks fyi (under the quotes on the keyboard)
i dunno but 'man sed' might work when you select launch in terminal, but it doesn't matter

---Sorry for my pointless post---

---

### Post by geirha on 2009-02-15
The command you supply to the -e switch is not executed in a shell afaik, so the common tricks you can do in the shells (/bin/sh and /bin/bash) do not apply. Try instead with:
```

gnome-terminal -x bash -c 'echo hello;read'
# or maybe you want to use it afterwards
gnome-terminal -x bash -c 'echo hello;bash'

```

---

### Post by kogger on 2009-02-15
Okay, it's starting to work, but one other small problem has come up. My PATH and JAVA_HOME variables reset in the new window (I add a couple directories to them in my .bashrc file), so in order to use the command I have to specify its full path.

---

### Post by geirha on 2009-02-15
That's odd. .bashrc should be read by bash ... Could you try adding an echo to the end of each of .bashrc and .profile? e.g. ```
echo echo I am profile >>~/.profile
echo echo I am bashrc >>~/.bashrc
```

Do any of those strings appear when you start gnome-terminal that way?

---

### Post by kogger on 2009-02-15
.profile and .bashrc already both have "I am profile" and "I am bashrc" echoed at the end of the file, but I've never seen it appear.

EDIT: "I am bashrc" appears when I open the terminal normally, but it doesn't affect the PATH variable inside the icon-launched one.

---

### Post by ridetheteapot on 2009-02-15
gnome-terminal -x bash -rcfile ~/.bashrc -c 'echo $PATH'
maybe .bashrc isnt getting read by default? a messed up .profile maybe?

---

### Post by geirha on 2009-02-15
Maybe I should've just tried it myself first, because .bashrc doesn't get loaded for me either ... it does if I just do «bash» in a terminal manually. I'm surprised .bashrc is not read when doing gnome-terminal -x bash -c 'something', but it seems to read it if you also supply the -i option
```
gnome-terminal -x bash -ic 'echo hello;read'
```

*scratch head*

---

### Post by ridetheteapot on 2009-02-15
man bash :INVOCATION:

       When  bash is invoked as an interactive login shell, or as a non-interactive shell with the --login option, it first reads and executes  commands  from  the file /etc/profile, if that file exists.  After reading that file, it looks for ~/.bash_profile, ~/.bash_login, and ~/.profile, in  that order, and reads and executes commands from the first one that exists and is readable.

guess no i or l no default profile

---

### Post by kogger on 2009-02-15
Well, adding the i works, so it now does what I wanted it to do:

```
gnome-terminal -x bash -ic '*command*'
```

Thanks.

---

