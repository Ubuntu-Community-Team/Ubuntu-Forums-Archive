---
title: "Changing HISTSIZE"
date: 2009-06-08
forum: General Help
---

### Post by luiznetto on 2009-06-08
All I want is something so simple! And yet so complicated. All I want is to change the value of one variable: the HISTSIZE variable. Only now I realize that my "history" command only shows 500 of my last actions. The default used to be 1000 in previous Linux distros that I used. 500 is not nearly enough for me; I want 1000. Doing

export HISTSIZE=1000

won't work; when I reboot the computer the shell won't remember that. I was told to modify the ~/.bash_profile file; but this file just doesn't exist in Ubuntu. I was told to use the "set" and "setenv" built-in shell commands; but those commands don't exist in Ubuntu either! I'm getting desperate. Anybody can help? Please.

---

### Post by luiznetto on 2009-06-08
Sorry, I spent the whole day yesterday searching the many Linux books that I have at home googling for an answer. The solution that I found was to change the file /etc/profile. I added a last line to it:

export HISTSIZE=1000

Apparently, it works. Now I get:

$ echo $HISTSIZE
1000

and my history has gotten to line 540. I'm not sure, though, that this is the best or safest solution. I read somewhere that /etc/profile in Ubuntu might be overwritten during updates. So if anybody has any input, I'll thank you with all my heart.
Luiz

---

### Post by Tex-Twil on 2010-07-01
Hi,
I export those variables correctly but it doesn't seem to work. My .bash_history is still only 500 lines :(

Any ideas ?

---

### Post by clrg on 2010-07-01
If you want to set global variables, /etc/profile is your friend.

@luiznetto: /etc/profile has never been overwritten during updates on my machine. Usually apt asks what do do if you altered a file manually, such as menu.lst or smb.conf or whatever.

@Tex-Twil: Add this line to the end of /etc/profile and restart (just exporting in a shell only works for that particular shell):

```
export HISTSIZE=1000
```

---

### Post by Tex-Twil on 2010-07-01
well I do export the variable in my .bashrc. If I open any shell it is correctly exported.

I will try in /etc/profiles

EDIT: putting it only in /etc/profiles does not work. It is still the default 500

> echo $HISTSIZE
500

---

### Post by luiznetto on 2010-07-01
Hi, I did that so long ago, that I didn't remember anymore. But fortunately, every time I solve a problem in Linux, I keep a record on how I did it. So this may be helpful:

* The HISTORY command
To find out where is the file that stores your command line history, do
$ echo $HISTFILE
The environment variable HISTSIZE determines the number of commands that are stored in your command history file. To find out what is the current value of that variable on your system, do 
$ echo $HISTSIZE
To change the value of this variable, I added these last lines to /etc/profile:
export HISTFILESIZE=2000
export HISTSIZE=2000
I also added the two last lines to /etc/environment:
HISTFILESIZE=2000
HISTSIZE=2000
Actually, just the latter change is enough to produce the desired effect.
The main files for configuring system-wide environment variables in Bash are:
/etc/profile, /etc/bash.bashrc, /etc/environment
See Bash Man Page, line 659, 2410 (in Konsole).
More information can be found in:
[https://help.ubuntu.com/community/EnvironmentVariables#System-wide](https://help.ubuntu.com/community/EnvironmentVariables#System-wide) environment variables
I also edited my /home/luiz/.bashrc by putting the comment hash in these two lines:
#export HISTCONTROL=ignoredups
#export HISTCONTROL=ignoreboth

Funny thing is, I just checked my /etc/profile, and those last two lines that I put there are no longer there. But when I do

$ echo $HISTSIZE
2000

I get what I expected. So I have a hunch that the crucial file is /etc/environment; here is what I get:

$ cat /etc/environment
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
HISTFILESIZE=2000
HISTSIZE=2000
HISTCONTROL=

I hope this solves the problem for you (it did for me).

Luiz

---

### Post by bodhi.zazen on 2010-07-01
Use /etc/environment if you want this setting for all users, use ~/.bashrc if you want it for a single user only.

If a file does not exist (.bash_profile) , make it ...

For details see man bash

[http://manpages.ubuntu.com/manpages/lucid/en/man1/bash.1.html#toptoc6](http://manpages.ubuntu.com/manpages/lucid/en/man1/bash.1.html#toptoc6)

Again, if one of those files does not exist, simply create it.

You can also source additional files (some people prefer to keep aliases or config options in separate files).

source ~/.bash_aliases
source ~/.bash_custom

feel free to improvise.

---

### Post by Tex-Twil on 2010-10-06
I tried putting in .bashrc and /etc/profiles.

The variables are exported:

```

$ echo $HISTSIZE  $HISTFILESIZE
100000 100000

```

but my history file does not contain commands I issued a week ago and has only 300 lines

```
$ cat .bash_history |  wc -l
350
```

:(

---

### Post by louisJ on 2012-03-24
up
same here...any solution?

---

### Post by oldos2er on 2012-03-24
Old thread is old, please start a new thread for your question.

---

