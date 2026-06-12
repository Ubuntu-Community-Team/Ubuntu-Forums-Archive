---
title: "Ctrl-keys does not work in gnome-terminal (gutsy)"
date: 2007-11-26
forum: Desktop Environments
---

### Post by knatten on 2007-11-26
After upgrading to gutsy, my Ctrl-keys have stopped working in gnome-terminal. They work just fine in other aplications, like xterm and firefox. Some examples:
Ctrl-d : Nothing happens
Ctrl-s : Same as pressing enter
Ctrl-c : Same as pressing enter
Ctrl-w : A comma appears
etc.

The problem persists in all applications run within gnome-terminal. Examples:
Can not use Ctrl key in vim
Can not use Ctrl+d for logging out after ssh-ing to another box.

Other special characters, like Shift, Esc and AltGr works.

$ uname -a
Linux abel 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

$ gnome-terminal --version
GNOME gnome-terminal 2.18.2

$ echo $LANG $GDM_LANG
en_US.UTF-8 en_US.UTF-8

Please tell me if you need any other information.

---

### Post by bingoUV on 2007-11-26
Assuming you use bash shell. Post the output of 
```

bind -p

```

---

### Post by knatten on 2007-11-26
> **bingoUV said:**
> Assuming you use bash shell. Post the output of 
```

bind -p

```

I am using bash.
bind -p : [http://knatten.org/paste/bind-p](http://knatten.org/paste/bind-p)

---

### Post by bingoUV on 2007-11-26
I don't see anything wrong there. What is the value of the TERM shell variable in xterm and gnome-terminal? Try changing the value of the TERM environment  variable to one of 
xterm
rxvt
gnome
linux
vt100

---

### Post by knatten on 2007-11-27
> **bingoUV said:**
> I don't see anything wrong there. What is the value of the TERM shell variable in xterm and gnome-terminal? Try changing the value of the TERM environment  variable to one of 
xterm
rxvt
gnome
linux
vt100

In both gnome-terminal and xterm:
```

$ echo $TERM
xterm

```

I tried to do
```
export TERM=foo
```
for foo in {xterm, rxvt, gnome, linux, vt100}, but none of those fixed my problem.

Any other suggestions?

---

### Post by bingoUV on 2007-11-27
Can you backup the following files, remove them from their current locations , restart the X server and try again?
~/.x*
~/.X*
~/.ICE*

You could also try creating a new user and trying this out, to help figure out whether the issue is specific to your username.

---

### Post by knatten on 2007-11-27
> **bingoUV said:**
> Can you backup the following files, remove them from their current locations , restart the X server and try again?
~/.x*
~/.X*
~/.ICE*


That did not help.

> **bingoUV said:**
> 
You could also try creating a new user and trying this out, to help figure out whether the issue is specific to your username.
It is. I created a new user, and the problem does not exist with that user.

By the way, under System->Preferences->Keyboard->Layout Options->Ctrl key position, I have selected "Make CapsLock an additional Ctrl." This was done before the upgrade, and worked. I have now tried to revert this setting to "Default", just in case it could influence my problem, but that did not help either.

I have also tried to do 'egrep -i "ctrl|control" ~/.*' , and search for ctrl and control in gconf-editor, but did not get any relevant hits.

---

### Post by stunner on 2007-11-29
Exact same problem here.  Have not yet tried either of the fixes proposed.

---

### Post by knatten on 2007-12-05
> **stunner said:**
> Exact same problem here.  Have not yet tried either of the fixes proposed.

Could you please post your results when you have tried them?

---

### Post by stunner on 2007-12-05
Creating a new user doesn't work. Control-P just prints blue ^P's without searching.

---

### Post by bernardfrancois on 2008-01-12
Here, creating a new user worked. Because I wanted to create a user with the same name, I had to erase the home folder of the user manually (this didn't happen by the users-admin tool, so the problem wasn't solved without removing manually).

I posted the steps I took here:
[http://ubuntuforums.org/showpost.php?p=4121195&postcount=2](http://ubuntuforums.org/showpost.php?p=4121195&postcount=2)

---

### Post by jasonkostempski on 2008-06-04
Is there a solution that doesn't involve deleting the account, that fix doesn't exactly get to the root of the problem.

---

### Post by jasonkostempski on 2008-06-05
Well, I was about to give in and delete my account. While I was setting up the temp account to transfer my data to, I notice a setting that was different. Under System->Administration->Users and Groups->Advanced my 'Shell' path was set to /bin/sh. On the temp account it was set to /bin/bash so I switched mine back to /bin/bash and logged out, when I logged back in everything worked fine. I have no clue how that got switched or if it ever was correct in the first place.

---

### Post by jasonkostempski on 2008-06-05
Seems like when you use useradd to add a user /bin/sh is the default. That is how I created my account so I assume it was never /bin/bash

---

