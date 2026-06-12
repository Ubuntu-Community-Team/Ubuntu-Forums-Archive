---
title: "What is PKG_CONFIG_PATH?"
date: 2009-03-09
forum: General Help
---

### Post by Neo_The_User on 2009-03-09
I am suprised only 2 results showed up for this thread and they were not what I was looking for. What is PKG_CONFIG_PATH? Where is located? In the Makefile? How do I edit PKG_CONFIG_PATH?

---

### Post by C-- on 2009-03-09
PKG_CONFIG_PATH is an environment variable. Environment variables contain information that affect how certain processes behave on a computer. 

PKG_CONFIG_PATH in particular contains a path to all the directories that the pkg-config script checks for certain files it can use to do its job, and is usually the directory /usr/lib/pkgconfig.

To set PKG_CONFIG_PATH to this directory, use this command:

```
export PKG_CONFIG_PATH=/usr/lib/pkgconfig
```

You can replace /usr/lib/pkgconfig with any directory, and you can include multiple directories if they are separated by a colon ( : ), for example:

```
export PKG_CONFIG_PATH=/usr/lib/pkgconfig:/usr/lib/blah:/home/username/Desktop
```

This value will cause the pkg-config script to check the /usr/lib/pkgconfig, /usr/lib/blah, and /home/username/Desktop directories.

If you type this into a terminal, the PKG_CONFIG_PATH will be set for as long as the terminal is open.

If you type it into your .bashrc file in your home directory, it will be reset every time you open a new terminal window, for that terminal window.

If you type it into your .profile file in your home directory, it will be reset every time you log in.

To view the current value of the PKG_CONFIG_PATH variable, use this command:

```
echo $PKG_CONFIG_PATH
```

All environment variables can be set and viewed in this manner.

For more information about environment variables, please see

> [http://en.wikipedia.org/wiki/Environment_variable](http://en.wikipedia.org/wiki/Environment_variable)

---

