---
title: "howto get own shell startup scripts run automatically?"
date: 2005-12-26
forum: Desktop Environments
---

### Post by lmlahti on 2005-12-26
Hi, what should I do to get a self-made script run automatically in shell startup?

I tried this by writing a shell startup script (in Ubuntu, i686)

#!/bin/sh
source ~/.aliases

and put this script into file
/etc/init.d/aliases

this was softlinked in  
/etc/rc.local/
as
lrwxrwxrwx  1 root root 19 2005-12-18 12:05 K01aliases -> /etc/init.d/aliases*                          

Well this does not work but it is about all I could reason from online support that I found for (various) other Linux versions. Thanks for your help:)

---

### Post by kabus on 2005-12-26
If you want to run a command everytime you start a new shell you could just add it to your ~/.bashrc, I think.
I'm not sure I'm understanding you correctly, though.

---

### Post by Sutekh on 2005-12-26
I agree with kabus.  This is how I would do it, I'd put these lines in ~/.bashrc, in fact they're already there if you have a check; just put your aliases in ~/.bash_aliases and uncomment the following lines...

```
if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi
```

---

### Post by Lambert on 2005-12-26
If the script is in /etc/init.d/ with correct permissions then do this.

```
sudo update-rc.d aliases start 99 2 .
```

to break this down

update-rc.d adds the proper link so it runs

aliases is the name of the file in /etc/init.d that you want to add

99 is the place in which it runs. you can enter 01-99

2 places the link only in runlevel 2 if you use or want the link in other runlevles just add a space and the next runlevel (start 99 2 3 4 5 .)

make sure you have the space and . at the end of the command

---

### Post by lmlahti on 2005-12-27
Thanks a lot, I got it working by modifying ~/.bashrc (uncommenting the alias call lines) and adding ~/.bash_aliases with the wanted alias definitions.

For some reason, I did not succeed in the other suggestion above. It added the links (see below) and I think all permissions are ok. Still aliases were not sourced at startup. But I am doing fine now as the scripts function with .bashrc thing.

leo@hoasb-ff0fdd00-55:~$ sudo update-rc.d aliases start 99 2 .
Password:
 Adding system startup for /etc/init.d/aliases ...
   /etc/rc2.d/S99aliases -> ../init.d/aliases

---

