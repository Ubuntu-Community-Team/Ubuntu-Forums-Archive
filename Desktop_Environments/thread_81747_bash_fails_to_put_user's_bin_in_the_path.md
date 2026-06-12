---
title: "bash fails to put user's bin/ in the path"
date: 2005-10-25
forum: Desktop Environments
---

### Post by jnoreiko on 2005-10-25
The .bash_profile file has these lines in it:

```
# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi
```

but they have no effect.
Is this a bug in bash, in ubuntu, or in gnome?

---

### Post by mgor on 2005-10-25
works fine for me.
```
$ cd -
$ mkdir bin
$ source .bash_profile
$ echo $PATH
/home/user/bin:/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games

```

---

### Post by cwaldbieser on 2005-10-25
[QUOTE=jnoreiko]The .bash_profile file has these lines in it:

```
# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi
```

but they have no effect.
Is this a bug in bash, in ubuntu, or in gnome?[/QUOTE]
Are you sure that you are in a login shell?  .bash_profile is only sourced from a login shell.  .bashrc is sourced for every bash shell.

---

### Post by jnoreiko on 2005-10-25
What's a login shell?

This is in the gnome Terminal app.

---

### Post by stoffe on 2005-10-25
[QUOTE=jnoreiko]What's a login shell?

This is in the gnome Terminal app.[/QUOTE]
Usually, when you log in remotely and come to the commandline that way.

You can move those lines to .bashrc, that should do it.

---

### Post by jnoreiko on 2005-10-26
So is it a bug?
Shouldn't my own bin/ folder be on the path all the time?

---

### Post by psychicdragon on 2005-10-26
Did you make all the programs in your bin executable?

---

### Post by jnoreiko on 2005-10-26
Yup.
The problem is definitely with .bash_profile, because adding the lines to .bashrc fixed it.

My point is: shouldn't these lines be in .bashrc instead?
My question is: whose responsibility is it to fix that?

---

### Post by psychicdragon on 2005-10-26
I see.

My bin always gets added because I don't use gdm I guess. :D 

You can file a bug report in [Bugzilla]("http://bugzilla.ubuntu.com/").

Here's a little more info from the wiki. [Click!]("https://wiki.ubuntu.com/BugReports?action=show&redirect=HowToReportABug")

---

### Post by jnoreiko on 2005-10-26
Right :)
I was just wondering who put those lines into the file -- are they a standard part of bash or added by gnome, or by ubuntu?

I'll file a bug anyway and see what happens :)

---

### Post by ironcamel on 2005-11-15
I ran into the same problem as the original poster, and it was driving me crazy, but I finally figured it out.

The way to get gnome-terminal to source bash_profile is:
open gnome terminal
edit your profile
click the "Title and Command" tab
check the box "Run command as a login shell"

This will cause the terminal to source bash_profile each time you open a new terminal window/tab (and there is a line in bash_profile which will source bash_rc).  Otherwise, only bashrc will be sourced.  This should add ~/bin to your path since there is a line in bash_profile which does that.

BTW, if you type 'bash' from a shell, bashrc will get sourced.  If you type 'bash --login', bash_profile gets sourced.  

The man page for bash says that bash_profile gets run for interactive sessions.  I guess by default shells are considered 'non-interactive' unless you give the --login option.

---

