---
title: "trouble exporting path"
date: 2006-07-02
forum: Desktop Environments
---

### Post by tefflox on 2006-07-02
I'm following [these directions]("http://linuxcommand.org/wss0010.php#path") to set the path to include my ~/bin, but it does not work.  I've tried several export commands in the .bash_profile and none of them work after logging out.  How do I get this right?

---

### Post by simonn on 2006-07-02
Are you running commands from a terminal?

.bash_profile only works in a terminal (or bash session to be precise). IIRC you need to use .xsession if you want to set a path for a user within gnome.

---

### Post by tefflox on 2006-07-02
I logged out of gnome (the F7 terminal) and logged into tty1 and my scripts work fine.  How do I set this up to work in gnome? thx.

---

### Post by simonn on 2006-07-02
If I Recall Correctly

Ok, I will rephrase the question.

Do you want to change you path becasue you want to run commands in ~/bin only from a terminal or also from the gnome menu?

---

### Post by tefflox on 2006-07-02
I'm trying to run my scripts in the gnome terminal.  I don't understand the "menu" part.. you mean from the Applications menu? I don't guess that's what I need. Just from the gnome terminal. 

in the F7 (gnome) gui terminal, the scripts don't run, but the same user can run these scripts on an F1 command-screen...

---

### Post by simonn on 2006-07-02
.bash_profile is sourced (i.e. used) at login.

.bashrc is sourced for all interactive shells, i.e. shells started while already logged in (using gnome, KDE etc).

What I suggest you do is use .bashrc to set anything you need for all terminals.

.bash_profile should contain:

```

if [ -f ~/.bashrc ]; then
	. ~/.bashrc
fi

```

Which will cause .bashrc, if it exists, to be sourced whenever .bash_profile is sourced.

This has the effects:

1) At login, both .bash_profile and .bashrc are sourced. 

2) Opening a terminal in gnome, KDE etc only .bashrc is sourced.

---

