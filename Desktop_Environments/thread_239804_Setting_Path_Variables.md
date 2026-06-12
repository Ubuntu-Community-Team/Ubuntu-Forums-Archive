---
title: "Setting Path Variables"
date: 2006-08-19
forum: Desktop Environments
---

### Post by magnoliablossom on 2006-08-19
I installed the free java sdk and it said that once I did it I needed to do this:

> After installation of this package you should be able to set JAVA_HOME
environment variable to /usr/lib/fjsdk (and preferably add /usr/lib/fjsdk/bin
at the beginning of your PATH) and use the common java utilities just like
in a non-free Java SDK.  Packages that can be built and run with help from
free-java-sdk's Java environment are in general eliglible to be placed in
the "main" section of Debian distribution.

When I did a search for setting paths, I found I needed to edit the /etc/profile file.  Well mine looks like this:

> #/etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).

if [ "$PS1" ]; then
  if [ "$BASH" ]; then
    PS1='\u@\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
	. /etc/bash.bashrc
    fi
  else
    if [ "`id -u`" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi

umask 022

What I need to know is where in there I need to put it.  Thanks in advance.

~* Ashley

---

### Post by magnoliablossom on 2006-08-19
Okay, I found another post concering this that says:

> If you want to use an IDE like eclipse, make sure you set your JAVA_HOME
environment variable.

sudo export JAVA_HOME = /path_to_java_sdk_dir

also you should add the java bin dir to your path

sudo export PATH=$PATH:/path_to_java_sdk_dir/bin

Hope that helps


However, when I try doing that it tells me this:

> heaven@ubuntu:~$ sudo export JAVA_HOME = /usr/lib/fjsdk
Password:
sudo: export: command not found


Any suggestions anyone?

---

### Post by taurus on 2006-08-19
You can set it in your ~/.bashrc.  Open a terminal (Applications -> Accessories -> Terminal) and type

```
gedit ~/.bashrc
```
Then, add these two lines to the end of it.

```

PATH=$PATH:/usr/lib/fjsdk/bin
export PATH

```
Source your ~/.bashrc or log out and back in and see if you have the right version of java

```

source ~/.bashrc
java -version

```

---

### Post by magnoliablossom on 2006-08-19
thanks....is this how i would do the JAVA_HOME part too?

---

### Post by taurus on 2006-08-19
Just add 

```

export JAVA_HOME=/usr/lib/fjsdk/bin

```

---

### Post by magnoliablossom on 2006-08-19
thanks works perfect....now on to my Ubuntu obstacle. :p

---

### Post by taurus on 2006-08-19
> **magnoliablossom said:**
> thanks works perfect....now on to my Ubuntu obstacle. :p
Good luck.  :mrgreen:

---

