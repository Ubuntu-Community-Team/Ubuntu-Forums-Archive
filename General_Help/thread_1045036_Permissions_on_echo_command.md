---
title: "Permissions on echo command"
date: 2009-01-20
forum: General Help
---

### Post by blazemore on 2009-01-20
It's sometimes useful to use echo to append a line to the end of a file.
For example:
```
echo deb http://ppa.launchpad.net/deluge-team/ubuntu intrepid main universe >> /etc/apt/sources.list
```

But because sources.list is root access only, I have to use sudo right?

Wrong.

I still get permission denied, even if I use sudo.
The way to do it is to do sudo su, then run the command

Can I sort out this annoying problem?

---

### Post by iaculallad on 2009-01-20
What about:
```

sudo su -c 'echo deb http://ppa.launchpad.net/deluge-team/ubuntu intrepid main universe >> /etc/apt/sources.list'
```

?

---

### Post by blazemore on 2009-01-20
Brilliant thank you. This is useful for shell scripting.

---

### Post by snova on 2009-01-20
It's because redirection is done by the shell, not by sudo. sudo merely runs the program with elevated privileges, Bash is where appending to the file gets done- which is still running under your user.

You could do it like this:

```
echo "deb http://repository/ ... " | sudo tee --append /etc/apt/sources.list
```

Which delegates appending to the **tee** program, which can then be run with elevated privileges.

Or you could also start a subshell:

```
sudo -i
echo "deb http://repository ..." >> /etc/apt/sources.list
exit
```

---

