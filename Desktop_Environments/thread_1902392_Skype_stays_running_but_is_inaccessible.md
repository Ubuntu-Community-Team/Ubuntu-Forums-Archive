---
title: "Skype stays running but is inaccessible"
date: 2011-12-30
forum: Desktop Environments
---

### Post by davethewave83 on 2011-12-30
When I launch Skype, login, then hit the "X" on the window, skype vanishes but I know it's still running, so I click to launch Skype and a new window appears to login with, when I try to login it says "Another skype instance may exist" which I know it does, but there are no icons anywhere to get back to it. 

Is there a command I can use in terminal to bring the window up? 

I've removed Unity and am using the gnome fallback because I was having similar issues with Unity on other programs.

---

### Post by ubix on 2011-12-30
There are many solutions to this problem. If you have just one instance of Skype running on your machine you should consider (1), (2) or (3) below:

***(1)***
The easiest is rebooting the system and it should stop running, unless you set it up so it automatically starts running when you boot.
***(2)***
A more elaborate is to kill it manually. But it requires a lot of typing, and I'd like to avoid leading you through this process, since it may take too much effort on both sides, unless you are familiar with basic Unix admin issues.
***(3)***
Second best is to run this script from your terminal:
```
sudo kill -9 `ps -ef |grep skype|grep -v grep| awk '{ print $2 }'`
```

The above, of course, will fail if there are more than a single instance of Skype running on your system. You can check that by entering "**ps -ef |grep skype|grep -v grep**" command without the quotes in your terminal (for a single Skype instance you'll get only a single line on the screen).


But if you have more than one instance of Skype running on your machine you are better off doing the following (#4):

***(4)***
***(4.a)*** create the following file by cutting and pasting the following into the file called **kill-all-skypes**:

```

myself=`basename $0`
for n in `ps -ef |grep skype|grep -v grep|grep -v $myself | awk '{ print $2 }' -`
do
  kill -9 $n && killed=yes
  [ "$killed" = "yes" ] || { 
    echo "You must enter: sudo $myself"; exit 1
  }
done
[ -z "$killed" ] && echo Skype was not running || echo Skype killed

```

***(4.b)*** run this command by executing the following line
```
sudo kill-all-skypes
```
If you have completed either 1, 2, 3 or 4 above, you can then start up Skype as you do it normally.

NOTE:
In old days code in **kill-all-skypes** would not work in **bash**, hence it is _Bourne shell_, not _bash_. For this reason, if you wish to save it as a command, for instance, in your /usr/local/bin you should add the **#!/bin/sh** and not **#!/bin/bash** shebang in front.

---

