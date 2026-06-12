---
title: "When does .bash_profile get read?"
date: 2006-01-08
forum: Desktop Environments
---

### Post by UphillSkier on 2006-01-08
Hi, just a quick question.  I store some scripts in my $HOME/bin directory.  My (default) .bash_profile contains the lines 
```

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi
``` 
But when I launch a terminal .bash_profile doesn't get executed because my path looks like this: 
 ```

andy@grumpy:~$ echo $PATH
/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games

``` 
But .bash_profile does do the job if it gets executed!
```
andy@grumpy:~$ source .bash_profile
andy@grumpy:~$ echo $PATH
/home/andy/bin:/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games

``` 
Questions.
1. So when does .bash_profile get executed?  I thought it would be executed every time I launch a terminal.

2.  What is the best way to ensure that $HOME/bin appears in my path automagically? 

Thanks for the help
Andy

---

### Post by cwaldbieser on 2006-01-08
[QUOTE=UphillSkier]Hi, just a quick question.  I store some scripts in my $HOME/bin directory.  My (default) .bash_profile contains the lines 
```

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi
``` 
But when I launch a terminal .bash_profile doesn't get executed because my path looks like this: 
 ```

andy@grumpy:~$ echo $PATH
/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games

``` 
But .bash_profile does do the job if it gets executed!
```
andy@grumpy:~$ source .bash_profile
andy@grumpy:~$ echo $PATH
/home/andy/bin:/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games

``` 
Questions.
1. So when does .bash_profile get executed?  I thought it would be executed every time I launch a terminal.

2.  What is the best way to ensure that $HOME/bin appears in my path automagically? 

Thanks for the help
Andy[/QUOTE]

~/.bash_profile gets sourced for a login shell.  Basically, if you log in without the GUI.

~/.bashrc gets sourced for every shell.

Normally, you just some code to your .bash_profile to source your .bashrc so you can share the startups for both.

See the bash man pages for some of the other relevant files.

---

### Post by UphillSkier on 2006-01-08
[QUOTE=cwaldbieser]~/.bash_profile gets sourced for a login shell.  Basically, if you log in without the GUI.

~/.bashrc gets sourced for every shell.

Normally, you just some code to your .bash_profile to source your .bashrc so you can share the startups for both.

See the bash man pages for some of the other relevant files.[/QUOTE]

Thanks for the help.  I will move the default code to .bashrc.  I am surprised that it isn't there to begin with :)

---

### Post by joehill on 2006-03-23
Ok, this clears up a lot.  I was wondering why I could access my ~/bin commands through tty1 and not through gnome.  It still seems a mistake in the default configuration to put ' PATH=~/bin:"${PATH}" ' in .bash_profile since it won't even get used there.  It would be nice if it worked out of the box.

---

