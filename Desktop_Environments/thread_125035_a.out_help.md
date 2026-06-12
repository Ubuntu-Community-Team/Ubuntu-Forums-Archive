---
title: "a.out help"
date: 2006-02-02
forum: Desktop Environments
---

### Post by psboy1987 on 2006-02-02
I am trying to run an a.out program. When I run it at the terminal window it says that it isnt a good command.  what app or files do I need to download in order to get it to work. Thanks

---

### Post by jrib on 2006-02-02
you probably need to do ./a.out (and be in the directory where it is located)

'.' means current directory and '..' means parent directory.

When you type a.out, linux looks in your $PATH for a file called a.out.  But since '.' isn't in there, it won't find it.  You could give the absolute path (maybe /home/psboy/programs/a.out) or you can use the '.' to signify that the file is in the current directory.  This is a relative path since ./a.out will mean different things depending on what directory you are in.

---

### Post by psboy1987 on 2006-02-02
That has gotten me further than I have been before but for some reason it now says cannot execute binary file

---

### Post by psboy1987 on 2006-02-02
I figured it out. thanks now I just need to find out how to change my scite editor to work right. Thanks for the help

---

