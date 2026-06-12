---
title: "Ubuntu Jaunty Jackalope Script"
date: 2009-04-27
forum: General Help
---

### Post by Sunny Hundal on 2009-04-27
I need to make some sort of script in 9.04 where i click on it and it automatically moves a specified text  file to a specified directory, If possible mabe edit a couple values then moves it, can someone point me in the right direction

---

### Post by mb_webguy on 2009-04-27
If you're moving the same file to the same place every time, you could just make a launcher using the command "mv */path/to/file /path/to/new_location/*".  You don't really need a script for that.

For anything more complex, you'll need a script.  A script that does the same as the launcher above would look like this:```
#! /bin/sh
mv */path/to/file /path/to/new_location/*
```Once you make this executable, you would just need to run the script.

Parsing and editing a file would take a bit more knowledge in scripting.  [Here]("http://www.freeos.com/guides/lsst/")'s a good place to start.

---

