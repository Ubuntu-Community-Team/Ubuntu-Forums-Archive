---
title: "&quot;sudo env&quot; - extremely limited $PATH"
date: 2005-12-25
forum: General Help
---

### Post by drfloob on 2005-12-25
I can't figure out how to set the $PATH variable for sudo.  "sudo env | grep PATH" reports an EXTREMELY short $PATH variable ... that doesn't reflect anything in a local .bashrc (root or regular user), nor in the /etc/profile file.  "sudo echo $PATH" outputs the PATH for the user calling sudo.  It's really inconvnient using absolute path names for everything ... I hope someone can help me out.

```

[me@myPuter~]$ sudo env | grep PATH
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin

[me@myPuter~]$ sudo echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/opt/jdk1.5.0_06/bin:/home/me/bin:/usr/X11R6/bin:/opt/xfce4/bin

```

---

### Post by JmSchanck on 2005-12-25
```

sudo -s

```
to log in as root and then change the PATH

---

### Post by drfloob on 2005-12-26
ok, I've done that.  "sudo -s" logs me in as root.  "env | grep PATH" then shows root's PATH, which I've already set up to include what I need.

Maybe I should be more clear about my problem.  I've written a bash script, called "drif" to easily manage my network, it's located in /home/me/bin, and it requires root access.  I've added "/home/me/bin" to the PATH variable in /etc/profile, so I can run the executable "drif" as any user ... and that much works.  BUT ... when I try and execute "sudo drif" as user "me", it returns with
```
sudo: drif: command not found
```

I did some snooping and found that "sudo env | grep PATH" does not include /home/me/bin ... so that's where I've left off.

Maybe I missed something ... how else should I change PATH (other than /etc/profile or ~/.bashrc)?

---

### Post by Faerine on 2007-12-05
I am having the same problem (in Dapper) -- I can't access the PATH env variables I have set in /etc/profile or ~/.bashrc when I am using sudo, even though they work with my user or with root. I haven't found a solution online so far. Can anyone advise on how to set the sudo PATH?

---

### Post by metalheart on 2007-12-05
To find out, if program is on your path, run
```
which script_name
```
To reload shell variables execute
```
source rc_file
```

---

### Post by dagnabit dang doohickey on 2007-12-05
Instead of making the path to your user's bin directory global, just put the script in the /usr/local/bin directory.

Edit: I didn't realize I was responding to an ancient post.

---

