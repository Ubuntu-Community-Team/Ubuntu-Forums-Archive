---
title: "How to change workspaces using the terminal"
date: 2009-02-19
forum: Desktop Environments
---

### Post by Blackdragon1400 on 2009-02-19
Hey guys, got a noob question for you. How do you use the terminal to change to a different workspace. I am writing some .sh shell scripts to run some commands I need. The problem is they both run continuously so I would like to have them both open in two different workspaces. Any clue on how to do this???

Thanks

---

### Post by cconroy on 2009-02-20
It sounds like what you really want to do is run them in the background

the following script would print "hi" very quickly...

```
longCommand1&
longCommand2&
echo "hi"
```

the & instructs the shell to run the process in the background and not wait for it to terminate.

---

### Post by Blackdragon1400 on 2009-02-20
If I run the process in the background how do I pull it up to see what it is doing ex. my script will be running commands verbosely so I would like to see some of that output

---

### Post by zhocchao on 2009-02-20
you're looking for wmctrl

---

### Post by Blackdragon1400 on 2009-02-20
im having some trouble getting wmctrl to work the way a would like it to, it seems to work on a basis of having multiple "Desktops" not so much for workspaces. I dont belive that this program has full support for what I need, I even had problems getting it to maximize a window. Any suggestions?

---

### Post by Armor Nick on 2009-02-21
Try using GNU screen (I think it's installed by default) or just use a tabbed terminal emulator. Heck, you could even use your virtual terminals if you want (Ctl+Alt+F* and replace * with a number from 1 to 6).

---

### Post by cconroy on 2009-02-21
> **Blackdragon1400 said:**
> If I run the process in the background how do I pull it up to see what it is doing ex. my script will be running commands verbosely so I would like to see some of that output

You could redirect the output. e.g.
```
chris@serenity:~$ cat blah.sh
sleep 2
echo "hi"
sleep 2
echo "hi again"
exit

```

```
chris@serenity:~$ sh blah.sh>blah.txt &
[2] 31827
chris@serenity:~$ tail -f blah.txt
hi
hi again

```

Take a look at the [[COLOR="Blue"]TLDP documentation for Bash I/O redirection[/COLOR]]("http://tldp.org/LDP/abs/html/io-redirection.html") if you need to do something fancier.

---

### Post by cubeist on 2009-02-21
Actually, if you are using compiz, there is a way to do this... First write your shell scripts so that each separate process opens in a specific terminal (in gnome, you can create terminal profiles with unique names).  The command to run a script in a specific terminal would look like this:
```
gnome-terminal --window-with-profile=asdf
```
Then in compiz, use the *place* plugin to place that window in a specific viewport... then everytime you run your shells, the new terminal windows will automatically be placed where you want them..


hope I explained this ok...good luck

---

