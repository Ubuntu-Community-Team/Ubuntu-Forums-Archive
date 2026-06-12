---
title: "Please - some help with skippy"
date: 2006-04-21
forum: Desktop Environments
---

### Post by waldorf on 2006-04-21
I'm trying to get skippy running and when I 

gggg@hpbox:~$ skippy

I get this error

WARNING: Couldn't read from config file '/home/ggg/.skippyrc'.
WARNING: $HOME/.skippyrc not found loading default config.

*** Warning ***
Skippy could not grab the specified keysym and will die now.
This usualy means that another application has requested the
key Skippy is trying to grab.
You must find this application and change it's key, or change
the key Skippy uses in your local skippyrc in
[general] -> keysym .

Some help would be greatly appreciated.

---

### Post by outofnicks on 2006-04-30
If you don't see the file .skippyrc in your home folder, copy the default file named "skippyrc-default" in /usr/share/doc/skippy/examples, to your home. Rename it ".skippyrc" (be sure to include the period). That may be all you need to get skippy running, with a terminal command--worked for me.
I didn't find the program all that useful, however.

---

